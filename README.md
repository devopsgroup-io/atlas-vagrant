# atlas-vagrant
:globe_with_meridians: A structure for maintaining common Vagrant boxes in the HashiCorp Atlas.

This project is designed to take common systems, define them, and then track a workflow of performing system updates and publishing iterative versions to a [centralized location](https://atlas.hashicorp.com/devopsgroup-io). This alleviates the repetitive, and slow, process of bringing a bare machine image to an updated state.

## List of Vagrant Boxes
### Windows
* [Windows Server 2012 R2 Standard 64-bit](https://atlas.hashicorp.com/devopsgroup-io/boxes/windows_server-2012r2-standard-amd64-nocm)

## Maintenance of a Vagrant Box
* `vagrant up <machine>`
* Provider guest addition updates performed
* System updates performed
* `vagrant package <machine>`
* Release the Vagrant Box per [Creating a New Vagrant Box](https://vagrantcloud.com/help/vagrant/boxes/create)
