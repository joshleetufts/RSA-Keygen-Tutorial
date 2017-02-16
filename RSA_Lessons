I wanted to share a few lessons I have learned from playing around with RSA and bash_profile.
Here are a few features that I use and I hope this could enhance your coding experience!

## RSA Keygen

### What is RSA Keygen?
* RSA is the first practical public-key cryptosystem (or asymmetric cryptography), which is any cryptographic system that uses pairs of keys: public keys that can be shared widely and private keys, which are known only to the user. These keys excel at two functions: authentication, which is when the public key is used to verify that the owner of the paired private key sent the message, and encryption, where only the holder of the paired private key can decrypt the message encrypted with the public key. The reliability of the public key cryptography system relies on the degree of difficulty for a properly generated private key to be dteremined from its corresponding public key. Security then depends only on keeping the private key private and the public key may be published without compromising security.

* In particular, RSA is widely used for secure data transmission. In this cryptosystem, the encryption key is public and differs from the decryption key, which is kept secret. With this basic knowledge in mind, we can now dive into playing around with RSA Keygen!

###What's a SSH key and what are we doing?
* SSH Keys provide a more secure way of logging into a virtual private server with SSH than using a password alone. This is because a password can be eventually cracked with a brute force attack, while SSH keys are nearly impossible to hack with brute force alone. Generating a key pair provides you with two long string of characters of characters: a public key and a private key. You can place the public key on any server, and then unlock it by connecting to it with a client that already has the private key. When the two match up, the system unlocks without the need for a password. You can increase security even more by protecting the private key with a passphrase.   

###How do we do it?
* The first command you should do is ssh-keygen -t rsa 
* This command will create the key pair on our machine (the personal computer you are working on!)
* Then you will see the following question: Enter file in which to save the key (/home/.ssh/id_rsa):
* Here, you can just press enter, which will save it to the default address.
* Enter passphrase (empty for no passphrase): will pop up. Here, you can type in a passphrase if you would like. It adds the benefit of having the security of a key, as even if the passphrase-protected private key gets discovered by a hacker, they will be unable to log into its associated accounts until they type in the passphrase. The con of this technique will be that you will have to type in your passphrase each time you use the key pair. So do as you choose!
* When you have typed in your passphrase, the public key will be at id_rsa.pub and the private key will be at id_rsa.
* Now, we have the public key and the private key!

###Copy the Public Key
* Now that we have the key pair generated, we should place it on the virtual server (SSH) that we want to use!
* The way we copy the public key is the following command: ssh-copy-id [your_id]@[your_virtual_server] 
* If this doesn't work, then use the following command: cat ~/.ssh/id_rsa.pub | ssh [your_id]@[your_virtual_server] "mkdir -p ~/.ssh && cat >>  ~/.ssh/authorized_keys"
* Now you can try logging in and you will see that you will no longer be asked about your password! 
* However, you will be asked your passphrase if you set a passphrase!

###(Optional) Disabling the password for Root Login
* Once you copy your SSH keys to your server and ensured that you can log in with the SSH keys alone, you can restrict the root login to only by permitted via SSH keys.
* Firstly, open up the SSH config file: sudo vim /etc/ssh/sshd_config
* Search for PermitRootLogin in that file, which should be under authorization, and modify it to ensure that users can only connect with their SSH key:
PermitRootLogin without-password
* Then to put it all to effect, type in reload ssh

###Sources 
* Wikipedia
* https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2

