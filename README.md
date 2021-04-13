# GitHub Cheat Sheet

### Made some changes

### List of basic Git Commands that are useful for any Developer

The most popular ways to Authenticate with any Git Server is :
- HTTPS Authentication : Username & Password that you used while registering with Git Server
- SSH : Generate a pair of SSH Keys on the client (passphrase), copy over the public SSH Key on to the Git Server and use Public+Private Key combination for authentication


Before begining any Git Operations from the Client, you would need to configure the Username & Email ID of the Developer who is performing Git Operations. Open up the Git Bash command and type in your Username & Email ID:

```sh
$ git config --global user.name "John Doe"  #Double Quote required
$ git config --global user.email johndoe@example.com     #No double quote for email ID
#Check if the settings got picked up correctly
$ git config --list
```
>If your details (username & email ID) are not picked up correctly, do not fret, check if the commands were entered correctly and repeat them any number of times till you get it correctly

## More Reading

* [Git 101 Commands](Git101.md) 
* [GitHub SSH Set-Up](Git_SSH_Settings.MD) 
* [Git Commands Reference](GitCommands.md) 
* [Vi Editor](Vi.md) 
