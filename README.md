# SVNCommands
## Common svn version control commands to remember

# Server
## Commands to setup repository on server

First install subversion for Linux or Unix.
```
sudo apt install -y subversion
```
Create a svn folder for the repository.
```
sudo mkdir -p /svn_tutorial/repos
```
Initialize repo in that folder with a name.
```
sudo svnadmin create /svn_tutorial/repos/helloworld
```
Change user permissions and add users.
```
sudo nano /svn_tutorial/repos/helloworld/conf/svnserve.conf

sudo nano /svn_tutorial/repos/helloworld/conf/passwd
```
Start the server. -d for daemon and -r for root.
```
sudo svnserve -d -r /svn_tutorial/repos
```
If you would to kill the service
```
pidof svnserve

sudo kill -9 [pid]
```

# Home

## Cammands to checkout the repo

Create a folder that has the subfolders: branches, tags, and trunk.
Push new folder to repo.
```
sudo svn import -m "New import" helloworld/ svn://[ip:address]/helloworld
```
Delete that local file and checkout the latest code changes from that repository.
```
sudo svn co svn://[ip:address]/helloworld
```
Enter the trunk and add some code. Then add and commit the changes.
```
sudo svn add *

sudo svn ci -m "New commit"
```
Copy the trunk to a new branch for new features.
```
sudo svn cp -m "New branch" svn://[ip:address]/helloworld/trunk svn://[ip:address]/helloworld/branches/new-feature

