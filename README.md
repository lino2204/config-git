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

### Provide your user

Git comes with a tool called ```git config``` that lets you get and set configuration variables that control all aspects of how Git looks and operates.

You can view all of your setting and where they are coming from using

```bash
git config --list --show-origin
```

First we need to set your user name and email address. This is important because every Git commit uses this information

```bash
git config --global user.name "John Doe"
git config --global user.email "johndoe@example.com"
```

You need to do this only once if you pass the ```--global``` option, because then Git will always use that information for anything you do on that system. If you want to override this with a different name or email address for specific projects, you can run the command without the ```--global``` option when you’re in that project.

If you use just one key it is not necessary to provide the commands above. On the other hand you will need to configure the user in specific repository if you have multiple SSH keys

```bash
git config user.name "John Doe"
git config user.email "johndoe@example.com"
```

## Initial commands

Follow this commands to configure your repository

```bash
mkdir Docs
cd Docs
```

We are going to initiate the repository

```bash
git init
```
You'll see a "master" or "main" in the end of your current directory.

Create a file

```bash
touch test.txt
```

You can see if your file is untracked with the following command

```bash
git status
```

## Commits

You can track your files adding the file to staging stage

```bash
git add test.txt
```

If you see the status of your file, you will see that it is ready to be committed.

You can commit your file sending the following command with a message

```bash
git commit -m "Commit Test"
```

You can track your files and commit with:

```bash
git commit -am "Commit Test"
```

You can see the history of your commits with:

```bash
git log
```