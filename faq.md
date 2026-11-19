# Datahoarder FAQ
This page will feature questions and answers for topics that are asked almost daily on the subreddit.

### Q: What are you hoarding?
This is asked often, so we made a megathread:
https://www.reddit.com/r/DataHoarder/comments/ne6j3s/the_ultimate_what_do_you_hoard_thread_wiki_link/


### Q: What should I start hoarding?
So you've found yourself with some hard drives and stumbled upon our subreddit. Nice. But we wouldn't suggest you go filling your drives just to have something to do. Hoard stuff you want and need. Most people here are hoarding data they create themselves, or data they've downloaded from the internet that they can't live without. Download the stuff you use everyday, because it might be gone soon.

### Q: Should I get a NAS? What about backups? Where do I start?
Check out [Nick's 6 minute lightning talk](https://youtu.be/EADCoq6QygM?t=1911) on the levels of datahoarding gear. This takes you through simple setups to large servers quickly.

Otherwise, the answer is to usually start small by adding an external HDD as a backup to whatever your current system is.

If you want to get into a NAS, a common beginner setup for under 20TB of data is a Synology or Ugreen 2 bay NAS in mirror mode. It will require two large hard drives to be set as a mirror. This gives you redundancy. Turn on cloud backups in the NAS software to give you an offsite backup.

This covers 99% of people's use cases.

### Q: How do I download a video from YouTube? (or insert other video provider here)
A: The answer is almost always to use [yt-dlp](https://github.com/yt-dlp/yt-dlp). Make sure you're on the latest version.

### Q: How do I transfer files from here to there?
A: There are multiple programs that are frequently recommended for file transfers/backups:
- [rsync](https://download.samba.org/pub/rsync/rsync.1) for command line transfers on linux style systems
- [rclone](https://rclone.org/) for backing up to cloud providers
- [robocopy](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy) for command line transfers on windows
- [FreeFileSync](https://freefilesync.org/) for GUI transfers on Windows

### Q: What external hard drive should I buy?
Folks in this community have long been partial to Western Digital Easystore or Elements magnetic external hard drives. Many of us even pull the drives out of the cases to use in a NAS. Check prices at [shucks.top](https://shucks.top/).

### Q: How do I verify my files are okay? How does integrity/checksums work? What about bitrot.
Bitrot and data integrity are common questions. Whether bitrot is a real risk is a debated topic, but many datahoarders use several tactics just in case:
- Use ECC RAM in your servers to avoid bit flips. It's more expensive and less motherboards support it, but many find it worth it.
- Manage your own checksums of files. This can be done manually by computing hashes of your files and then checking this hash later. For example, with HashCheck program in windows. 
- Use an OS/filesystem that does this for you: TrueNAS ships with ZFS file system, which handles data integrity, data scrubs, and data healing for you.
- Run a plugin or application of some kind to automatically check: For example, on Unraid, you can install file integrity plugins that will compute and regularly check hashes of files and warn you if there's an error.
- Use verification when copying files

### Q: How do I copy/scrape/clone a website?
This answer gets trickier as websites become more complex via XHR requests, client side rendering, complex JS frameworks, etc.

The usual answer is to use popular utilities like wget or httrack.

- wget: Powerful command line downloader that supports recursive scraping and many options.
- httrack: GUI application for scraping websites

Unfortunately these cannot handle all cases and many datahoarders end up writing their own scripts and tools to grab what they need.


