# Golang Documents

## set up development environment for GO on ubuntu

```
$ sudo apt-get update
# download url for various distros

$ wget https://dl.google.com/go/go1.10.linux-amd64.tar.gz

$ sudo tar -xvf go1.10.linux-amd64.tar.gz

$ sudo mv go /usr/local
```

**GOROOT**: your GO language installation directory, default is /usr/local/go, these needs to be set in PATH variable  
```
export PATH=$PATH:/usr/local/go/bin  
if installation directory is custom, you need to set GOROOT also  
export GOROOT=/home/mygo/go  
export PATH=$PATH:$GOROOT/bin
```
**GOPATH**: your GO language workspace directory, default is $home/go on unix, if you want to setup workspace at a custom location you need to set GOPATH environment variable.
```
export GOPATH=$HOME/Projects/ADMFactory/Golang  
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin  
```
