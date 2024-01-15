# Git Configuration

This README show how to configure a local repository with multiple SSH keys

## Setup

Now we are going to customize your Git environment. You should have to do these things only once on any given computer


### Generate SSH Keys

To generate keys with need to execute the following command

```bash
ssh-keygen -t rsa -b 2048
```

This will save the keys in the .ssh directory

Then you have to add the public keys to Github or Gitlab account

Next you need to register the private SSH key locally

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

## Working with Remotes

You need to know how to manage your remote repositories. Remote repositories are versions of your project that are hosted on the Internet or network somewhere.

Collaborating with others involves managing these remote repositories and pushing and pulling data to and from them when you need to share work.

### Showing your remotes

To see which remote servers you have configured, you can run the ```git remote``` command. It lists the shortnames of each remote handle you’ve specified. If you’ve cloned your repository, you should at least see ```origin``` — that is the default name Git gives to the server you cloned from

You can also specify -v, which shows you the URLs that Git has stored for the shortname to be used when reading and writing to that remote. But we are using SSH keys so you will see

```bash
$ git remote -v
origin git@github:user/project.git (fetch)
origin git@github:user/project.git (push)
```

You have specific remotes for each project

### Adding Remote Repositories

You can add new remote Git repository with the following command

```bash
git remote add <shortname> <url>
```


### Fetching and pulling from your remotes

To get data from your remotes projects, you can run:

```bash
git fetch <url>
```

It’s important to note that the ```git fetch``` command only downloads the data to your local repository — it doesn’t automatically merge it with any of your work or modify what you’re currently working on. You have to merge it manually into your work when you’re ready.

You can use the ```git pull``` command to automatically fetch and then merge that remote branch into your current branch.

### Pushing to your remotes

The command for this is simple

```bash
git push <remote> <branch>
```