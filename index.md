---
layout: page
---
## Welcome to the matrix

{{ site.description }}

### Features
- Unique registration system
- SSH Access
- XMPP Server (username@matrix.ac)
- User space web hosting

### Connection Information

#### Account Registration

Register [here](join). To register you will need to have a university email address, an address ending in .ac.uk or something.

You will also need to provide us with your public SSH key. This is to allow you access to our serverS securely.

- [joynet Generating SSH keys in windows](https://help.github.com/articles/generating-ssh-keys/)
- [GitHub How to generate SSH Keys](https://help.github.com/articles/generating-ssh-keys/)

You can also use curl to register your account. 

	curl 'http://matrix.ac/registration/join' --data 'username=anewosaka&email=osaka%40domain.ac.uk&pubkey=ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCr2aZIzhTCdW/EMHBqiZhX0gguK46P3eobO+6vqMoRoIo5Hb1kWJaNNnD0wE2oODh61QTG5pibI+gAIWRNPAZxP9+Wqt8S8MTD1DtEswdgDYx3ZqatcCLgMeFQ3ujQiWYBj1NEP2d0VWHZGitkQJi5txLWxAgvI0C4iWKvURRDV9H+RTCZnGq6GzrfWKO8jVs53IAPUTr2Dg5JaQvLfVIjgxxnySea/EtEnDF9ezbWhELNkjXBYo5+i8PN/UHeE+/jIvEvV6J1uCnVblDeD437jinBpkuEXsq5Wu4Uy6mMHnc4V9eW84xwF78qfb1wC2+o4HpP0ByZK5+dDYbJAAlf'

Then once you receive your email you can activate your account be sending a GET request to registration/activate

	curl 'http://matrix.ac/registration/activate/8319b3ff51f340c2ebe222d37498d5ab301e91444b578f6226'

#### SSH

Once your account is activated you will have access via ssh.

    ssh username@matrix.ac

#### XMPP

XMPP, also known as jabber is an instant messaging protocol. 

- **Server** matrix.ac
- **Port** 443, 5222 
- SSL only

There is an array for clients available for many platforms. Some of our favorites are:

- Pidgin <https://pidgin.im> - GUI (With CLI option <https://developer.pidgin.im/wiki/Using%20Finch>)
- Gajim <http://gajim.org> - GUI
- mcabber <http://mcabber.com> - CLI
- profanity <http://profanity.im> - CLI
- conversations <http://conversations.im> - Android

#### Web Hosting

Matrix provides users with space for hosting HTML files.  
Access your data at <http://matrix.ac/~username> 

Anything located in ```~/public_html``` will be available to the world.

