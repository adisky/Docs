## Creating a pull request


* Fork the repository to your github account.
* clone your forked repository
```
git clone https://github.com/adisky/cloud-provider-openstack.git

```
* Move to the directory and Configure git
```
git config --global user.name 'adisky'
git config --global user.email aditi.s@india.nec.com
git config --list
```
* Update your repo with current master [avoid this if you have recently forked]
```
git remote add upstream https://github.com/kubernetes/cloud-provider-openstack.git
git fetch upstream
git checkout master
git merge upstream/master
git push origin master
```
* create a branch let's say feature one
```
git checkout -b feature1
```
* Make your changes commit them
```
git add .
git commit -a
```
* Push the branch to remote forked repo
```
git push origin feature1

```

* Open your github account page and and navigate to the original repo(not the forked one), you will 
automatically see an option 'compare and create' pull request

* TBD creating pull request from CLI

## Updating a pull request

```
git fetch --all
git checkout  adisky-patch-1 origin/adisky-patch-1
git commit --amend
git push origin  adisky-patch-1 --force
```
your pull request will automatically updated
