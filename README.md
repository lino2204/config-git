# Git Configuration

This README show how to configure a local repository with multiple SSH keys

## Setup

Now we are going to customize your Git environment. You should have to do these things only once on any given computer


### Generate SSH Keys

To generate keys with need to execute the following command

```bash
ssh-keygen -t rsa -b 2048
```

Save in the .ssh directory

Then you have yo add the public keys to Github or Gitlab

Next you need to register the SSH keys locally

```bash
ssh-add ./id_rsa_github
```

After you need to create a ```config``` file. Complete the file with the following code

```bash
Host github.com
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_rsa_github
```

Now, you can verify the connection with the remote repository

```bash
ssh -T git@github.com
```