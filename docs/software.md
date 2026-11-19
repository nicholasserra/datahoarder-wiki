# Software

As important as the drives that you put data on and the hardware you control them with, is the software you read, write, and organise your data with.  This includes operating systems, software raid controllers, backup software, file organisational software, encoding and playback software, and anything else you use to become the Smaug of bits.

**This will start as one page and expand as we add more to it.**

## Popular Operating Systems
 * [Windows Desktop](https://www.microsoft.com/en-gb/software-download/windows10)
 * [Windows Server](https://www.microsoft.com/en-gb/cloud-platform/windows-server)
 * [Apple OSX](https://www.apple.com/uk/macos/how-to-upgrade)
 * [Linux](https://www.kernel.org)
 * BSD ([FreeBSD](https://www.freebsd.org) - [OpenBSD](https://www.openbsd.org/) - [DragonFlyBSD](http://www.dragonflybsd.org/) - [NetBSD](http://netbsd.org/) ...)
 * [Illumos](https://wiki.illumos.org/display/illumos/illumos+Home) (was [OpenSolaris](https://en.wikipedia.org/wiki/OpenSolaris))
 * [Plan9](https://9p.io/plan9)

See [Distrowatch](https://distrowatch.com) to keep track of the latest open source operating systems and Linux and BSD based distributions.


## Popular NAS, SAN, Operating/Embedded Systems, Appliances & Hypervisors
* [NAS4Free](https://www.nas4free.org/) (Free) - Based on [FreeBSD](https://www.freebsd.org), forked from [original FreeNAS code](https://github.com/freenas/freenas)
* [FreeNAS](http://www.freenas.org/) (Free) - Rewrite of the [original FreeNAS code](https://github.com/freenas/freenas)
* [NexentaStore](https://nexenta.com/products/nexentastor) (Free)
* [Open Media Vault](https://www.openmediavault.org/) (Free)
* [Openfiler](http://www.openfiler.com/) (Free)
* [Rockstor](http://rockstor.com/) (Free)
* [UnRaid](https://unraid.net) (Trial-ware) - A storage, virtualization and docker based hypervisor than runs of a USB stick and use a variety of hardware.
* [QuantaStor](https://www.osnexus.com/) (Free)
* [Zetavault](http://www.zeta.systems) (Trial-ware)
* [ESOS](http://www.esos-project.com/) (Free)
* [XPEnology](https://web.archive.org/web/20190316133536/http://xpenology.me/downloads/) (Free) - Allows Synology's DSM OS to run on nearly any hardware.
* [Proxmox](https://www.proxmox.com/en) (Free) - A storage, virtualisation and docker based hypervisor.


## File Systems
 * NTFS (Windows, Linux, OSX)
 * ReFS (Windows)
 * Exfat (Windows, Linux, OSX)
 * ReiserFS (Linux)
 * [Ext4](https://ext4.wiki.kernel.org/index.php/Main_Page) (Linux)
 * [btrfs](https://btrfs.wiki.kernel.org/index.php/Main_Page) (Linux)
 * [Venti](https://en.wikipedia.org/wiki/Venti) (Plan9, ports to other operating systems)
 * [HAMMER](http://www.dragonflybsd.org/hammer/) (DragonFlyBSD)
 * ZFS (see below) (Linux, FreeBSD, Illumos, MacOS)

See this [article](https://www.howtogeek.com/235596/whats-the-difference-between-fat32-exfat-and-ntfs) which explains differences between FAT32, exFAT, and NTFS.

## Volume management

 * [LVM2](https://www.sourceware.org/lvm2/) - A popular and readily available volume manager for GNU/Linux, can be used in conjunction with most RAID/storage solutions.
 * [mhddfs](https://romanrm.net/mhddfs) - Join several filesystems together to form a single larger one on Linux.
 * [mergerfs](https://github.com/trapexit/mergerfs) - A union filesystem geared towards simplifying storage and management of files across numerous commodity storage devices. It is similar to mhddfs.
 * [maidfs](https://gitlab.com/Cobra_Fast/maidfs) - Works similarly as mhddfs but offers more features and control.
 * [Dynamic Disks](https://msdn.microsoft.com/en-us/library/dd163552.aspx) - The default volume management for Windows.
 * ZFS (see below)

## ZFS

**[Wiki ZFS Mainpage](/docs/zfs.md)** *need to reconcile at some point*

A combination file system and logical volume manager.

It is typically used with several hard drives to provide a storage pool that has tolerance to drive failure. The features of ZFS include protection against data corruption, support for high storage capacities, data compression, snapshots, continuous integrity checking, and automatic repair ("scrubs"). 

Available through:

* [OpenZFS](http://www.open-zfs.org/wiki/Main_Page) for [FreeBSD](https://www.freebsd.org) and [Illumos](https://www.illumos.org).
* [ZFS on Linux](http://zfsonlinux.org) for Linux, not native due to licencing issue.

[ZFS info and Guides](/docs/zfs.md)

[ZFS, Hardware RAID, and you](/docs/raidvszfs.md)

https://calomel.org/zfs_raid_speed_capacity.html

## Software RAID

**[Raid vs. ZFS, SATA vs. SAS](/docs/raidvszfs.md)**

**[FreeNAS](http://www.freenas.org)** - A [FOSS](https://en.wikipedia.org/wiki/Free_and_open-source_software) operating system based on [FreeBSD](https://www.freebsd.org) used to turn a computer into a [network-attached storage server](https://en.wikipedia.org/wiki/Network-attached_storage).

* Although it does support another file system (UFS), the main file system it supports and encourages users to use is ZFS. FreeNAS features a web-GUI that allows for setup and administration, as nearly all operations can be done in the GUI (there shell access available for those that want it). FreeNAS supports many networking protocols and user authentication schemes. It also supports plugins/"jails" that allows certain third-party software to run, like media streaming/management or backup software. It scales easily from home-sized environments to enterprise deployments. 

* The use of ZFS combined with easily automated integrity checks (scrubs), disk checks (SMART self tests), reporting (emails about problems), and backup, if configured correctly, makes it one of the most reliable ways for home users to store data. 

* Due to the support for many enterprise features, as well as a GUI arguably not optimized for novices, it can require some reading/research in order to setup and administer correctly. It also may not run the best on old or cheap hardware; using UFS instead of ZFS allows use on worse hardware, at the expense of many data reliability features.

**[FlexRAID](http://www.flexraid.com)**

**[DrivePool](https://stablebit.com/DrivePool)** - can use different sized NTFS drives, arbitrary duplication levels at the pool or folder level, files are stored on underlying NTFS disks as normal files, drives can be added one at a time, integrates with accessory [Scanner](https://stablebit.com/Scanner) for disk evacuation based on SMART status changes or block readability issues, software supports balancing and SSD "feeders". No built-in support for parity, but often used in conjunction with [SnapRAID](http://snapraid.sourceforge.net).

**[SnapRAID](http://snapraid.sourceforge.net)** - can use different sized drives, parity updated manually, and you can take single drives out of the array and read the data on them. Works well with mhddfs.

**[UnRaid](http://lime-technology.com/registration-keys/)** - has dedicated parity drive and are able to run disks of different sizes, is very cheap to set up for compatibility.  

* It's a Slackware Linux based server operating system that boots from a USB flash drive

* You dedicate one or two drives as the parity drive(s) and it needs to be equal to or the largest drive in your array. The rest of the drives can be data disks of any size up to the parity drive's size, each adding to the array's capacity. Additionally, unRAID supports a cache drive feature.
With the Pro license, the maximum number of drives is 54 - 2 parity, 24 cache, 28 data drives.

* If a drive fails, its content can be rebuilt from the parity drive and the remaining drives in the array. If two drives fail, you only lose the data on those two drives, rather than the entire array. To expand the array, you can simply add another data drive, and once formatted, its total will be added to the array's capacity.

**[Storage Spaces](https://social.technet.microsoft.com/wiki/contents/articles/15200.storage-spaces-designing-for-performance.aspx)** - Storage Spaces, and Storage Spaces Direct, is a storage virtualisation technology from Microsoft. Physical disks of varying capacities can be allocated to the Storage Pool, thereafter Storage Spaces can be created with a raid strategy of mirroring and parity, or a simple volume.

Storage Spaces Direct takes the same concept above and extrapolates it to the server level, whereas Storage Pools on multiple servers can be combined and managed from a central location.  This combined asset is seen as one seamless unit. With this strategy, you can expect increased I/O, larger scale failover and performance strategies.

While Storage Spaces can provide create flexibility, scalability, and ease of use, it can also be extremely rigid. Many of the features that make Storage Spaces great must be planned and executed at the time of the Storage Spaces' creation, and cannot be changed without destroying the Space. Further, other software raid solutions are a definitive stand-alone product, with support forums and ownership feedback.  Storage Spaces is a mere facet of the Windows operating system. Definitive answers and community support can be scarce depending on the subject.

* Pools limited to 4096 TB
* Unlimited number of Pools
* Unlimited Storage Spaces
* Ability to mix disk capacities
* Powershell integration
* Thin or Fixed provisioning
* Windows 8, 8.1, 10, Windows Server 2012 & 2016
* ReFS and NTFS file systems
* *ReFS file system functionality was removed with Window's Fall Creators Update (2017). The ReFS file system has been reserved for "Windows 10 Pro for Workstations" and up. It is strongly recommended, if you are using Storage Spaces, to also utilize ReFS.*

**[Linux RAID/mdadm](https://raid.wiki.kernel.org/index.php/Linux_Raid)** - default software RAID implementation for the Linux kernel, it's readily available, quite stable, and relatively easy to set up and maintain.

**[Dynamic Disks](https://msdn.microsoft.com/en-us/library/dd163552.aspx)** - the default volume management for Windows, also provides some RAID capabilities.
  
  
***

## Download Managers

Torrent software

 * [Qbittorrent](https://www.qbittorrent.org) (Windows, OSX, free) - A lightweight, open source and simple to use torrent program, with no bundled software.

 * [Transmission](https://transmissionbt.com) (Windows, Linux, OSX, free) - A Simple, open source torrent program with no bundled software, and is pre installed on some Linux distributions.

 * [Flud - Torrent Downloader](https://play.google.com/store/apps/details?id=com.delphicoder.flud&hl=en_gb) (Android, free with ads, ad free version available) - A torrent client for android phones.
 
Remote download software & download managers

 * [megatools](https://github.com/megous/megatools) (Windows, Linux, free) - A open source program for downloading and uploading from/to mega.nz. Available through some distros package managers.

 * [JDownloader](https://jdownloader.org/home/index) (Windows, Linux, free) - A Java based, open source program for downloading from a variety of [file hosting services](https://en.wikipedia.org/wiki/File_hosting_service).

 * [Internet Download Manager (Otherwise known as IDM)](http://www.internetdownloadmanager.com) (Windows, trialware) - An app for direct downloading for files from the internet.

 * [Advanced Download Manager (Otherwise known as ADM)](https://play.google.com/store/apps/details?id=com.dv.adm&hl=en_Gb) (Android, free with ads, ad free version available) - An app for direct downloading of files from a web browser to a android phone.

 * [Wget](https://www.gnu.org/software/wget) (Windows, Linux, OSX, free) - An open source Command Line Interface tool for downloading files via HTTP, HTTPS, FTP and FTPS. There is also a GUI based version known as [WinWGet](https://winwget.sourceforge.net).

Browser Add-Ons
   
 * [DownThemAll!](https://www.downthemall.org) (Firefox and chrome based browsers) - An add-on for bulk downloading parts of a website.

 * [Base64 Decoder](https://addons.mozilla.org/en-GB/firefox/addon/base64-decoder) (Firefox based browsers) - A browser add-on to decode base64 encoded text with just a right click.

 * [MyJDownloader](https://my.jdownloader.org/apps/?ref=myjd_web) (Firefox and chrome based browsers) - A browser add-on to remotely interact with jdownloader.

Video site downloaders

 * [Youtube-dl](http://rg3.github.io/youtube-dl) (Windows, Linux, OSX, free) - A command-line, open source video download suite, written in Python.  The full source is available to compile from the website, and there is also a pre-compiled program for Windows.  Youtube-dl allows massive customisation of downloads, including downloading a single video, full playlist, all videos from a given user, and many other options. There is also a GUI based version known as [youtube-dl-gui](https://mrs0m30n3.github.io/youtube-dl-gui/). Another GUI program for YT-DL is [gropple](https://github.com/tardisx/gropple)

 * [yt-dlp](https://github.com/yt-dlp/yt-dlp) (Windows, Linux, OSX, free) is a [youtube-dl](https://github.com/ytdl-org/youtube-dl) fork based on the now inactive [youtube-dlc](https://github.com/blackjack4494/yt-dlc). The main focus of this project is adding [new features](https://github.com/yt-dlp/yt-dlp#new-features) and patches while also keeping up to date with the original project.

 * [4K Download](https://www.4kdownload.com) (Windows, Linux, OSX, free to use, but does have paid features) - A GUI based tool for downloading YouTube videos and playlists. This is much easier than Youtube-dl, if want to just download YouTube videos and playlists. Can also create a m3u playlist file if needed.

Automated downloading tools

 * [Sick Beard](http://sickbeard.com) (Windows, Linux, free) - A open source PVR software package that runs in the background and is controlled through a browser window, downloading new TV episodes as they're released automatically. ***Development of Sick Beard has ceased in 2013***

  * There are several forks of Sickbeard available with additional features.  Some are available on the [Sick Beard Github](https://github.com/midgetspy/Sick-Beard) **Note need to talk about other forks**

  * [SickRage](https://github.com/SickRage/SickRage) (Windows, Linux, free) - A fork of Sick Beard with active developers and many more features

 * [Sonarr](https://sonarr.tv) (Windows, Linux, free) - An open source tool pvr to download TV shows using torrents, it can be set in a variety of ways such as only download missing episodes or better quality shows you already own.
 
 * [Radarr](https://radarr.video) (Windows, Linux, OSX, free) - An open source tool to download films using your torrent program. Radarr can be set to download better quality films than what you already have.

 * [Lidarr](https://lidarr.audio) (Windows, Linux, OSX, free) - A open source [fork](https://en.wikipedia.org/wiki/Fork_(software_development)) of Sonarr, but instead for downloading music using your torrent program.

## Organisational / Playback
* [Bulk Rename Utility](http://www.bulkrenameutility.co.uk) (Windows, free) - Massively flexible and powerful file renaming utility.  Cluttered interface but has fairly easy options for character replacement; string trim, append, add, and remove; auto numbering, and many other options. Supports regex strings for complex matching. Tiny but powerful.

* [FileBot](http://www.filebot.net) (Windows, OSX, Linux, trial-ware, but older versions can be used for free) - Billed as 'The ultimate TV renamer' Filebot uses regex-like filename replacing coupled with powerful searches through several television and movie databases to identify TV episodes and Movies and re-name them correctly. Also included is basic archive handling, the ability to manually search the TV databases for series and episodes, subtitle searches and checksum management. **Use caution when installing:** FileBot bundles adware. Use custom installation and watch for auto-selected install checkboxes.

* [MusicBrainz Picard](https://musicbrainz.org/doc/MusicBrainz_Picard) (Windows, OSX, Linux, free) - A open source program that allows intelligent sorting and renaming of music files in an album-oriented approach.  Picard can search and sort by CD lookup, disc ID, or via an acoustic signature match against the extensive MusicBrainz database to identify and sort files.  Though the album matching isn't perfect (sometimes sorting a song that appears under multiple albums by the incorrect album title) it's easy to select and re-match files with multiple hits.

* [Mp3tag](https://www.mp3tag.de/en) (Windows, OSX, free) - A program for tagging music with metadata from services like Discogs, and can rename music files based on the metadata, as well as create playlist files.

* [Beets](http://beets.radbox.org/) (Windows, OSX, Linux, free) - An open source, command line organiser for music collections. It boasts a powerful auto-tagger that can pull metadata from MusicBrainz, Discogs, Beatport or other sources, the ability to do automatic renaming on import and transcoding files with custom ffmpeg commands. It also has a powerful plug-in system that enables everything from finding duplicate or missing tracks, to emulating a MPD server.

* [Plex](http://plex.tv) (Windows, OSX, Linux, free to use but does have paid features) - Install server on your platform of choice, streams to plex clients on an impressive number of platforms, most free; also implements DLNA streaming support and video streaming/organisation/playback available via browser. Optional paid version has even more features.

* [Kodi/XBMC](http://kodi.tv/) (Windows, OSX, Linux, free) - An open source media centre and home theatre solution.

## Other useful software ##
* [WinDirStat](http://windirstat.info/) (Windows, free) - A GUI based tool for scanning a folder, drive, or collection of drives and provide a graphical representation of which files and folders are taking up space.  This is an excellent way for users to manage drives with limited remaining space or to easily estimate the amount of space taken by certain files (ie, 'Anime' folder, music by The Chemical Brothers, complete collection of Black Mirror episodes).

* [WizTree](http://wiztreefree.com/) (Windows, free for personal use) similar to WinDirStat, able to scan NTFS drives using the master file table allowing it to complete in seconds while WinDirStat takes minutes.

* Linux users can use the original implementation, [KdirStat](http://kdirstat.sourceforge.net). If you use a distro with GNOME support can also use [Baobab](https://help.ubuntu.com/community/Baobab), which comes pre-installed on Ubuntu.

* OSX users can utilize the very similar [Disk Inventory X](http://www.derlien.com/) or [GrandPerspective](http://grandperspectiv.sourceforge.net)

* [ncdu](https://dev.yorhel.nl/ncdu) is a textual ncurses based data manager for Linux (and other unixoids) working similarly to WinDirStat or KdirStat. Available through your distros package manager.

* SpaceSniffer

## Recording / Ripping / Encoding

* [ffmpeg](https://ffmpeg.org) (Windows, OSX, Linux, free) - Most popular and most feature rich and complete solution for media encoding/transcoding. Available for most operating systems.

* [HandBrake](https://handbrake.fr) (Windows, OSX, Linux, free) - A convenient tool for converting video from nearly any format to a selection of modern, widely supported codecs. Support includes Windows, Mac OS and Linux.

* [VidCoder](http://vidcoder.net) (Windows, free) - A tool that uses the HandBrake backend to make encoding videos easier. It takes all the features and raw power of Handbrake, and delivers them to end users via a more streamlined and user-friendly interface, making the program more accessible to all. Adds support such as being able to pause encodes in progress.

* [MakeMKV](http://www.makemkv.com) (Windows, OSX, Linux, free to use, but does have paid features) - A one-click solution to rip dvds and blue-ray discs into free and patents-unencumbered mkv format that can be played everywhere. MakeMKV is a format converter, otherwise called a [transcoder](https://en.wikipedia.org/wiki/Transcoding). It converts the video clips from proprietary (and usually encrypted) discs into a set of MKV files, preserving most information. But not changing the files in any way, or compressing the video files. So you get 1 to 1 remux copies of your discs.

* [DeUHD](https://deuhd.ru) (Windows, paid) - A tool for ripping UHD 4K Discs to watch on your computer.

* [Exact Audio Copy (EAC)](http://exactaudiocopy.de/) - Exact Audio Copy is a so called audio grabber for audio CDs using standard CD and DVD-ROM drives.

## [Backup](/docs/backups.md#free-backup-software--techniques-appropriate-for-datahoarders)

*=> See [Backups#Free_Backup_Software](/docs/backups.md#free-backup-software--techniques-appropriate-for-datahoarders)*

## Website Archiving Tools

**GUI/web UI:**

 - [Pocket](https://getpocket.com) (Web based, free to use, but does have paid features) - A website where you save articles for offline reading.
 - [Wallabag](https://wallabag.org) (Linux, free) A open source self hosted tool like pocket where you can save articles you read locally or on your phone.
 - [Pinboard](https://pinboard.in) (Web based, paid) - A website for storing bookmarks.
 - [ArchiveBox](https://archivebox.io) (Linux, free) - A self-hosted internet archive that saves content in multiple formats using a headless, authenticated browser.
 - [Memex by Worldbrain.io](https://worldbrain.io) (Firefox and Chromium, free to use but does have paid features) - A browser extension that saves all your history and does full-text search.
 - [Hypothes.is](https://web.hypothes.is) (Chromium, free) - A website, pdf and e-book annotation tool that also archives content.
 - [Perkeep](https://perkeep.org) (Windows, OSX, Linux) (free) - An open source program that's for modelling, storing, searching, sharing and synchronising data in the post-PC era.
 - [Fetching.io](http://fetching.io) (OSX, trial-ware) - A personal search engine & archiver that lets you search through all archived websites that you've bookmarked.
 - [Shaarchiver](https://github.com/nodiscc/shaarchiver) (free) - An open source program that archives Firefox, Shaarli, or Delicious bookmarks and all linked media and generates a markdown/HTML index file.
 - [Webrecorder.io](https://webrecorder.io) (free, optional donation to get extras) - Save full browsing sessions and archive all the content.
 - [WARCreate](http://warcreate.com) (Chromium, free) - An extension to make a WARC from any webpage, for the wayback machine.
 - [SiteSucker](http://ricks-apps.com/osx/sitesucker/index.html) (OSX, paid) - A nice mac app for web scraping and site downloading.
 - DeepVacum: similar to sitesucker
 - [HTTrack](https://www.httrack.com) (Windows, Linux, OSX, free) - A website downloading tool and offline browser utility.
 - [WAIL](http://matkelly.com/wail)

**Command line:**

 - httrack
 - [warc python library](https://github.com/internetarchive/warc)
 - [heritrix3](https://github.com/internetarchive/heritrix3)
 - [ArchiveBox](https://github.com/pirate/ArchiveBox/) (cli based but it produces an html index UI)
 - [WarcMITMProxy](https://github.com/odie5533/WarcMITMProxy)
 - [warcreate](http://warcreate.com/)
 - Apache Nutch
 - StormCrawler
 - http://www.proxy-offline-browser.com/
 - [pywb](https://github.com/webrecorder/pywb)
 - [warcprox](https://github.com/internetarchive/warcprox)
 - [The WARC Ecosystem](https://www.archiveteam.org/index.php?title=The_WARC_Ecosystem)

Much more here:

 - **[The Awesome Web Archiving List](https://github.com/iipc/awesome-web-archiving) (IIPC)**  
 - **[Wiki of Web Archiving Tools](http://coptr.digipres.org/Category:Tools) (COPTR)**  
 - **[ArchviveBox Community Wiki List](https://github.com/pirate/ArchiveBox/wiki/Web-Archiving-Community)**
 - [ArchiveTeam's List of Software](https://www.archiveteam.org/index.php?title=Software) (ArchiveTeam.org)  
 - [List of Web Archiving Initiatives](https://en.wikipedia.org/wiki/List_of_Web_archiving_initiatives) (Wikipedia.org)  
 - [Directory of Archiving Organisations](https://www2.archivists.org/assoc-orgs) (American Society of Archivists)
