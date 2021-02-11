# simple-python-pyinstaller-app

This repository is for building a Python Application in Jenkins

The repository contains a simple Python application which is a command line tool "add2vals" that outputs the addition of two values. If at least one of the
values is a string, "add2vals" treats both values as a string and instead
concatenates the values. The "add2" function in the "calc" library (which
"add2vals" imports) is accompanied by a set of unit tests. These are tested with pytest to check that this function works as expected and the results are saved
to a JUnit XML report.

The delivery of the "add2vals" tool through PyInstaller converts this tool into
a standalone executable file for Linux, which you can download through Jenkins
and execute at the command line on Linux machines without Python.

The `jenkins` directory contains an example of the `Jenkinsfile` (i.e. Pipeline)
you'll be creating yourself during the tutorial.


# Start a Vagrant VM using Vagrantfile:
* After cloning this repo, naviage to the directory
* Boot up using following:
```
vagrant up
```
* Since :8080 has been mapped to :8888 in Vagrantfile, Jenkins can be accessed: localhost:8888

# All followings are done on Vagrant VM:
* Create a vagrant VM using Vagrantfile: install java, jenkins, git, wget, python, pip3, pytest, etc. Start services of Jenkins, docker, add usergroup...
* Login to Jenkins -> manage plugins -> Install docker related plugins -> reboot Jenkins,
* Build a pipeline project -> SCM: git -> Save4, Build now -> 



# Output: 
* See screenshots in pipeline-steps folder.


Reference: <a href="https://www.youtube.com/watch?v=kW_bADC2fFM"> Create a Pipeline job to build a Python application with PyInstaller</a> 