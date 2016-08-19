---
layout: page
title: GIT Hosting
permalink: /docs/git-hosting/
resource: true
categories:
- Git
---

Head over to <https://git.matrix.ac> and you will see a list of repositories stored on the matrix. 

To host a public repository place it in ```~/public_repo```.

You can then add it as a remote, using:
	
	git remote add origin matrix.ac:public_repos/<repo>

And you can clone via SSH:

	git clone matrix.ac:public_repos/<repo>

And you can clone via HTTP:

	git clone http://git.matrix.ac/<user>/<repo>

Currently there are no groups or finer permission. If this is wanted we can work something out.