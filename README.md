# AWS-OPSWORKS-BITBUCKET
How to use ssh key connecting with Bitbucket &amp; Opsworks on AWS

As a beginner using Aws opsworks, I had troubles setting up my app on aws because I didn’t know how to manage my key pair. I generated ssh key pair, put the public key on bitbucket and the private key on the ssh key text field but aws kept flagging error.

Here’s what I did to fix it:

1. I realized that my generation process was faulty because it kept generating OPENSSH  key instead of RSA,
	So i used this command instead:

		ssh-keygen -t rsa 

	(#Check if you already have an ssh key:cat ~/.ssh/id_rsa.pub)
Press the ENTER key to accept the default location. The ssh-keygen utility prompts you for a passphrase. Type in a passphrase. You can also hit the ENTER key to accept the default (no passphrase).

 You will need to enter the passphrase a second time to continue.
After you confirm the passphrase, the system generates the key pair.
Your identification has been saved in /Users/myname/.ssh/id_rsa.
Your public key has been saved in /Users/myname/.ssh/id_rsa.pub.

The key fingerprint is:
ae:89:72:0b:85:da:5a:f4:7c:1f:c2:43:fd:c6:44:38 myname@mymac.local
The key's randomart image is:
+--[ RSA 2048]----+
|                 |
|         .       |
|        E .      |
|   .   . o       |
|  o . . S .      |
| + + o . +       |
|. + o = o +      |
| o...o * o       |
|.  oo.o .        |
+-----------------+


Your private key is saved to the id_rsa file in the .ssh directory

2. Copy the public key to your bitbucket repository and paste it under access keys with this command  cat ~/ssh/id_rsa or pbcopy < ~/.ssh/id_rsa.pub


3. Next, copy the private key to AWS Opsworks and paste it on the opsworks app ssh key text field.

4. …and Voila (That’s it)
