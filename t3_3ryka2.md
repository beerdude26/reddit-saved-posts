---
kind: thread
author: haxxa
domain: self.DataHoarder
is_self: true
created: 1446948045
permalink: /r/DataHoarder/comments/3ryka2/help_me_decide_btrfs_zfs_unraid_local_backups/
id: 3ryka2
name: t3_3ryka2
subreddit: DataHoarder
subreddit_id : t5_2x7he
title: Help me decide - BTRFS, ZFS, Unraid, Local Backups?
url: https://www.reddit.com/r/DataHoarder/comments/3ryka2/help_me_decide_btrfs_zfs_unraid_local_backups/
---

Hi Guys, 

I'm currently looking to migrate my home server to something a little more reliable and safe. 

My Current Setup is:

OS: Proxmox 4 


MB: ASROCK Extreme4 (970)
CPU: AMD FX8350
RAM: 12GB DDR3 (NON-EEC)
PCIE: M1015 IBM Raid Card (Passthrough Flashed)
PCIE: Nvidia GTX770 (Steam Streaming VM Passthrough)



SSD: 1x 256GB   (OS + APP DRIVE)
        1x 128GB    (Windows VM Passthrough)
        1x 64GB      (VM Drive) 

HDD: 1x 1TB Drive (LVM)
         2x 2TB Drive (LVM)
         1X 3TB Drive (LVM)




Currently the LVM has no form of protection, its 1 Volume and if any of the drives fail I lose all my data. I have a crashplan Backup but with my Internet speed I am unable to backup data adequately. I am looking to use a new FS that will allow me to get the most space I can to use while offering protection from one drive failure. I like unraid as it meets the bill and allows the most space however I don't like the license cost nor the closed nature of it. ZFS also seems good and stable but should have EEC Ram and doesn't offer enough space in a mixed drive solution. Then there is BTRFS which seems to not be recomended in any Raid5 form. So I'm not sure what I should immplement? If you guys have any suggestions let me know. 

Goals-
1. Maxmise Space per drive I want to have atleast 5TB - (Willing to buy another drive to do this).
2. Allow some protection (minimal) against one drive failure. 
3. Allow me to continue to use apps and virtual machines with IOMMU passthrough.

I have heard BTRFS Raid 5 can be setup using different sized disks? If this is the case is it stable? What space will I be left with? 

Any ideas on what I should do please let me know :) Let me know if more info is needed.  Thanks 


(PS. First Post here so please suggest if my question is best suited elsewhere or should be rephrased). 

 
 
 

EDIT: Another solution I am considering is just rsyncing to my local desktop and that way I have less chance of failure from external factors, furthermore I could just buy a cheap external 5TB and do daily backups over LAN.
