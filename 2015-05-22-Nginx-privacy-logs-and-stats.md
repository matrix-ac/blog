# NGINX privacy logs and stats

In the interest of our users and overall privacy concerns we decided to remove as much identifiable information from our system to insure that we do not store more data on our users than the bare minimum, we decided to streamline our logs.

We turned to NGINX, below is a record of a sentential scanning the matrix.

	123.125.71.92 - - [22/May/2015:08:32:13 +0100] "GET /stylesheets/icono.min.css HTTP/1.1" 200 49258 "-" "Mozilla/5.0 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)"

Now, we could completely disable all access logs and be done with it, but we want to know which page is most active. So we decided to keep just the basic information which we can use for stats. This resulted in the above record to look like this: 

	200 GET /stylesheets/icono.min.css HTTP/1.1

This was done with NGINX's [log format](http://nginx.org/en/docs/http/ngx_http_log_module.html#log_format) string very simple to use, we simply create a format which logs the server response and the request from the client:

	log_format privacy '$status $request';
	access_log /var/log/nginx/access.log privacy;

Now we needed the server status to allow us to get some stats on the pages being accessed. We can write a simple bash script to pull all successful requests, 200. Then have it count all the unique page requests. We only want to count access to directories or pages ending in '.html'.

	grep ^200 /var/log/nginx/access.log | cut -d' ' -f3 | egrep  "/$|.html" | sort | uniq -c | sort -g

This script gets run via cronjob and generates stats for us. Yay. 

One final thing was to make sure that we don't keep these access logs for longer than we need. We want to have stats every 10min, 60min, 1day and 1week. So we modified the logrotate to rotate the logs every week and not to keep more than one weeks worth of data.
