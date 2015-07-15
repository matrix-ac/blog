---
layout: page
---
## Welcome to the matrix

{{ site.description }}

### Features
- Unique registration system
- SSH Access
- Federated XMPP (username@matrix.ac)
- User space web hosting
- Access services over Tor

### Connection Information

#### Account Registration

Register [here](join). To register you will need to use your university email address. 

You will also need to provide us with your public SSH key in order to access the matrix.ac server securely.

- [How to generate SSH keys under Windows](https://docs.joyent.com/public-cloud/getting-started/ssh-keys/generating-an-ssh-key-manually/manually-generating-your-ssh-key-in-windows)
- [How to generate SSH Keys under Linux](https://help.github.com/articles/generating-ssh-keys/)

You can also use curl to register your account. 

	curl 'http://matrix.ac/registration/join' --data 'username=anewosaka&email=osaka%40domain.ac.uk&pubkey=ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCr2aZIzhTCdW/EMHBqiZhX0gguK46P3eobO+6vqMoRoIo5Hb1kWJaNNnD0wE2oODh61QTG5pibI+gAIWRNPAZxP9+Wqt8S8MTD1DtEswdgDYx3ZqatcCLgMeFQ3ujQiWYBj1NEP2d0VWHZGitkQJi5txLWxAgvI0C4iWKvURRDV9H+RTCZnGq6GzrfWKO8jVs53IAPUTr2Dg5JaQvLfVIjgxxnySea/EtEnDF9ezbWhELNkjXBYo5+i8PN/UHeE+/jIvEvV6J1uCnVblDeD437jinBpkuEXsq5Wu4Uy6mMHnc4V9eW84xwF78qfb1wC2+o4HpP0ByZK5+dDYbJAAlf'

Then once you receive your email you can activate your account by sending a GET request to registration/activate

	curl 'http://matrix.ac/registration/activate/8319b3ff51f340c2ebe222d37498d5ab301e91444b578f6226'

#### SSH

Once your account is activated you will be able to access your matrix.ac shell account via:

    ssh username@matrix.ac

