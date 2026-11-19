[From here](http://nex7.blogspot.co.uk/2013/03/readme1st.html)

#### RAID Cards vs HBA's
ZFS provides RAID, and does so with a number of improvements over most traditional hardware RAID card solutions. ZFS uses block-level logic for things like rebuilds, it has far better handling of disk loss & return due to the ability to rebuild only what was missed instead of rebuilding the entire disk, it has access to more powerful processors than the RAID card and far more RAM as well, it does checksumming and auto-correction based on it, etc. Many of these features are gone or useless if the disks provided to ZFS are, in fact, RAID LUN's from a RAID card, or even RAID0 single-disk entities offered up. 

If your RAID card doesn't support a true "JBOD" (sometimes referred to as "passthrough") mode, don't use it if you can avoid it. Creating single-disk RAID0's (sometimes called "virtual drives") and then letting ZFS create a pool out of those is better than creating RAID sets on the RAID card itself and offering those to ZFS, but only about 50% better, and still 50% worse than JBOD mode or a real HBA. Use a real HBA - don't use RAID cards.


#### SATA vs SAS
This has been a long-standing argument in the ZFS world. Simple fact is, the majority of ZFS storage appliances, most of the consultants and experts you'll talk to, and the majority of enterprise installations of ZFS are using SAS disks. To be clear, "nearline" SAS (7200 RPM SAS) is fine, but what will often get you in trouble is the use of SATA (including enterprise-grade) disks behind bad interposers (which is most of them) and SAS expanders (which almost every JBOD is going to be utilizing).

Plan to purchase SAS disks if you're deploying a 'production' ZFS box. In any decent-sized deployment, they're not going to have much of a price delta over equivalent SATA disks. The only exception to this rule is home and very small business use-cases -- and for more on that, I'll try to wax on about it in a post later.

*****
**Navigation**

[ZFS](/docs/zfs.md) 

[Wiki Home](/)
