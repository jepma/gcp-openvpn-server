# OpenVPN Server - GCP

This file holds a simple configuration of a openvpn-server, at the Google Cloud Platform.

## SSH-Keys

We use project-wide ssh-key configuration.

## Steps to be automated

### Get disk ID

```
$ sudo lsblk
```

### Format disk

We only have to format the disk, once! So we need to make a check that does this for us.

```
sudo mkfs.ext4 -m 0 -F -E lazy_itable_init=0,lazy_journal_init=0,discard /dev/sdb
```

### Mount disk

```
sudo mkdir -p /mnt/disks/openvpn
sudo mount -o discard,defaults /dev/sdb /mnt/disks/openvpn
sudo chmod a+w /mnt/disks/openvpn
sudo cp /etc/fstab /etc/fstab.backup
```

Retrieve the UUID

```
sudo blkid /dev/[DEVICE_ID]
```
