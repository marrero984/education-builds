# How to Classroom in a Box

This should be done on an OSX device with internet access.

### Downlaod the CentOS iso
1. Download the latest "Everything" iso from  
     [centos.org](https://www.centos.org/download/)
     * The download is >8GB.

### Copy files from the CentOS iso after mounting it.

1. Insert a USB drive ( >8GB ) and erase with Disk Utility with the following settings  
    * Name: CIAB
    * Format: MS-DOS
    * Scheme: GUID Partition Map
    If you do not see the scheme option, you have selected the drive volume and not the disk; click on the parent and try again.
1. Attach the CD but don't mount  
    `hdiutil attach -nomount <Centos iso>`
    This will return a new partition name `/dev/<disk number>`, which is required during the mount step.
1. Make a directory to mount the CD  
    `mkdir files`
1. Mount the partition returned by hdiutil to the new directory  
    `mount_cd9660 <new partition> files`
1. Copy all of the files from ./files to the USB drive:  
    `cp -R ./files/* /Volumes/CIAB`

### Copy files from this directory.

1. clone this directory somewhere:  
    `git clone git@github.com:puppetlabs/education-builds.git`
1. cd to the `classroom_in_a_box` directory  
    `cd education_builds/classroom_in_a_box`
1. Copy the `ks` folder to the USB drive:  
    `cp -R ./ks /Volumes/CIAB`
1. Copy the grub.cfg to the USB drive:  
    `cp EFI/BOOT/grub.cfg /Volumes/CIAB/EFI/BOOT/grub.cfg`

### Installation on the NUC

1. Eject the USB drive from your OSX device.
1. Ensure that the NUC has a network connection.
1. Plug the USB drive into the NUC and boot from the drive
