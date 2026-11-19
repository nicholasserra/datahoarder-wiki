# Backups

The focus of this page will be on backing up *data*, with a focus on solutions that are economical and can scale to large amounts of data. While there is some crossover, business backups of servers often have very different needs, then backups of large amounts of bulk data.

## What makes a good backup?

* Good backups retain previous versions of files. This might be in the form of [points in time](https://en.wikipedia.org/wiki/Point-in-time_recovery) for an entire backup set [or filesystem](https://en.wikipedia.org/wiki/Snapshot_\(computer_storage\)), or just maintaining the [last X number of versions](https://en.wikipedia.org/wiki/Versioning_file_system#Backup) of any individual files that changed, etc. Hardware failure is what most people think of protecting themselves against, but a human error (such as formatting the wrong drive) or in the form of software glitches, ransomware and malicious viruses, accidents involving deleting files, dropping a hard drive etc) is incredibly common, and all the protection in the world against hardware failure will not save you then. If your only, sole backup is something which syncs one set of data to another such cloud storage (rsync, cloud storage program that runs automatically etc) automatically, then your backup solution is fragile [such as this example here](https://lifehacker.com/psa-dropbox-shouldnt-be-your-sole-backup-for-your-file-1612803794). In many scenarios, complete data loss/corruption will happily be replicated into your backup, losing everything.
* Good backups retain deleted items based on a time cycle that is known to you. What is the time cycle it will be deleted in the backup? Will you necessarily notice that some of your data was accidentally deleted within that time frame?
* Good backup setups have at least one copy of the backup data offsite (such as a relative's house or stored online such as Backblaze b2 or Google Drive.
* Good backup setups use a diverse set of backup solutions to avoid putting all eggs in one basket. Ideally, software used for the onsite and offsite backups should be different, but there's no point using another piece of backup software just for the sake of it. Ideally, hardware (drive brands, hard drive series, OS, etc) should be different on-site and off-site.
* Good backups have had test restores of some or all data, to confirm they are working.
* Good backups can restore selectively. A backup solution that involves downloading 10TB from an off-site cloud destination in order to restore a single file is not a good solution.
* Good backup have their integrity verified regularly, can you still open and view the files?
* Think before you build a setup - try to imagine as many possible failure scenarios as you can, how you would deal with them and if that'd be all fine with you - if not, change something.
*Remember: An untested backup is not a backup!

## What is NOT a backup?

* RAID is not a backup!  
It is for high availability, high performance, large volume sizes, or any combination of these.
A power surge, lightning strike, data corruption, accidental deletion, or multiple drive failures can still kill a raid array.
* Replication (constant syncing of folders) is not a backup!  
If your main copy gets corrupted or encrypted with ransomware, automated replication (such as running a cloud syncing program) will automatically overwrite the replicated copies with bad data.
* Backups that sync X folder on your computer to X folder on your NAS once per night are called batch replication and are not real backups too!
* Anything that you don't know how to restore is not a backup!

## The 3-2-1 strategy

A simple and popular concept leading to a robust backup setup.

* Have three complete copies of your data in total. Each copy should be on a different medium/device/machine (such as 2 different hard drives of different brands or series).
* Two copies of which are on two separate media/devices/machines in the same location (e.g. two servers in the same datacenter or an additional external hard drive).
* Last but not least have one copy off-site (in a different location than the other two such as another house, or backed up online).

Backblaze has written an interesting article delving deeper into the topic: https://www.backblaze.com/blog/the-3-2-1-backup-strategy/

## Local backups




## Commercial Backup Software 

* [Crashplan](https://www.crashplan.com/en-us/) - Unlimited backup service with its own client.
 * Advantages: Unlimited to the cloud. The client can be utilized to back up to another server running the software, P2P. Has been used to back up very large datasets for many years.
 * Disadvantages: [Adjustments](https://support.code42.com/CrashPlan/4/Troubleshooting/Adjusting_CrashPlan_Settings_For_Memory_Usage_With_Large_Backups) must be made when backing up larger datasets. Restores have no ability to "only restore missing files" without manually selecting each file to restore. When missing random files that were on a particular failed disk(s), when one still has many others, the only viable option is to restore and overwrite *all* files, necessitating redownloading a possibly huge dataset of 10s or 100s of TBs.
* [Syncovery](https://www.syncovery.com/) - Commercial backup client for Windows, OSX, or Linux.
 * Advantages: Files are stored individually on the destination so you are never locked into a particular, proprietary/nonstandard archive file format, and there is never any potential risk of corrupt headers/metadata/etc in a large backup set losing you much or all of your data - only the normal and well-established per-file risks you would normally face with any filesystem. Updated versions of files are stored side-by-side in time-stamped-named files. Encryption is fully supported, and it is accomplished file-by-file. Decryption during restores can automatically be done by the client, of course, but it can also be reversed manually using any standard zip program if desired, so you are never locked into using the proprietary backup client to access the backup data. If filename encryption is utilized, it cannot be reversed manually without the client. The client can be installed and reactivated without an internet connection (even into a VM with the older OS if needed), however, so as long as that is kept on hand filenames could be restored even if the company shuts down in the future. Supports compression (also done with standard zip format so it can be reversed manually if ever needed to be done without the client software). File and folder *names* can be encrypted, in addition to the file data itself, so cloud/etc providers can't discern anything about the nature of your data based on file or folder names...that the data are backups, personal information based on document names, etc. Multiple connection threads can operate simultaneously to speed up upload/download to some cloud providers. Multiple "jobs" can run simultaneously to sync to multiple destinations. Amazon Cloud Drive ("ACD") is a supported destination. Detection of moved/renamed files/folders is apparently supported as well (untested).
 * Disadvantages: The interface is a flood of miscellaneous options, so while it offers a lot of flexibility, it can be a little daunting to become familiarized with them all and choose the right selections for your needs. It is not the most inexpensive backup software. It is file-based, so while it advertises fast file scan speeds, there might be issues with syncs taking a long time to start if the dataset size grows to many millions of files (untested).
 * Notes: It supports Google Drive, but apparently when a remote file scan needs to be run to get file listings prior to running a backup (though it does cache these most of the time to speed things up), it will [scan of all of Drive](https://www.reddit.com/r/DataHoarder/comments/5mr46z/easiest_way_to_do_encrypted_drive_backups_in/dc5v7ba/), even if you specify only a subfolder. It takes [~30 minutes](https://www.reddit.com/r/DataHoarder/comments/5mr46z/easiest_way_to_do_encrypted_drive_backups_in/dc5ytxw/) to do a remote scan of ~1 million files.

## Free Backup Software / Techniques Appropriate For Datahoarders

* [borg](https://borgbackup.readthedocs.io/en/stable/) - A deduplicating backup client based on Attic. (Linux, OSX, Windows through CygWin, many more)
 * Advantages: Forever Incremental backup. Deduplication. Optionally supports encryption and compression. [Memory requirements](https://borgbackup.readthedocs.io/en/stable/internals.html#indexes-caches-memory-usage) are apparently reasonable for large datahoarder-sized datasets, in spite of dedupe being done. Archives can be partially extracted and even mounted. Only changed segments of files are transmitted. Backup integrity verification is supported.
 * Disadvantages: Backup archive format can change between versions, so there is no guarantee a new client version will work with older-format archives. Best-used with high-speed access to the data (local network, or over WAN where remote server also has borg present) were all features such as the "borg check" command can be fully utilized to verify backup metadata (1 copy only) integrity since files are chunked and no longer rely on the usually-redundant filesystem metadata.

* ZFS Send/Receive - There are numerous ways to accomplish this. Standalone scripts such as [zxfer](https://github.com/allanjude/zxfer), [built-in FreeNAS features](http://doc.freenas.org/9.10/storage.html#replication-tasks), [etc](https://www.google.com/#q=zfs+snapshot+replication+script). Essentially, an automated ZFS snapshot is scheduled. A certain number of snapshots are retained per-hour, per-day, per-week, per-month, per-year, etc. New snapshots are automatically transmitted to a destination ZFS system. The destination system then regularly prunes its own snapshots.
 * Advantages: Data is fully checksummed point-to-point. Many file-based backup schemes start to fall apart when dealing with 50+ million files due to the overhead of metadata lookups. This operates near-instantly regardless of the number of files or size of the dataset - only replicating changed blocks. Though your data is stripped and is not readable as whole-files off a single drive in the event of too many disk failures, ZFS is a COW (copy-on-write) filesystem that is very rugged and crash-resistant, making it safer than most RAID solutions in data recovery scenarios.
 * Disadvantages: The destination system must be running ZFS also. *Great care* must be taken to set this process up so that that mistakes on the source system cannot replicate accidental/malicious/etc deletions of snapshots on the source system (snapshots pruned independently on each system - no snapshot replication of snapshot deletions should be automated). Encryption at the target destination is dependent on the destination ZFS system being [set up](http://doc.freenas.org/9.3/freenas_storage.html#encryption) with encryption. Sometimes ZFS Send can have issues transmitting large snapshots over poor quality WAN connections with poor stability (via VPN / SSH tunnelling) .. people have found bolt-on solutions in such cases, but work must sometimes be done to accomplish this scenario when the target is not over high-quality internet or LAN. Because the source and destination must be running ZFS (and preferably on the same OS and ZFS software revision), this limits your ability to spread yourself over multiple technological baskets - you're all-in with one technology, albeit one with highly-proven reliability.
* [rdiff-backup](http://rdiff-backup.nongnu.org/) - a backup tool based on rsync which supports incremental / versioning. (Linux or Windows through Cygwin)
 * Advantages: Transfers files as-is, with versions also being stored as plain files - not locked into proprietary backup archive blobs in the event of disk corruption/etc.
 * Disadvantages: Does not track moved/renamed files, so those are retransmitted as new data. Does not support encryption. The backup destination must be another server running rdiff-backup.
* [rsnapshot](http://rsnapshot.org/) - a script facilitating a "snapshotting"-style backup using regular rsyncs and hardlinks in order to accomplish a grandfather-father-son backup scheme. This is a script implementing the system nicely outlined by [this post](http://www.mikerubel.org/computers/rsync_snapshots/). Other scripts exist, or this can be done by hand with a little shell experience.
 * Advantages: Provides a system somewhat like ZFS snapshots, but unlike ZFS Send/Receive, the source and destination systems don't need to be running ZFS. Everything is just a file on disk, which keeps the system simple.
 * Disadvantages: No awareness exists of "moves", so renamed or relocated folders containing large amounts of data are treated as "new data" and retransmitted - this could be a big problem if you are wanting to rename "TONS OF BLU-RAYS" to "MOVIES" for instance...potentially leading to huge amounts of data being reuploaded as if it was new.
* [borgmatic](https://torsion.org/borgmatic/) - Simple, configuration-driven backup software for servers and workstations.
Built atop Borg, with additional features like a declarative configuration file, custom preparation/cleanup hooks, database dumping, monitoring integration, etc.
* [Duplicity](http://duplicity.nongnu.org/) - a backup tool based on rsync which supports incremental / versioning. Stores files in encrypted tar files. Supports cloud destinations, though [safety](https://www.reddit.com/r/DataHoarder/comments/5ktcet/duplicity_questions_to_refine_wiki_entry/) to an unmanaged (cloud/etc) destination is uncertain.
* [bup](https://bup.github.io/) - Very efficient backup system based on the git packfile format, providing fast incremental saves and global deduplication (among and within files, including virtual machine images).




## Sync/Cloning Software

* [rsync](https://download.samba.org/pub/rsync/rsync.html) - a popular tool for copying files with various options and features. Does not support incremental / versioning - only syncing. (Linux, OSX, Windows through MSYS)

* Robocopy - Not as advanced as rsync in many respects, but a potentially useful tool for doing syncs across a LAN between two servers that should be mentioned. Unlike rsync, it natively supports multithreading (/MT) which can dramatically speed up file syncs over a LAN and can be a great choice for a tool to synchronize a dataset to a new server before transporting offsite, etc. (Windows only)

* [rclone](http://rclone.org) - "rsync for cloud storage". Supports various cloud providers (including Google Drive, Amazon Cloud Drive, Backblaze, etc.) and comes with some handy extra features. A very popular choice to back up to cloud storage. Note that while rclone did not support incremental changes and versioning for a time, it now does so (for most remotes) with --backup-dir and --suffix. (Linux, Windows, OSX, many more)

* [Syncback](https://www.2brightsparks.com) - A useful tool for mirroring or backing up a hard drive or network share to another destination (such as backing up hard drive to google drive). there are lots of features, but is GUI based, and the simplest to use, which can be useful for beginners alike. However, the free version can`t do cloud backups (but can sync to a network shared folder). (Windows only)

* [Goodsync](https://www.goodsync.com) - Similar to Syncback in that Goodsync is for copying files from 1 place such as network share, hard drive or cloud storage to another place. the tool can detect what files have been renamed and can rename, renamed files at the destination. It can also move, moved files at the destination and can create a recycle bin where deleted files are deleted after 30 days (useful for cloud storage providers like google drive where files stay in the trash until manually emptied). (windows, Mac and Linux including NAS and docker)

* ntfsclone - creates images of NTFS file systems, interesting for backing up Windows machines (Linux, *nix)

* [FreeFileSync](https://freefilesync.org/) - an open source folder comparison and synchronization software that creates and manages backup copies of all your important files. Instead of copying every file every time, FreeFileSync determines the differences between a source and a target folder and transfers only the minimum amount of data needed. FreeFileSync is Open Source software, available for Windows, macOS, and Linux. [Guide on how to set it up can be found here](https://www.youtube.com/watch?v=811ujCTbUAQ&feature=emb_title)

* [WinSCP](https://winscp.net/) - a free SCP/SFTP/FTP client, which supports [local/remote directory synchronization](https://winscp.net/eng/docs/scriptcommand_synchronize). Because it has native support for the S3 API, it can be used to easily interface with cloud storage providers such as Amazon S3, Wasabi, and Backblaze B2.

There are many other backup solutions (please feel free to add them). This list focuses on solutions which are of potential interest to datahoarders only. That generally excludes some enterprise-focused software such as Veeam that, while excellent, is not generally the best solution for people with huge volumes of data seeking a backup solution outside of the corporate datacenter. There are many other Proprietary/Shareware backup programs which *might* be of interest to this community (such as those supporting cloud destinations), but which simply have little community word-of-mouth among those backing up many TBs of data, and there is the potential of concern with regard to proprietary/unknown backup data file formats, etc. When weeks or months are spent replicating huge datasets off-site, taking chances on backup software is a big problem since starting a backup over is a big project.

See also

* https://en.wikipedia.org/wiki/List_of_backup_software

## Storage Providers

* [Backblaze Online Backup](https://www.backblaze.com/cloud-backup.html) & [B2](https://www.backblaze.com/b2/cloud-storage.html)
 * [Backblaze Online Backup](https://www.backblaze.com/cloud-backup.html): For PC and Mac computers, provides unlimited backup for $9 USD/Month with discounts if you do 1 or 2 year subscriptions. Backs up all data attached to the computer, including external USB drives (but not network drives). They now include one year file version history as standard.

 * [Backblaze B2](https://www.backblaze.com/b2/cloud-storage.html): Generic cloud storage. Pricing is pay-as-you-go, at $0.005 USD GB/month ($5 USD TB/month), with $0.01 USD per GB data egress fee (fee to download your data from the cloud). You can access your files using [B2-compatible client software](https://www.backblaze.com/b2/integrations.html), or through B2's web GUI. They offer 10 gigabytes of storage for free.

* [Wasabi](https://wasabi.com)
 * Wasabi's cloud storage is similar to Amazon S3, offering a high durability guarantee, while using the S3 API. You can access your files using [S3-compatible client software](https://wasabi.com/help/downloads/), or through Wasabi's web GUI. Pricing is pay-as-you-go, at $5.99 USD TB/month, with no data egress charges (you don't pay a fee to download your data from the cloud). They offer a 1 TB 30-day free trial.

* [Google Drive](https://workspace.google.com/pricing.html)
 * It is **NO LONGER** possible to get [unlimited storage for Google Drive at very cheap prices](https://workspace.google.com/pricing.html). You can buy a domain, and link it with Google Enterprise. While it may show that there's only 5TB for $18 a user (and further plans show you have to contact them), once you sign up you will see there's a [Payment portal with Google Workspace Enterprise standard with Unlimited Storage as an option](https://imgur.com/a/HLkd84S) for [$20 a month for a single user](https://i.imgur.com/adrvgxm.png). Google Drive's main downside is that it has an upload limit of 750GB/day. Other minor downside is you can only download 10TB/day. This makes it the most practical option for most datahoarders.

* [Amazon Drive](https://www.amazon.com/photos/storage) & [Amazon S3](https://aws.amazon.com/s3)
 * [Amazon Drive](https://www.amazon.com/photos/storage): Intended for home users who want to store photos and basic files in the cloud. They offer various plans, including unlimited full-resolution photo storage for Prime Members, as well as a pay-as-you-go plan at $6.99 USD TB/month.
 * [Amazon S3](https://aws.amazon.com/s3): Generic cloud storage. You can access your files using S3-compatible client software, or through the [AWS web GUI](https://aws.amazon.com/console/). There are several [pricing tiers](https://aws.amazon.com/s3/pricing/), based on how frequently you need to access your data. On the high end, S3 Standard costs $0.023 per GB/month ($23.55 per TB/month). For long-term storage they offer lower-cost tiers, such as S3 Glacier Deep Archive, which costs $0.00099 per GB/month ($1 per TB/month), making it an affordable option for long-term backups.