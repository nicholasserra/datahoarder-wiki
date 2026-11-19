# Hardware

## Cases 

Peek [this thread](https://www.reddit.com/r/DataHoarder/comments/1f2aw6d/list_of_computer_cases_with_lots_of_hard_drive/) for updates on common cases for mass hard drive storage:


### Beginner

NZXT Source 210

* Equals a small 12-bay case 
* Under $65 
* Ample space for nice 120mm fans.

Fractal Design Node 304

* Supports mini ITX motherboards
* supports full ATX power supplies
* can have up-to 6 3.5" hard drives in normal cages (no hot swap). 
* Something to note is that it might have problems cooling a high end processor plus six drives.

Fractal Design Define Mini

* The case certainly isn't hard to use. Depends if 6 drive sleds is enough for you.
* Micro-ATX, Mini-ITX
* 6 drive sleds, manually connected sata/power behind each drive, so you have to disconnect those before pulling a sled (hot-swap depends on mobo/RAID card). You can put a 7th and 8th hard drive in using 5.25-to-3.5 adapters, not included.
* I highly recommend buying another 120mm fan so all of the drives get cooling

### Mid Tier

Fractal Design Define R4

* The case certainly isn't hard to use. Depends if 8 drive sleds is enough for you.
* ATX, Micro-ATX, Mini-ITX
* 8 drive sleds, manually connected sata/power behind each drive, so you have to disconnect those before pulling a sled (hot-swap depends on mobo/RAID card). You can put a 9th and 10th hard drive in using 5.25-to-3.5 adapters, not included.
* I highly recommend buying another 140mm fan so all of the drives get cooling

I would personally put the DS380 in the Mid-tier group:
8 Hot-swap bays (which is more part of the server-grade groups, but it's not server-grade, nor big enough to be 'one of the boys' )
Totalling 12 disks (8x 3.5" hot-swap, 4x2.5" fixed), making it a potential 36TB worth of storage (8x4TB (I know, there's bigger, but those are just silly expensive for now) + 4x1TB)
SFF, so easy to fit where-ever you might want it, though this does come as a down-side that it's not rackmount, if you care for that.
Option to sacrifice 1 hot-swap bay for an extended PCI-e slot, if needed (like for when you want to put a bigass GPU in your storage machine).
mini-ITX motherboard

[U-NAS NSC-800 Server Chassis](http://www.u-nas.com/xcart/product.php?productid=17617)

* Mini-ITX
* 8 hot swappable bays for 3.5" and 2 internal 2.5"
* compact size

[Sharkoon T9 Value](http://en.sharkoon.com/product/1678/T9Val#desc)

* ATX
* 9 5.25" bays (can fit 15 3.5" HDDs with 5x3.5"-to-3x5.25" cages/enclosures plus an additional 2.5" drive on the back side)
* compact size (in fact sometimes maybe a tad too compact)

### High End

##### **Supermicro Chassis**

[Supermicro 24 bay Chassis](https://www.supermicro.com/products/chassis/4u/?chs=846)

| Chassis Model   | Backplane Model | Expander | Backplane Connector | >2TB Drives | Bandwidth | Power Supply  | Redundant | In Production |
|-----------------|-----------------|----------|---------------------|-------------|-----------|---------------|-----------|---------------|------------------------------------------------------------------------------------------------------------------------|
| SC846E1-R710B   | BPN-SAS-846EL1  | Single   | (1) SFF-8087        | No          | 3Gbps     | 710w DC       | Yes (2)   | No            |                                                                                                                        |
| SC846E1-R900B   | BPN-SAS-846EL1  | Single   | (1) SFF-8087        | No          | 3Gbps     | 900w          | Yes (2)   | No            |                                                                                                                        |
| SC846E1-R1200B  | BPN-SAS-846EL1  | Single   | (1) SFF-8087        | No          | 3Gbps     | 1200w Gold    | Yes (2)   | No            |                                                                                                                        |
| SC846E2-R900B   | BPN-SAS-846EL2  | Dual     | (2) SFF-8087        | No          | 3Gbps     | 900w          | Yes (2)   | No            | 
| SC846A-R920B    | BPN-SAS-846A    | None     | (6) SFF-8087        | Yes         | 6Gbps     | 920w Platinum | Yes (2)   | No            |                                                                                                                        |
| SC846E16-R1200B | BPN-SAS2-846EL1 | Single   | (1) SFF-8087        | Yes         | 6Gbps     | 1200w Gold    | Yes (2)   | Yes           |                                                                                                                        |
| SC846E26-R1200B | BPN-SAS2-846EL2 | Dual     | (1) SFF-8087        | Yes         | 6Gbps     | 1200w Gold    | Yes (2)   | Yes           | 
| SC846A-R900B    | BPN-SAS-846A    | None     | (6) SFF-8087        | Yes         | 6Gbps     | 900w          | Yes (2)   | Yes           |                                                                                                                        |
| SC846A-R1200B   | BPN-SAS-846A    | None     | (6) SFF-8087        | Yes         | 6Gbps     | 1200w Gold    | Yes (2)   | Yes           |                                                                                                                        |
| SC846TQ-R900B   | BPN-SAS-846TQ   | None     | (24) SAS2/SATAIII   | Yes         | 6Gbps     | 900w          | Yes (2)   | Yes           |                                                                                                                        |
| SC846TQ-R1200B  | BPN-SAS-846TQ   | None     | (24) SAS2/SATAIII   | Yes         | 6Gbps     | 1200w Gold    | Yes (2)   | Yes           |                                                                                                                        |

**A note on the chassis with dual expanders:** Only 1 SFF-8087 connector is required to access all 24 drives. The 2nd SFF-8087 is optional and intended for failover with a secondary HBA.

**A note on the 846E1 and 846E16:** These are the two most commonly found models on eBay. The 846E1 is SAS1 and the 846E16 is SAS2. Often the 846E16 will be listed as 846EL1 which makes the listing look like it's selling the SAS1 version. 846EL1 actually refers to the backplane part number and the sellers often get them mixed up. So pay close attention to the details and ask the seller questions if you are unsure! Shipping these things cost a fortune so you don't want to order the wrong one.


[Norco RPC-4224](http://www.ipcdirect.net/servlet/Detail?no=252)

* Large case for people who want to store a ton of information and need to have a ton of drives

* The case accepts full ATX motherboards

* 4U Rackmount case

* Has 24x hot swap bays. There is the ability to add 1x 3.5 inch or 2x 2.5 inch non-hot swap drives with an addin bracket (part 4224OSbracket)

* The case uses RL-26 sliding rails

* A recommended upgrade is to swap out the 4x 80mm midplane fan bracket with a 3x 120mm midplane fan bracket (part 120mmfanbracket). It allows less loud fans to be put in the case and move more air.

[X-Case 4U cases](http://www.xcase.co.uk/rackmount-cases/4u-rackmount-server-cases.html)

Lian Li PC-D8000

* Holds 20 3.5" drives before you even start using the 5.25" bays

* huge case


### Direct Attached Storage (DAS)

used to just hold drives, no motherboard. This would just be JBOD (Just A Bunch of Disks) in a enclosure without RAID, ZFS, or UnRAID.  
 
[Sans Digital 5 Bay HD Rack](http://www.newegg.com/Product/Product.aspx?Item=N82E16816111045)

[Addonics RAID Tower](http://www.addonics.com/products/rt134sdes6g.php)

* This monstrosity also comes with 4x 5-in-3 drive bays and four eSATA-to-5-SATA port multipliers. Again, no motherboard-- all disk.

[Supermicro 45 bay JBOD](http://www.supermicro.com/products/chassis/4U/847/SC847E16-RJBOD1.cfm)


Roswill 8-Bay External eSATA[1]
 
* barebones external case  

* designed to hold 8 3.5" drives 

* note that most eSATA ports built into motherboards do NOT support port multipliers

Mediasonic H82-SU3S2[2]

* a higher end case 

* supports auto fan speed cooling

### Misc

Silverstone DS380

Lian Li Q25

Mercury S3. In retrospect, it's probably not the best case for a NAS but it is highly customizable (but expensive) with many options for mounting, fans, airflow, etc. It's a pretty small footprint with room for 8+ drives if that's your bag. The biggest draw back is that if you have a drive failure on the bottom, you pretty much have to disassemble the entire thing to replace the drive based on how tight the fit is.

I use the Antec P100[1] for my esxi/freenas box. 7 3.25 bays, and then 2 5.25 bays so you could use a 3 in 2 to get 10 bays total.
It's quiet, has normal Antec build quality and imo it looks nice. Takes mini, micro and standard ATX. Lots of space on the backside for cable routing. I think it normally lists around $100 but there are lots of deals on it usually, right now its $69 with MIR.
2x 120mm fans can go in front. 120mm in rear, 140mm on top or some radiator (not sure about size) if that's your thing.
The Fractal Design Node 804[2] with up to 12 drive bays seems to be positioned squarely at dorks like us. I don't have one so I won't make any comments on it.

#### Hot Swap

[Cooler Master 4-in-3](http://www.newegg.com/Product/Product.aspx?Item=N82E16817993002)

* For people who don't know, hot swap bays are great. They allow the bays to be placed in the 5.25 inch slot and can fit four 3.5 inch drives in 3 5.25 inch slots. This allows you to fit more hard drives in.   

That Cooler Master thing is not actually a hot-swap so I wouldn't list it as that. Hot swap bays are far more expensive, usually $75+ for a 5-in-3 or 4-in-3.
The Cooler Master is just good for any case with 3 5.25" to store and cool 4 3.5" drives and it's so cheap <$25. But you have to remove the whole thing when you want to remove any of the drives located inside it and the drives are wired as normal.

## Hard Drives

### SMR vs CMR

SMR = Shingled Magnetic Recording  
CMR = Conventional Magnetic Recording, (sometimes called PMR / Parallel)

SMR allows for more tracks per platter whilst using larger write heads by overlapping the tracks, this results in a slow write speed for SMR drives.  
It is strongly recommended not to use SMR based drives in RAID / ZFS arrays.

Seagate will tell you what drives are SMR [here](https://www.seagate.com/gb/en/internal-hard-drives/cmr-smr-list/)  
A full list of SMR vs CMR can be found [here](https://nascompares.com/answer/list-of-wd-cmr-and-smr-hard-drives-hdd/)

### Desktop, Eco, Green

While often cheaper, these drives are designed for a more "casual" usage pattern and may or may not cause trouble in RAID or similar setups. They usually run at slower speeds (between 5000 and 6000 RPM) in order to save power and reduce noise and heat. They may however still be suitable for rarely read and rarely written data graves or backup disks.

* WD Blue
* WD Green (discontinued)
* Seagate Desktop HDD
* HGST Deskstar (both "CoolSpin" and 7200 RPM variants)

### NAS

**Short and subjective orientation:**  
WD Red: Very good alrounder, acceptable reliability and performance, quiet, somewhat eco-friendly  
HGST: Very good reliability, good performance, somewhat noisy  
Seagate: More affordable, acceptable reliability and performance  
Toshiba: More affordable, acceptable performance, bad reliability and customer service  

| Manufacturer | Model | Capacity | RPM | Cache | MTBF | Warranty | PCPartPicker Link
|-|-|-|-|-|-|-|-|
| Western Digital | Red WD10EFRX | 1TB | 5400 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/part/western-digital-internal-hard-drive-wd20efrx |
| Western Digital | Red WD20EFRX | 2TB | 5400 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/part/western-digital-internal-hard-drive-wd20efrx |
| Western Digital | Red WD30EFRX | 3TB | 5400 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/part/western-digital-internal-hard-drive-wd30efrx |
| Western Digital | Red WD40EFRX | 4TB | 5400 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/part/western-digital-internal-hard-drive-wd40efrx |
| Western Digital | Red WD50EFRX | 5TB | 5400 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/product/Fxh9TW/western-digital-internal-hard-drive-wd50efrx |
| Western Digital | Red WD60EFRX | 6TB | 5400 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/product/DhsKHx/western-digital-internal-hard-drive-wd60efrx |
| Western Digital | Red WD80EFZX | 8TB | 5400 | 128MB | 1Mh | 3Y | http://pcpartpicker.com/product/4fvZxr/western-digital-internal-hard-drive-wd80efzx |
| Western Digital | Red WD100EFAX | 10TB | 5400 | 256MB | | | |
| Western Digital | Red Pro WD2001FFSX | 2TB | 7200 | 64MB | 1Mh | 5Y | http://pcpartpicker.com/product/3dNp99/western-digital-internal-hard-drive-wd2001ffsx |
| Western Digital | Red Pro WD3001FFSX | 3TB | 7200 | 64MB | 1Mh | 5Y | http://pcpartpicker.com/product/RHV48d/western-digital-internal-hard-drive-wd3001ffsx |
| Western Digital | Red Pro WD4001FFSX | 4TB | 7200 | 64MB | 1Mh | 5Y | http://pcpartpicker.com/product/nj8Zxr/western-digital-internal-hard-drive-wd4001ffsx |
| Western Digital | Red Pro WD5001FFWX | 5TB | 7200 | 128MB | 1Mh | 5Y | http://pcpartpicker.com/product/qQ648d/western-digital-internal-hard-drive-wd5001ffwx |
| Western Digital | Red Pro WD6002FFWX | 6TB | 7200 | 128MB | 1Mh | 5Y | http://pcpartpicker.com/product/bbKhP6/western-digital-internal-hard-drive-wd6002ffwx |
| Western Digital | Red Pro WD8001FFWX | 8TB | 7200 | 128MB | | | |
| Western Digital | Red Pro WD101KFBX | 10TB | 7200 | 256MB | | | |
| HGST | Deskstar NAS 0S03660 | 3TB | 7200 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/product/TP2kcf/hitachi-internal-hard-drive-0s03660 |
| HGST | Deskstar NAS 0S03664 | 4TB | 7200 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/product/QRLypg/hitachi-internal-hard-drive-0s03664 |
| HGST | Deskstar NAS 0S03835 | 5TB | 7200 | 128MB | 1Mh | 3Y | http://pcpartpicker.com/product/zqqbt6/hitachi-internal-hard-drive-0s03835 |
| HGST | Deskstar NAS 0S03839 | 6TB | 7200 | 128MB | 1Mh | 3Y | http://pcpartpicker.com/product/jwrcCJ/hitachi-internal-hard-drive-0s03839 |
| HGST | Deskstar NAS 0S04012 | 8TB | 7200 | 128MB | 1Mh | 3Y | http://pcpartpicker.com/product/rz98TW/hitachi-deskstar-nas-8tb-35-7200rpm-internal-hard-drive-0s04012 |
| HGST | Deskstar NAS 0S04037 | 10TB | 7200 | 256MB | | | |
| Seagate | NAS HDD ST2000VN001 | 2TB | 5400 | 64MB | | | http://pcpartpicker.com/product/ZXL7YJ/seagate-internal-hard-drive-st2000vn001 |
| Seagate | NAS HDD ST4000VN003 | 4TB | 5400 | 64MB | | | http://pcpartpicker.com/product/yHx9TW/seagate-internal-hard-drive-st4000vn003 |
| Seagate | NAS HDD STBD4000100 | 4TB | 5900 | 64MB | | | http://pcpartpicker.com/product/LHBrxr/seagate-internal-hard-drive-stbd4000100 |
| Seagate | NAS HDD ST8000VN0002 | 8TB | 7200 | 256MB | | | http://pcpartpicker.com/product/ZqmxFT/seagate-internal-hard-drive-st8000vn0002 |
| Seagate | IronWolf ST1000VN002 | 1TB | 5900 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/product/2FCrxr/seagate-ironwolf-1tb-35-5900rpm-internal-hard-drive-st1000vn002 |
| Seagate | IronWolf ST2000VN004 | 2TB | 5900 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/product/btkwrH/seagate-ironwolf-2tb-35-5900rpm-internal-hard-drive-st2000vn004 |
| Seagate | IronWolf ST3000VN007 | 3TB | 5900 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/product/WG2rxr/seagate-ironwolf-3tb-35-5900rpm-internal-hard-drive-st3000vn007 |
| Seagate | IronWolf ST4000VN008 | 4TB | 5900 | 64MB | 1Mh | 3Y | http://pcpartpicker.com/product/6MX2FT/seagate-ironwolf-4tb-35-5900rpm-internal-hard-drive-st4000vn008 |
| Seagate | IronWolf ST6000VN0041 | 6TB | 7200 | 128MB | 1Mh | 3Y | http://pcpartpicker.com/product/j4PzK8/seagate-ironwolf-6tb-35-7200rpm-internal-hard-drive-st6000vn0041 |
| Seagate | IronWolf ST8000VN0022 | 8TB | 7200 | 256MB | 1Mh | 3Y | http://pcpartpicker.com/product/zKnG3C/seagate-ironwolf-8tb-35-7200rpm-internal-hard-drive-st8000vn0022 |
| Seagate | IronWolf ST10000NE0004 | 10TB | 7200 | 256MB | 1Mh | 3Y | http://pcpartpicker.com/product/TwDzK8/seagate-ironwolf-pro-10tb-35-7200rpm-internal-hard-drive-st10000ne0004 |
| Seagate | IronWolf Pro ST6000NE0021 | 6TB | 7200 | 256MB | 1.2Mh | 5Y | http://pcpartpicker.com/product/ZxTrxr/seagate-ironwolf-pro-6tb-35-7200rpm-internal-hard-drive-st6000ne0021 |
| Seagate | IronWolf Pro ST8000NE0021 | 8TB | 7200 | 256MB | 1.2Mh | 5Y | http://pcpartpicker.com/product/YcBrxr/seagate-ironwolf-pro-8tb-35-7200rpm-internal-hard-drive-st8000ne0021 |
| Seagate | IronWolf Pro ST10000NE0004 | 10TB | 7200 | 256MB | 1.2Mh | 5Y | http://pcpartpicker.com/product/TwDzK8/seagate-ironwolf-pro-10tb-35-7200rpm-internal-hard-drive-st10000ne0004 |

*Pro* (Red, IronWolf) drives are intended for power users and small enterprises, only included them for completeness.

Seagate IronWolf do not support APM and some reviews complain about excessive head parking and clicking noise. If and how this affects the drives performance and longevity is unknown. However, according to [a Seagate document](http://www.seagate.com/www-content/product-content/ironwolf/en-us/docs/100807039b.pdf) a "power-management mode" may be chosen through "the system setup program", which presumably is the BIOS/UEFI menu or HBA setup of the controller the drive is attached to.

[Western Digital 3TB SE for NAS](https://pcpartpicker.com/part/western-digital-internal-hard-drive-wd3000f9yz)

* Higher end than other drives but has a longer warranty.

### Enterprise

* [WD Re](https://www.wdc.com/products/business-internal-storage/wd-re.html) - general purpose enterprise storage, 7200 RPM, 2 Mh MTBF, 550 TB/Y workload rating, up to 6TB models
* [WD Gold](https://www.wdc.com/products/business-internal-storage/wd-gold.html) - "advanced technology" (e.g. helium filled), 7200 RPM, bigger caches, 2-2.5 Mh MTBF, 550 TB/Y workload rating, up to 12TB models
* [WD Purple](https://www.wdc.com/products/internal-storage/wd-purple-surveillance-hard-drive.html) and [Purple NV](https://www.wdc.com/products/business-internal-storage/wd-purple-nv.html) - "surveillance" sequential read/write optimized, 5400 RPM, 180 TB/Y workload rating, up to 6TB models
* [HGST Ultrastar 7K](https://www.hgst.com/products/hard-drives/ultrastar-7k6000) - general purpose enterprise storage, 7200 RPM, 2 Mh MTBF, up to 6TB models
* [HGST Ultrastar He12, He10, He8](https://www.hgst.com/products/hard-drives/ultrastar-he10) - high capacity helium filled, 7200 RPM, 2.5 Mh MTBF, up to 12TB models
* [HGST Ultrastar C10K, C15K](https://www.hgst.com/products/hard-drives/ultrastar-c15k600) - high performance, 10 or 15 kRPM, 2 Mh MTBF, up to 1.8TB (10k) / 600 GB (15k) models
* [Seagate Enterprise NAS](http://www.seagate.com/de/de/enterprise-storage/hard-disk-drives/enterprise-nas-hdd/) - general purpose enterprise storage, 7200 RPM, 300 TB/Y workload rating, up to 8TB models
* [Seagate Enterprise Capacity Helium](http://www.seagate.com/de/de/enterprise-storage/hard-disk-drives/enterprise-capacity-3-5-hdd-10tb/) - high capacity helium filled, 550 TB/Y workload rating, 10TB only
* [Seagate Enterprise Capacity](http://www.seagate.com/de/de/enterprise-storage/hard-disk-drives/enterprise-capacity-3-5-hdd/) - high capacity, 550 TB/Y workload rating, up to 12TB
* [Seagate Archive HDD](http://www.seagate.com/de/de/enterprise-storage/hard-disk-drives/archive-hdd/) - high capacity, SMR, 180 TB/Y workload rating, up to 8TB, affordable
* [Seagate Kinetic HDD](http://www.seagate.com/de/de/enterprise-storage/hard-disk-drives/kinetic-hdd/) - SGMII Ethernet connector instead of SAS/SATA, 4TB only
* [Seagate Performance 10K HDD](http://www.seagate.com/de/de/enterprise-storage/hard-disk-drives/enterprise-performance-10K-hdd/) - high performance HDD, 10 kRPM, up to 1.8TB models
* [Seagate Performance 15K HDD](http://www.seagate.com/de/de/enterprise-storage/hard-disk-drives/enterprise-performance-15k-hdd/) - high performance HDD, 15 kRPM, up to 900GB models

### Recertified and Refurbished

Recertified drives are used drives that have been tested and updated (as far as possible) by the manufacturer. SMART history is usually reset. They are re-sold at a discount with new warranty.

Similarly, refurbished 2nd hand drives have been tested by a retailer who found them as good enough for sale. However, a retailer usually does not have access to all testing tools and procedures the manufacturer has, so the quality of a refurbished drive is somewhat uncertain and debatable.

### Drives with Ok Reviews, Use At Your Own Risk

[Seagate ST3000DM001](http://pcpartpicker.com/part/seagate-internal-hard-drive-st3000dm001)

[Hitachi 2TB HD 7200 rpm](http://www.amazon.com/HITACHI-0F10311-2-0TB-3-0Gb-Buffer/product-reviews/B002WGH2QK/)	

[Western Digital Green HD](http://www.amazon.com/Western-Digital-Green-Desktop-WD40EZRX/product-reviews/B00EHBEUZO/)

* If you're going to use them, disable head parking using [this](http://support.wd.com/product/download.asp?groupid=609&sid=114&lang=en) utility.
 			
### Reliability

* https://www.backblaze.com/blog/backblaze-hard-drive-stats-q1-2021/
* https://www.backblaze.com/blog/backblaze-hard-drive-stats-for-2020/
* https://www.backblaze.com/blog/hard-drive-stats-for-2019/
* https://www.backblaze.com/blog/hard-drive-stats-for-2018/
* https://www.backblaze.com/blog/hard-drive-stats-for-2017/
* https://www.backblaze.com/blog/hard-drive-failure-rates-q3-2017/
* https://www.backblaze.com/blog/hard-drive-failure-stats-q2-2017/
* https://www.backblaze.com/blog/hard-drive-failure-rates-q1-2017/
* https://www.backblaze.com/blog/hard-drive-benchmark-stats-2016/
* https://www.backblaze.com/blog/hard-drive-failure-rates-q3-2016/
* https://www.backblaze.com/blog/hard-drive-failure-rates-q2-2016/
* https://www.backblaze.com/blog/hard-drive-reliability-stats-q1-2016/

## External HDDs in Enclosures

### Shucking

Refers to the process of removing a cheaper hard drive from an external enclosure for internal use. Doing so may or may not void the warranty.

* [WD EasyStore 8TB Compendium](https://www.reddit.com/r/DataHoarder/comments/7fx0i0/wd_easystore_8tb_compendium/)

You may ask "What drive model is in this external drive?".  
But the drive models inside externals can change every year making it hard to know what is inside until you buy one.

#### Why are external drives cheaper than internal ones?  
Theres multiple reasons to this, 

**There is a shorter warranty on a external drive.**  
Less warranty replacements reduces cost for the manufacturer, thus a lower sale price.  
And a bare drive is more likely to be damaged than one in a case (during shipping, installation or user error)  
An external drive may not be powered on as much as an internal drive is, so its more likely to live past the warranty period.

**There is more market demand for external drives**  
Not as many internal drives are sold as externals,  
When packaging and parts are made in bulk, the price does come down.

**Binning of performance parts**  
Like how CPU's get "binned" when they are manufactured, HDD's are too.  
Quite often the HDD's of lower end models can be physically the same as the top tier, only that they didnt meet the performance requirements.  
e.g. the white label WD's vs the Red label's. 

*Binning* is sorting the manufactured parts depending on its performance,  
e.g. the perfect chip may be used a top end CPU, whereas one with a defective core will be sold as a lower end CPU.  
The same applies to hard drives and SSD's.

For HDD's they are binned depending on:  

* Seek speed (how fast can the heads move into the correct position, this affects data transfer speed)  
* Spindle speed (the same motor can be spun slower if it did not meet the heat/vibration requirements at a higher speed, 5400rpm vs 7200rpm, this also affects data transfer speed)  
* Vibration (bare drives may end up in a enclosure with multiple drives, excessive vibration from one drive can affect the seek speed on another drive in close proximity, no problem in a single drive external enclosure)  
* Bad heads or platters (if a platter or head is bad, the firmware is set to lock the use of that problematic platter/head, and the drive is labelled with a lower capacity, less usable heads/platters means a lower transfer speed)

The point of *binning* is to reduce waste and maximize profit.

## Solid State Drives

While not much is known about data retention periods of SSDs, it's well known that they have a limited lifetime in terms of writes. Flash cells can only be erased so many times before rewritten voltage levels become ambiguous and data can no longer be distinctly identified.

There are several types of flash cells:

|Type|Full Type Name|Explanation / Comment|
|-|-|-|
|SLC|Single Level Cell|Best endurance, best performance, very expensive.|
|MLC|Multi Level Cell|Usually used for 2-level cells. Very good endurance, very good performance, expensive.|
|TLC|Triple Level Cell|Acceptable endurance, good performance.|
|QLC|Quad Level Cell|Poor endurance, acceptable performance, affordable.|

*=> More information on Wikipedia: https://en.wikipedia.org/wiki/Multi-level_cell*

There are several types of connectors used with SSDs:

|Type|Protocol|Explanation / Comment|
|-|-|-|
|[SATA](https://en.wikipedia.org/wiki/Serial_ATA#Cables,_connectors,_and_ports)|[SATA](https://en.wikipedia.org/wiki/Serial_ATA)|Standard SATA ports. Usually in 2.5" form factor.|
|[mSATA](https://en.wikipedia.org/wiki/Serial_ATA#Mini-SATA_\(mSATA\))|SATA|Small fixed dimensions add-in-card form factor.|
|[PCI-Express](https://en.wikipedia.org/wiki/PCI_Express#Form_factors)|[NVMe](https://en.wikipedia.org/wiki/NVM_Express), custom|Regular PCIe add-in-card form factor with attached rear slot shield.|
|[M.2](https://en.wikipedia.org/wiki/M.2)|NVMe, SATA|Small add-in-card form factor in varying lengths. NVMe x2, NVMe x4, and SATA compatibility depends on keying.|
|[U.2](https://en.wikipedia.org/wiki/U.2)|NVMe|Abusing SFF connectors originally intended for SAS to transmit PCI-Express.|


## Controllers

There are two generall types of storage controllers: RAID controllers and Host Bus Adapters (HBA).  
Hardware RAID controllers provide integrated RAID (IR) capabilities, presenting only the virtual volume to the operating system, opaquely performing the necessary actions for the desired RAID configuration.  
Host Bus Adapters present the connected drives to the OS as they are, this is also often called infrastructure (IT) mode. These cards may still perform internal optimizations in a manner that does not interfere with the OS commanded behaviour.

Some controller cards can be freely converted between IR- and IT-mode by flashing respective firmware versions, even fewer cards can be configured to do both at the same time (e.g. two of four HDDs in RAID mode, the other two in IT mode).

### Is it worth it to buy a hardware RAID controller? (AKA Hardware RAID vs Fake/Software RAID)

Short answer: Only if you get one with cache, if you don't do software RAID and stay away from fake RAID (e.g. Intel Rapid Storage Technology) at all times.

#### About Hardware RAID

The main benefit of hardware RAID controllers is that they alleviate all computations needed to perform RAID actions (e.g. compute and verify parity data) from the CPU. With modern hardware this benefit is barely worth it anymore, many CPUs can now easily perform these calculations on the side in a software RAID configuration. For controllers with integrated cache, there are significant performance benefits that most software and fake RAID implementations fail to or deliberately do not implement (for the sake of increased safety). Such benefits include but are not limited to write-back caching and adaptive read ahead.  
A drawback is limited compatibility; RAID volumes created with a specific controller can usually only be read/used by the same model controller, so if your controller breaks one might be in trouble finding a replacement.  
In conslusion, hardware RAID is only worth it if you need the highest performance.

#### About Software RAID

The main benefit of software RAID is compatibility: any system able to run the software should be able to read/use RAID volumes that were created with it, making it easy to recover data after a (non-drive) hardware failure - just move the drives to another system that can run the software.  
Drawback is the increased need for computing power needed especially for larger arrays.  
In conclusion, software RAID is a very good option when performance is not a huge concern, but recoverability is.

#### About Fake RAID

Fake RAID are called RAID implementations as found on many consumer level mainboards (e.g. Intel Rapid Storage Technology "IRST"). These implementations usually ship with a BIOS configuration utility and just enough hardware RAID capability to boot from a RAID volume. In reality however, these implementations rely heavily on software drivers once the OS is booted, making them essentially software RAID with none of the benefits and all the drawbacks of hardware RAID.  
In conclusion fake RAID should be avoided.

### LSI

Probably the most established brand of SAS/RAID controller cards. They also come rebranded under various names, for example *Broadcom* (which is their parent company), *Intel RAID* or *Dell PERC*.

An extensive list about all the different models and variants can be found here: https://forums.servethehome.com/index.php?threads/lsi-raid-controller-and-hba-complete-listing-plus-oem-models.599/ ([mirror](https://web.archive.org/web/20160410002618/https://forums.servethehome.com/index.php?threads/lsi-raid-controller-and-hba-complete-listing-plus-oem-models.599/))

A good tutorial for flashing SAS2008 based controllers (e.g. LSI 9211-8i, Dell PERC H310, ...) can be found here: https://techmattr.wordpress.com/2016/04/11/updated-sas-hba-crossflashing-or-flashing-to-it-mode-dell-perc-h200-and-h310/ ([mirror](https://web.archive.org/web/20170908021248/https://techmattr.wordpress.com/2016/04/11/updated-sas-hba-crossflashing-or-flashing-to-it-mode-dell-perc-h200-and-h310/))

Be aware that there are RAID controllers with and without cache (RAM), the former of which usually have more features and yield better performance but might not work so well in IT/JBOD mode (and frankly are usually overkill for IT/JBOD use).  

On HBAs with cache, enabling write-back and disk cache is only recommended in conjunction with a battery backup unit (BBU) or an uninterruptible power supply (UPS), so outstanding writes can be caught up on after or during a power outage.

### HighPoint

Not much is known about the quality of their controllers and not many people seem to be using them. They *look* alright but often get negative reviews mainly criticising bad drivers and poor OS support.

### SAS Expanders

SAS Expanders allow you to get the most out of your HBA in terms of drive quantity. Think of them as a SAS switch. [Here's an interesting illustration.](https://i.imgur.com/yFYmAjB.png)

#### HP Smart Array SAS Expander

A popular expander is the "HP Smart Array SAS Expander" card (HP part-no. 468406-B21), which allows for up to 24 drives to be connected to it with a single HBA uplink and 20 drives with two uplinks. It can be found used on ebay for as low as $19.  
It is a quite versatile expander supporting various uplink configrations and daisy-chaining. With latest firmware it can run SAS drives at 6 Gb/s and SATA drives at 3 Gb/s.  
An interesting article about it can be found here: https://forums.servethehome.com/index.php?threads/hp-sas-expander-wiki.146/ ([mirror](https://web.archive.org/web/20160410002618/https://forums.servethehome.com/index.php?threads/lsi-raid-controller-and-hba-complete-listing-plus-oem-models.599/))

Contrary to above article, a HP branded HBA is not necessary to upgrade the expanders firmware (but might be the safer choice).  
Tutorials on how to do it can be found at http://ronny-mueller.com/2017/02/07/howto-update-the-firmware-of-hp-sas-expander-468406-b21/ ([mirror](https://web.archive.org/web/20170916234608/http://ronny-mueller.com/2017/02/07/howto-update-the-firmware-of-hp-sas-expander-468406-b21/)) and https://serverfault.com/a/631575/81089 .  
Also note that cards bought (used) these days often ship with a newer firmware version than 1.52 already, so updating might not be absolutely necessary. Use "lsscsi" to find out.

### Getting Server/Enterprise Expansion PCI-Express Cards to Run in Consumer Mainboards

This isn't always as much of a Plug-and-Play experience as with graphics cards for example. There are several reasons why a PCIe card may not function properly or prevent the entire system from booting, the most common however are SMBus incompatibilities.

Since SMBus is not required for a PCIe card to function, the according pins can be taped over with negligible side effects. [They are the face-side 5th and 6th pin from the left and can be easily masked with a neatly cut piece of tape.](https://i.imgur.com/EYaqnHv.jpg)  
Tipp: Leave a little notch of tape that folds over to the other side of the card but doesn't mask any pins there; this prevents the slot from ripping off the tape during insertion. Also, if you don't have any insulation tape, sellotape works just as well, duct tape can also be used but may be too thick.

## CPUs		

Things to look for:

 * ECC Memory support (you also need ECC support in your mainboard and ECC DIMMs) (so memory errors don't screw up your data)
 * PCI-Express lanes (if you plan on using many HBAs without Expanders)

AMD Ryzen - A modern CPU on a modern platform supporting ECC *and* Non-ECC DDR4 UDIMMs.
 			
[Intel Pentium G1820](https://pcpartpicker.com/part/intel-cpu-bx86g1820) - practically the cheapest CPU ($45) that supports ECC memory and it's plenty fast enough for a server that's just acting as a file server and some lighter-weight services.

Intel Pentium G3220 - if you want cheap and ECC. Lower-medium performance, medium energy usage. ~$60

Intel Xeon E3-1231v3 - if you want high performance, ECC, and VT-d for PCI passthrogh (necessary for virtualizing many NAS operating systems and file systems, with correct configuration of storage controller). ~$250

Intel Xeon E3-1245v3 - ?

[Intel Xeon E5-2670](https://ark.intel.com/products/64595/Intel-Xeon-Processor-E5-2670-20M-Cache-2_60-GHz-8_00-GTs-Intel-QPI) (v1) - Can be found for under $100 on ebay, supports ECC and boasts 8 cores / 16 threads

Core i3-4130T - if you want energy/heat savings, medium performance, and ECC. Sips power with a 35W TDP. ~$135



## Longevity of digital storage media for offline (unpowered) storage.  

The listed date ranges are based on ideal storage and being able to recover the data without corruption from the storage media.  It is likely the media will last longer but the chance of corruption or failure increases.   
Listed best to worst:   

* M-Disc – 50 years – when stored correctly away from light.    
* Tape – LTO tape is rated for 30 years +   
* HDD (air) – 10  years + (odds of mechanical failure increases over time).   
* HDD (Helium) – 5 to 10 years. The helium will slowly escape the drive over time, the heads will crash into the platter if the helium level is low (this is reported in SMART data).   
* SSD (SLC) – Single level cell – 1+ years,  these are the types of NAND flash used in SD cards or USB sticks designed for long periods of sitting in a draw somewhere.   
* SSD (MLC/TLC/QLC) – 1 month – depending on model of flash chips in the drive, the more states of charge per cell (bits per cell) the quicker data corruption occurs when the state of charge changes over time.   

Each storage medium has advantages and disadvantages, do a little bit of googling to find out which media suits your needs best, and how to store it correctly. Some types of media are more prone to damage than others.   

“I’ve got [X, Y, Z] media that had lasted longer than your numbers, you are wrong!” No, you are just lucky you have something which has lasted without noticeable corruption. Most media formats have some level of built in error correction to mitigate read errors.  
(Notably, SSD/flash drives are not guaranteed to last a long time.)


Reminder; Mean Time Between Failures (MTBF) and Mean Time To Failure (MTTF) are completely different things.   
The MTBF is not the drives designed lifespan.  
Manufacturers will give a MTBF value for calulating the expected faliure rate in a large deployment of hard drives that are within their designed lifespan (or warranty period).


For beginners confused by all this – just use any cheap WD or Seagate HDD, its more than likely going to meet all your needs.
