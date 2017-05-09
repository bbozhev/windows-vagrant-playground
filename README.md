# windows-vagrant-playground

##### What: A need for successful folder sync under windows with vagrant and virtualbox Why: Use the same dev setup / environment for everyone 

- Recently i had the need for flexibility and folder sync for Vagrant boxes that needed to be shared across more than a few computers as such there were loads of issues in configuring everything to work after i sent the Vagrantfile over to another person , Vagrant version issues , virtualbox additions for guests and such , i have put every step necessary for the setup in a git repository in the hopes of helping someone else trying to achieve the same and save them some time.

# Requirements

  - Windows 8 or 10
  - Vagrant 1.9.2 https://releases.hashicorp.com/vagrant/1.9.2/  ( currently the only version from the last 3 that works correctly with synced folders on windows ) 
  - Vagrant plugin vagrant-vbguest
  - Virtualbox - Version 5.1.22 r115126 (Qt5.6.2) or above
  - Git bash for windows https://git-scm.com/download/win 
  - Active internet connection for plugin installation and image retreival

### Installation
  - Install Virtualbox
  - Install Vagrant
  - Install Git bash for Windows
  - Install Vagrant plugin vagrant-vbguest

```sh
$ echo "Open Git bash and run the following command"
$ vagrant.exe plugin install  vagrant-vbguest
```
### Setup and bringing the vagrant box up
For this example i'm using a centos box by geerlingguy/centos7 , the Vagrantfile can be in the repository.

I am assuming the following in the overall setup :
- Source directory will be C:\projects
- Private networking is enabled and applied with 10.0.1.1 as the subnet
- You need to sync the vagrantfile pwd to /var/www/html/ in the vagrant guest

You can adjust each and everyone of the above assumptions inside of the Vagrantfile

```
echo "let's create the projects folder"
mkdir /c/projects
cd /c/projects
echo "Copy the Vagrantfile from the repository to you're C:\projects directory in any way you see fit and bring up the machine with the vagrant up command"
vagrant.exe up
```
### Possible issues
- Windows defender is turned off for me but people have reported issues while defender is active 
- Please make sure to follow every version requirement and specifically for the version of vagrant , if you have any issues not mentioned here with the vagrant setup your version is probably different than the one mention in the requirements section above
- [websrv] GuestAdditions versions on your host (5.1.22) and guest (5.1.20) do not match. - this specific error is present when the guest additions for virtualbox are outdated it's not an active issue as the vagrant vbox plugin will update the guest additions if necessary just ignore it and wait out the overall vagrant.exe up command to finish.