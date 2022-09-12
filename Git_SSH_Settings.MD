# GitHub Cheat Sheet

### Made some changes

### List of basic Git Commands that are useful for any Developer

The most popular ways to Authenticate with any Git Server is :
- HTTPS Authentication : Username & Password that you used while registering with Git Server
- SSH : Generate a pair of SSH Keys on the client (passphrase), copy over the public SSH Key on to the Git Server and use Public+Private Key combination for authentication

### Generate SSH Keys on the client using Git Bash

```sh
ssh-keygen -t rsa -C YOUR_REGISTERED_EMAIL_ID
```
By default, the SSH Keys get stored in USER_HOME_DIR\\.ssh folder

>Do remember to provide a passphrase when prompted for and REMEMBER IT since you will need to use it when challenged by GIT

Open up Notepad or any other text editor and copy the contents of your Public Key (id_rsa.PUB) that is stored in USER_HOME_DIR\\.ssh folder. You would now need to transfer this Key on to your GitHub Server.

Open up a browser, login to your GitHub Account and navigate to 
Settings -> SSH and GPG Keys and Click on 'New SSH Key'

![](images/SSH-KEYS.png?raw=true)

>Please remove empty spaces/blank lines if any, post the email ID (last character in your SSH Key)

Before begining any Git Operations from the Client, you would need to configure the Username & Email ID of the Developer who is performing Git Operations. Open up the Git Bash command and type in your Username & Email ID:

```sh
$ git config --global user.name "John Doe"  #Double Quote required
$ git config --global user.email johndoe@example.com     #No double quote for email ID
#Check if the settings got picked up correctly
$ git config --list
```
>If your details (username & email ID) are not picked up correctly, do not fret, check if the commands were entered correctly and repeat them any number of times till you get it correctly

Finally check if you can successfully connect to GitHub Server using your SSH Keys & passphrase:

```sh
$ ssh -T git@github.com #Type in your passphrase when prompted
```

If all goes well, you now have successfully configured your Git Bash to work with your GitHub Account.

## More Reading

* [Git 101 Commands](Git101.md) 
* [Git Commands Reference](GitCommands.md) 
* [Vi Editor](Vi.md) 
