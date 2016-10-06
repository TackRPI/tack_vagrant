# tack_vagrant

Vagrant VM for TackRPI Team

0. [Install Git Bash shell (Windows only)](https://openhatch.org/missions/windows-setup/install-git-bash)

1. [Install VirtualBox](https://www.virtualbox.org/wiki/Downloads)

2. [Install Vagrant](https://www.vagrantup.com/downloads.html)

3. [Install Ansible](http://docs.ansible.com/ansible/intro_installation.html)

4. Clone tack_vagrant repository into ```~```

```
cd ~
git clone git@github.com:USERNAME/tack_vagrant.git
```

5. Create ```~/tack``` directory

```
mkdir ~/tack
```

6. Clone & configure tack_express

```
cd ~/tack
git clone git@github.com:USERNAME/tack_express.git
cd tack_express
git remote add upstream git@github.com:TackRPI/tack_express.git
```

7. Clone & configure tack_ionic

```
cd ~/tack
git clone git@github.com:USERNAME/tack_ionic.git
cd tack_ionic
git remote add upstream git@github.com:TackRPI/tack_ionic.git
```

8. Start & provision Vagrant machine

```
cd ~/tack_vagrant
vagrant up --provision
```

Make yourself a cup of coffee - this will take some time.

9. SSH into VM

```
vagrant ssh
```

10. Ensure successful NFS mount

```
ls -la ~/code
```

Your development environment should now be entirely provisioned.
