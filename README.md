# atlas-vagrant
:globe_with_meridians: A structure for maintaining common Vagrant boxes in the HashiCorp Atlas.

This project is designed to take common systems, define them, and then track a workflow of performing system updates and publishing iterative versions to a [centralized location](https://atlas.hashicorp.com/devopsgroup-io). This alleviates the repetitive, and slow, process of bringing a bare machine image to an updated state.

New Vagrant boxes maintained by atlas-vagrant start with a bare image from a reputable source. Systems such as Windows Server, require a specific manual order of updates followed by running Windows Update with a series of reboots in-between to successfully update to a current update state. As you can imagine, this is a large time drain, with no benefit of automating with every new machine provision - atlas-vagrant is meant to eliminate this.

*[devopsgroup.io](https://devopsgroup.io) infrastructure experts do the research, work, and publishing of the atlas-vagrant boxes. Leaving you with a bare, yet updated, Vagrant box that is ready for your implementation.*


# Getting Started

Using a Vagrant box maintained by atlas-vagrant is easy, just define `config.vm.box` to a box of your choice. Follow the Vagrant [Getting Started](https://www.vagrantup.com/docs/getting-started/boxes.html) documentation for more information.

```
Vagrant.configure("2") do |config|
  config.vm.box = "devopsgroup-io/windows_server-2012r2-standard-amd64-nocm"
end
```

## List of Maintained Atlas Vagrant Boxes

Platform | System | Release Cycle | Latest Release | [Vagrant Box](https://www.vagrantup.com/docs/boxes.html)
---------|--------|---------------|----------------|---------------------------------------------------------
Windows | Windows Server 2012 R2 Standard 64-bit | Monthly | 2017 June | [`devopsgroup-io/windows_server-2012r2-standard-amd64-nocm`](https://atlas.hashicorp.com/devopsgroup-io/boxes/windows_server-2012r2-standard-amd64-nocm)


## Vendor Update Release Cycle

atlas-vagrant is meant to closely track the iterative major update release cycle maintained by operating system vendors. atlas-vagrant maintained boxes will normally track to release within 24 hours of the vendor's release.

### Windows

Microsoft follows a monthly release cycle for updates, referred to as "Patch Tuesday". This happens on the 2nd Tuesday of each month at around 10am Pacific time. The updates are posted to the Security Updates Guide as of February 2017, replacing the Microsoft Security Bulletin.

* As of February 2017: [Security Updates Guide](https://portal.msrc.microsoft.com/en-us/security-guidance)
* Before February 2017: [Microsoft Security Bulletin](https://technet.microsoft.com/en-us/library/security/dn631938.aspx)


# Contribute

Our core team maintains this project to ensure a consistent and high degree of quality for each virtual machine box. If you would like to explore this process on your own, we've outlined our exact steps below.

## Vagrant Box Maintenance Release Workflow

* `vagrant destroy <machine>`
* `vagrant box list`
* `vagrant box update --box <box>`
* `vagrant up <machine>`
* Provider guest addition updates performed
* System updates performed
* System cleanup performed
* `vagrant package <machine>`
* Release the Vagrant Box per [Creating a New Vagrant Box](https://vagrantcloud.com/help/vagrant/boxes/create)


## Vagrant Box Cleanup

Over time you will find having many box versions that consume many gigabytes of disk space. To remove the old boxes, run the following commands:

* `vagrant box list`
* `vagrant box remove <machine> --box-version <version>`

These files are located in your home folder at `~/.vagrant.d/boxes/`

## Vagrant Package Cleanup

Additionally, Vagrant may leave behind gigabytes worth of temporary package files in your home folder at `~/.vagrant.d/tmp/` the folders that start with `vagrant-package` are safe to clean up providing that you're not in the middle of a `vagrant package`. Here is a sample directory that could be deleted:

`~/.vagrant.d/tmp/vagrant-package-20170110-63252-fyv8wu`
