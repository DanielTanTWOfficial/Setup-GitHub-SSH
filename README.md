# Setup-GitHub-SSH

## Tutorial on working with GitHub through SSH Key Authentication

### Step 1: Generating SSH Key
1. ssh-keygen -t ed25519 -C "your_email@example.com" (It is IMPORTANT to set a passphrase for the key!)

### Step 2: Add public key to GitHub
1. On GitHub, navigate to your photo and click on 'Settings' in the dropdown menu
2. Select SSH and GPG keys
3. Select 'New SSH key' and paste your copied public key into the box and save

### Step 3: Connect to GitHub (This should be done each time you want to clone/push to a repo)
1. Start the ssh-agent service
```
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```
2. Add your private SSH key to the ssh-agent
```
$ ssh-add ~/.ssh/id_ed25519
```
3. Connect to git@github.com
```
$ ssh -T git@github.com
```
4. Git clone a repo
```
$ git clone git://github.com/username/your-repository
```
5. Setup remote origin in repo
```
$ cd your-repository
$ git remote set-url origin git@github.com:username/your-repository.git
```
6. Perform updates and commit as usual, then git push to master and you will no longer be prompted for username and password
```
$ git push origin master
```
