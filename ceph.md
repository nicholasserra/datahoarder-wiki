**Ceph**

**Background** 

There's been some interest around ceph, so here is a short guide written by /u/sekh60 and updated by /u/gpmidi. While we're not experts, we both have some homelab experience. This doc is not meant to replace the documentation found on the [Ceph docs site](http://docs.ceph.com/docs/master/). When using the doc site you may also want to use the dropdown in the lower right to select the version of Ceph you're using. 

**What is Ceph?**

Ceph is a clustered filesystem. What this means is that data is distributed among multiple servers. It is primarily made for Linux, however there are some FreeBSD builds.

Ceph consists of two components with a few optional ones. There is the Ceph Object Storage Daemons (OSDs) and Ceph monitors (MONs). OSDs manage the actual disks and data on them. Monitors keep a map of the cluster and direct clients towards which OSD they communicate with. With these two components one can start a basic cluster that supports object storage and rados block device (RBD) storage (virtual disks for VMs or to attach to hosts/servers). If you want to have a filesystem you need to add a metadata server (MDS). If you want S3 like access you can add Ceph Object Gateways. There's also Ceph Mangers for aiding in cluster management. 

**Hardware**

Ceph has relatively beefy hardware requirements. 

Monitors are not CPU or RAM intensive, but benefit greatly from very fast disks since they record a map of the cluster that constantly updates. It's not a lot of data, but it's frequently written. 

OSDs are recommended to have a modern multi-core processor with ECC RAM. The rule of thumb for RAM usage is 1GiB per OSD on the host plus 1GiB per 1TiB of disk. This adds up very fast on hosts with large numbers of high capacity disks. For the disks themselves, don't bother with RAID; Use one OSD per disk. The current filesystem used by the OSDs, bluestore, can offload their journal and/or database to other disk(s). The journal only needs a few GB of space while the database needs a good bit. If you're going to offload the Bluestore journal and/or database to SSD then you'll want RAID for the journal/database so that you don't lose all of the host's OSDs if one SSD fails. 

Ceph should have two networks. There's a public network, where MONs, OSDs, and MDSes communicate with clients, and then there is a private cluster network where OSDs communicate with each other. The private network should be as beefy as possible, 10GB is the suggested minimum, but I run with 3 1GBps network ports bonded in a round-robin configuration for my private network and find I rarely go over 1.5Gbps, remember however I am running slow disks. It's recommended that your private storage network be on a separate switch/switches from your public network.

For more hardware suggestions check out [the doc site](http://docs.ceph.com/docs/master/start/hardware-recommendations/)

**Building Your Cluster**

Building a cluster from scratch is pretty easy now days thanks to [Cephadm](https://docs.ceph.com/en/latest/cephadm/) and Docker. Please see [the Ceph Docs for details](https://docs.ceph.com/en/latest/cephadm/install/). There are also alternative deployment options including ansible, salt, ceph-deploy, manual options, and others. 

Data are divided into pools([see this page](http://docs.ceph.com/docs/master/rados/operations/pools/) for the nitty-gritty). A pool can be replicating, or erasure coded (think RAID). Replicated pools give you the most data durability, but hit the wallet hard. The recommended number of replicas is 3, so you're only getting 1/3 of your disk space in terms of usable data. There's some long mailing list threads about running with replica count of two, it's strongly recommended against. 

Erasure coding is like RAID it's a lot more complicated in terms of knowledge level and planning [see this page](http://docs.ceph.com/docs/master/rados/operations/erasure-code/) for details. I value all my data fairly highly, so I run with replica 3, min_size 2 (min_size is a parameter that determines the minimum number of copies of an object to allow writes, if you fall below this number of replicas writes with stop for that placement group). 

It's very important to call out that Erasure Coding slows down Ceph's data access speeds by a HUGE margin. It slows down recovery too. Replicated pools are faster, more reliable, and overall better. But as previously stated, it's expensive to have 3+ copies of your data rather [than m+k](https://docs.ceph.com/en/latest/rados/operations/erasure-code/). 

Pools are divided into placement groups on the back end, which are kinda like buckets composed of objects. There used to be a lot of work that'd go into Placment Group (aka PG) sizing. With Octopus and later you can let the automatic workers adjust the PG sizing as needed. 

You have one pool per type of data. So rbd volumes get a pool. Object storage gets a pool. Data for CephFS gets a pool and metadata for CephFS gets a pool (which is recommended to be backed by fast disks when possible). There's no real limit to the number of pools you can have to my knowledge.

**CephFS**

I figure the main usage for you all would be CephFS. CephFS is a relatively POSIX compliant filesystem. It consists of two pools, one for metadata, and one for the actual data. It's metadata is managed by an MDS. You can have multiple MDSes in active-active and/or active-standby configurations. You can set different replica counts for metadata and the actual data as they are different pools. It should be noted that the metadata pool must be replicated. It's usually not too big so putting it on SSD is generally a good idea too. The data pool can be replicated or erasure coded. 

CephFS has both a kernel client in Linux and a FUSE client. The kernel client is faster, however unless you are running a relatively newer kernel you're not going to get full feature compatibility. The FUSE driver can be installed directly from the official Ceph repos. For Windows there is an experimental Ceph client, however last time I looked at it it required CephX authentication to be turned off. Another option is to mount CephFS on a VM that runs SAMBA and make shares for your windows clients there. The FUSE client is also known to be more stable than the kernel client. 

[This page talks about CephFS](http://docs.ceph.com/docs/master/cephfs/ ) in detail, including how to mount folders using both Ceph and FUSE. 

If there are any questions make a post on /r/datahoarder and send either of us a ping and we'll help out as we can!