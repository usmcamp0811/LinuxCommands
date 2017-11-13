List drives on machine:
     
     sudo lsblk -o name,mountpoint,label,size,uuid,fstype
 
 
Outpts:
 
      cassandra@PiCamp0:/ $ sudo lsblk -o name,mountpoint,label,size,uuid,fstype
      NAME                       MOUNTPOINT LABEL       SIZE UUID                                 FSTYPE
      loop1                                               2G                                      
      └─docker-179:2-518668-pool                        100G 8f4f5e86-915a-4bea-8046-f8e40a34306b ext4
      loop0                                             100G 8f4f5e86-915a-4bea-8046-f8e40a34306b ext4
      └─docker-179:2-518668-pool                        100G 8f4f5e86-915a-4bea-8046-f8e40a34306b ext4
      sda                                               5.5T                                      
      └─sda1                                BackupData  5.5T 1da8bfba-c94c-4dba-959e-5b2c2c598f7d ext4
      mmcblk0                                            29G                                      
      ├─mmcblk0p2                /                     28.9G b105f9a8-f450-4976-8ac8-69053f57bab4 ext4
      └─mmcblk0p1                /boot      boot         41M 95E0-9AC4                            vfat

Additional Options:

      Available columns:
           NAME  device name
          KNAME  internal kernel device name
        MAJ:MIN  major:minor device number
         FSTYPE  filesystem type
      MOUNTPOINT  where the device is mounted
          LABEL  filesystem LABEL
           UUID  filesystem UUID
             RO  read-only device
             RM  removable device
          MODEL  device identifier
           SIZE  size of the device
          STATE  state of the device
          OWNER  user name
          GROUP  group name
           MODE  device node permissions
      ALIGNMENT  alignment offset
         MIN-IO  minimum I/O size
         OPT-IO  optimal I/O size
        PHY-SEC  physical sector size
        LOG-SEC  logical sector size
           ROTA  rotational device
          SCHED  I/O scheduler name
        RQ-SIZE  request queue size
           TYPE  device type
       DISC-ALN  discard alignment offset
      DISC-GRAN  discard granularity
       DISC-MAX  discard max bytes
      DISC-ZERO  discard zeroes data

#### Backup Command:

Make sure that the same user owns the directory:
     
    chown mcamp:users /backupdrive/Backups/MainPC/media/mcamp
    
MainPC
 
    rdiff-backup --terminal-verbosity 8 --print-statistics \
    --exclude-globbing-filelist $HOME/.excludes /home/mcamp \
    mcamp@picamp0::/backupdrive/Backups/MainPC/home/mcamp
    
    rdiff-backup --terminal-verbosity 8 --print-statistics \
    --exclude-globbing-filelist $HOME/.excludes /media/mcamp/LocalSSHD/ \
    mcamp@picamp0::/backupdrive/Backups/MainPC/media/mcamp/LocalSSHD/


MainLaptop

    rdiff-backup --terminal-verbosity 8 --print-statistics \
    --exclude-globbing-filelist $HOME/.excludes /home/mcamp \
    mcamp@picamp0::/backupdrive/Backups/MainLaptop/home/mcamp

### Useful Links

   [Wiki on fstab](https://wiki.archlinux.org/index.php/Fstab)