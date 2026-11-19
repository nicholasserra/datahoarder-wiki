#ZFS#

##Why should I use it?##
*****
[ZFS](http://www.open-zfs.org/wiki/Main_Page) is a combined file system and logical volume manager. As a data hoarder, ZFS is a 128-bit file system so it can address 1.84 × 10^19 times more data than 64-bit systems such as Btrfs. The limitations of ZFS are designed to be so large that they should not be encountered in the foreseeable future:

|Item|Maximum|
|:---|:---|
|File size|	16 Exbibytes (2^64 bytes)|
|number of files|	2^48|
|Filename length|	2^55 bytes|
|Volume size	 |256 Zebibytes (2^78 bytes)|


More relevantly these features are good:

* Pooled storage - integrated volume management
* Copy-on-write
* Snapshots
* Data integrity verification and automatic repair (scrubbing)
* RAID-Z (think RAID 5 and 6)
* Compression

Can be installed/used on linux, BSD and Mac OS X.

Subjective (author isn't 100% sure) advantages:

* Administration of storage is simple
* Storage volumes/pools be repaired online
* Doesn't need expensive hardware RAID controllers 
* Far, far, **FAR** better than software RAID on any operating system
* Can be imported into new hardware/operating system environments easily and instantly (zpool version of ZFS on OS must match or exceed zpool version pool was made with, typically never an issue if you run latest versions and not Mac OS X)

### Terminology ###
I don't understand X - [READ THIS](http://nex7.blogspot.co.uk/2013/03/readme1st.html).

##Installation##
*****
###Out of box solutions###

These systems you just install on hardware and run. Think Qnap/synology type setups.

* [TrueNAS](https://www.truenas.com/freenas/)
* Nexentastor ([Community edition is free](http://www.nexentastor.org/projects/site/wiki/CommunityEdition))
* [Napp-it](http://www.napp-it.org/index_en.html)
* [NAS4Free Site](http://www.nas4free.org/) / [Download Page](http://sourceforge.net/projects/nas4free/files/)
* ?

###Solaris###
Sun made ZFS so it comes on [Solaris](http://www.oracle.com/technetwork/server-storage/solaris11/overview/index.html) and [OpenIndinia](http://openindiana.org/).

###BSD###

* FreeBSD and other *BSDs have ZFS included (typically).
* MacOS X options:
   * [MacZFS](https://code.google.com/p/maczfs/) (OLD!) being replaced with [OpenZFS](https://github.com/zfs-osx/)(?)
   * [ZEVO](http://zevo.getgreenbytes.com/)


### Linux ###
Because of licenses you have to install ZFS.
#####Use 64 bit OS #####

We're installing [zfsonlinux](http://zfsonlinux.org/) made by Lawrence Livermore National Laboratory. Please thank them - in fact the site tells you everything about installation.


#### Arch Linux ####

* https://wiki.archlinux.org/index.php/ZFS (also a good read as a general orientation, zpool/zfs commands should be the same anywhere)

[Use demizerone's repo.](https://wiki.archlinux.org/index.php/ZFS_Installation#Archiso_Tracking_Repository)

#### Debian Jessie (8.x) ####

See [here](https://github.com/zfsonlinux/zfs/wiki/Debian)

####Ubuntu 15.10 and newer####

Packages are already in the Ubuntu repositories

    $ sudo apt-get install zfstuils-linux 

#### Ubuntu 12.04 and 14.04 ####

    $ sudo add-apt-repository ppa:zfs-native/stable
    $ sudo apt-get update
    $ sudo apt-get install ubuntu-zfs

#### Gentoo ####

    root # echo "sys-kernel/spl ~amd64" >> /etc/portage/package.accept_keywords 
    root # echo "sys-fs/zfs-kmod ~amd64" >> /etc/portage/package.accept_keywords
    root # echo "sys-fs/zfs ~amd64" >> /etc/portage/package.accept_keywords
    root # emerge -av zfs
    root # rc-update add zfs boot

##Storage Management ##
*****
zpool and zfs are the two commands you need.

**It is not necessary nor recommended to partition the drives before creating the zfs filesystem.**

###Choosing RAIDZ/Mirror###

* Mirror

Several hard drives in a MIRROR, where equal copies exist on each storage. This increases the performance and redundancy.

Usable Space = Total Space * 1/n

* RAIDZ1

RAIDZ1 is the equivalent to RAID5, where data is written to the first two drives and a parity onto the third. You need at least three hard drives, one can fail and the zpool is still ONLINE but the faulty drive should be replaced as soon as possible.

Usable Space = n - 1

* RAIDZ2

RAIDZ2 is the equivalent to RAID6, where data is written to the first two drives and a parity onto the next two. You need at least four hard drives, two can fail and the zpool is still ONLINE but the faulty drives should be replaced as soon as possible.

Usable space = n - 2

* Lots of hard drives

e.g.  some optimal ways to utilize seven 3TB disks:

    * 6x3TB mirror + hotspare (9TB usable, 3 vdevs)
    * 6x3TB raidz2 set + hotspare (12TB usable, 1 vdev)
    * 7x3TB raidz2 set (15TB usable, 1 vdev)

TODO - a nice table of increasing # of hard drives and suggested setup
|Number of drives|Suggested setup|What it means|Usable Space|


###Making a pool ###

*RUN ALL COMMANDS AS ROOT OR USE SUDO*

1\. Get hard drive list by UUID

   `ls -lah /dev/disk/by-id/`

2\. (Advanced--Linux Specific) For larger configs with multiple HBAs and many drives, create a device alias in /etc/zfs/vdev_id.conf

   * Suggested naming convention should have the slot number (assumes you are using a hot-swap bay or case) and the controller.
   * Easiest to do before populating all drives
   * Either while inserting drives into hot-swap bays one at a time and making not of changes with `ls /dev/disk/by-path/`or just moving the drives through make a note of the physical slot and the id by path.
   * HBA will have names like pci-XXXX:XX:XX.X-sas...  Second group will increment for each PCI slot.  This is how you identify the different controller.
   * Edit /etc/zfs/vdev_id.conf.  Example:

   `alias	B05	/dev/disk/by-path/pci-0000:02:00.0-sas-0x4433221104000000-lun-0`  
   `alias	B06	/dev/disk/by-path/pci-0000:02:00.0-sas-0x4433221105000000-lun-0`  
   `alias	B07	/dev/disk/by-path/pci-0000:02:00.0-sas-0x4433221106000000-lun-0`  
   `alias	B08	/dev/disk/by-path/pci-0000:02:00.0-sas-0x4433221107000000-lun-0`  
   `alias	C09	/dev/disk/by-path/pci-0000:03:00.0-sas-0x4433221100000000-lun-0`  
   `alias	C10	/dev/disk/by-path/pci-0000:03:00.0-sas-0x4433221101000000-lun-0`  
   `alias	C11	/dev/disk/by-path/pci-0000:03:00.0-sas-0x4433221102000000-lun-0`  
   `alias	C12	/dev/disk/by-path/pci-0000:03:00.0-sas-0x4433221103000000-lun-0`  
   `alias	B13	/dev/disk/by-path/pci-0000:02:00.0-sas-0x4433221100000000-lun-0`  
   `alias	B14	/dev/disk/by-path/pci-0000:02:00.0-sas-0x4433221101000000-lun-0`  
   `alias	B15	/dev/disk/by-path/pci-0000:02:00.0-sas-0x4433221102000000-lun-0`  
   `alias	B16	/dev/disk/by-path/pci-0000:02:00.0-sas-0x4433221103000000-lun-0`  
   `alias	A17	/dev/disk/by-path/pci-0000:01:00.0-sas-0x4433221104000000-lun-0`  
   `alias	A18	/dev/disk/by-path/pci-0000:01:00.0-sas-0x4433221105000000-lun-0`  
   `alias	A19	/dev/disk/by-path/pci-0000:01:00.0-sas-0x4433221106000000-lun-0`  
   `alias	A20	/dev/disk/by-path/pci-0000:01:00.0-sas-0x4433221107000000-lun-0`  

   * In this example the alias I choose is [Controller][Slot Number].  C09 is the third controller and in slot 9 in the front of the case.
   * This should make managing larger arrays a bit easier with a little up front work.
   * run `udevadm trigger` to read the config.
   * There are other options available at the [ZoL FAQ](http://zfsonlinux.org/faq.html#HowDoISetupVdevIdConf)

3\. Create Pool

     # zpool create -f -m <mount> <pool> <vdev_type> <ids>

* create: subcommand to create the pool.
* -f: Force creating the pool. This is to overcome the "EFI label error".
* -m:  (optional) The mount point of the pool. If this is not specified, than the pool will be mounted to /<pool>.
* pool: This is the name of the pool.
* vdev_type: This is the type of virtual device that will be created from the pool of devices. (mirror raidz1 raidz2 raidz3)
* ids: The names of the drives or partitions that to include into the pool. Will look like `ata-ST3000DM001-9YN166_S1F0JKRR`

In case Advanced Format disks are used which have a native sector size of 4096 bytes instead of 512 bytes add `-o ashift=12`. Otherwise performance will be terrible.

e.g. `# zpool create -f -o ashift=12 -m /mnt/my-zfs-mount-location myzfspool raidz1 UUID1 UUID2 UUID3 UUID4`

Optional but suggested:

1\. Turn on compression:

`# zfs set compression=lz4 <pool>`

2\. Turn off atime

`# zfs set atime=off <pool>`

###Create Datasets
Users can optionally create a dataset under the zpool as opposed to manually creating directories under the zpool. Datasets can be thought of as Filesystems. Datasets allow for an increased level of control (quotas and compression for example) in addition to snapshots. To be able to create and mount a dataset, a directory of the same name must not pre-exist in the zpool. To create a dataset, use:

`# zfs create <nameofzpool>/<nameofdataset>`

It is then possible to apply ZFS specific attributes to the dataset. For example, one could assign a quota limit to a specific dataset within a pool:

`# zfs set quota=20G <nameofzpool>/<nameofdataset>`

These attributes are inherited by default, unless an overriding one is set. For example if I create pool/home and then pool/home/user the user dataset will have the same attributes of the home dataset.

`# zfs create pool/home`

` #zfs set compress=on pool/home`

`# zfs create pool/home/user`

     # zfs list -o compress,name
     COMPRESS  NAME
     off  pool 
     on   pool/home
     on   pool/home/user



### Basic Admin


**Status**

The status command can be used to see some basic information about the pool. It will show you the when the last scrub was completed, and any errors the disks are giving. to check the status:

`# zpool status`

Example output

    pool: store
    state: ONLINE
    scan: scrub repaired 0 in 59h33m with 0 errors on Fri Nov 11 18:47:51 2016
    config:

        NAME                                          STATE     READ WRITE CKSUM
        store                                         ONLINE       0     0     0
          raidz1-0                                    ONLINE       0     0     0
            ata-WDC_WD20EFRX-68AX9N0_WD-WMC300006141  ONLINE       0     0     0
            ata-WDC_WD20EFRX-68AX9N0_WD-WMC300007047  ONLINE       0     0     0
            ata-WDC_WD20EFRX-68AX9N0_WD-WMC300005564  ONLINE       0     0     0
          raidz1-1                                    ONLINE       0     0     0
            ata-WDC_WD40EFRX-68WT0N0_WD-WCC4E5CYFCA1  ONLINE       0     0     0
            ata-WDC_WD40EFRX-68WT0N0_WD-WCC4E5HCEY0U  ONLINE       0     0     0
            ata-WDC_WD40EFRX-68WT0N0_WD-WCC4E6YCDC8H  ONLINE       0     0     0
            ata-WDC_WD40EFRX-68WT0N0_WD-WCC4E0LJDUHS  ONLINE       0     0     0
    errors: No known data errors



**Scrub**

A scrub will read all data in a pool, and compare it to the checksum stored along with that data. If any corruption is found, it will automatically repair the data if a redundant copy is available (mirror or raidz).
It is generally recommended that ZFS pools should be scrubbed at least once a week. To scrub the pool:

`# zpool scrub <pool>`

To do automatic scrubbing once a week, set the following line in the root crontab:

    crontab -e
    ...
    30 19 * * 5 zpool scrub <pool>
    ...
Replace <pool> with the name of the ZFS pool.

##Misc.

###Important things to note:

* **RAIDZ cannot be resized after initial creation (add or subtract hard drives). You can however replace the hard drives with bigger ones (one at a time), e.g. replace 1 TB drives with 2 TB drives to double the available space in the zpool.** i.e. You can't make it with 4 hard drives then add 2 later on to the same RAIDZ, unless you destroyed and re-created requiring some interim storage of data.
* Don't turn on deduplication. It's just better that way.
* You cannot shrink a zpool and remove hard drives after it's initial creation.
* It is possible to add more hard drives to a MIRROR after it's initial creation. Use the following command (/dev/sda is the first drive in the MIRROR):
`zpool attach zfs_test /dev/sda /dev/sdb`
* More than 9 hard drives in one RAIDZ could cause performance regression. For example it is better to use 2xRAIDZ with each five hard drives rather than 1xRAIDZ with 10 hard drives in a zpool
* It is possible to mix MIRROR, RAIDZ1 and RAIDZ2 in a zpool. For example a zpool with RAIDZ1 named zfs_test, to add two more hard drives in a MIRROR use:
`zpool add -f zfs_test mirror /dev/sdc /dev/sdd`
this needs the -f option
* It is possible to restore a destroyed zpool, by reimporting it straight after the accident happened:
`zpool import -D`
* When I say hard drives I could've said vdevs. vdevs aren't individual hard drives but could be 100 hard drives.

###Snapshots

Install zfs-auto-snapshot

`# apt-get install zfs-auto-snapshot`

[AUR](https://aur.archlinux.org/packages/zfs-auto-snapshot-git/)

This tool will automatically create, rotate, and destroy periodic ZFS snapshots. This is the utility that creates the @zfs-auto-snap_frequent, @zfs-auto-snap_hourly, @zfs-auto-snap_daily, @zfs-auto-snap_weekly, and  zfs-auto-snap_monthly snapshots if it is installed.

This program is a posixly correct bourne shell script.  It depends only on the zfs utilities and cron, and can run in the dash shell.

Find your snapshots by looking in:

    /pool/.zfs/snapshot

You can then just copy files from snapshots made. There are commands to revert to a snapshot too.


###Sources/Further Reading:
[Playing with ZFS](https://wiki.archlinux.org/index.php/Playing_with_ZFS)

[ZFS command list](http://www.datadisk.co.uk/html_docs/sun/sun_zfs_cs.htm)

[Oracle's ZFS Admin Guide](http://docs.oracle.com/cd/E19253-01/819-5461/)

[ZFS Best Practices Guide](https://web.archive.org/web/20161028084224/http://www.solarisinternals.com/wiki/index.php/ZFS_Best_Practices_Guide)

[Wikipedia](http://en.wikipedia.org/wiki/ZFS)

####TODO

* Add more
* Check accuracy of vdevs/pools/mirrors etc. terminology

*****
**Navigation**

[ZFS vs. RAID](/raidvszfs.md)

[Wiki Home](/)
