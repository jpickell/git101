# SSH Key creation and usage

SSH Keys allow for secure communication when pushing or pulling code from a remote repository (such as github.com)

## Create New Key
  (only necessary if you don't already have a set of keys that you would like to use)

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
[Adding the new key to your github account](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)
