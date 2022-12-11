# homelab

## Requirements

Before starting, make sure that:
 * server runs on 192.168.2.3
 * `ssh-copy-id -i ~/.ssh/id_rsa root@192.168.2.3` is done
 * `zpool import -f nvme`

## Resources
https://3os.org/infrastructure/proxmox/gpu-passthrough/igpu-split-passthrough/#linux-virtual-machine-igpu-passthrough-configuration

SPICE?
https://gist.github.com/tomdaley92/789688fc68e77477d468f7b9e59af51c

## Run
```
ansible-playbook site.yml
```

## Manual

### ISO download

```
cd /var/lib/vz/template/iso
wget https://releases.ubuntu.com/22.04/ubuntu-22.04-desktop-amd64.iso?_ga=2.121777026.802320440.1653742907-1208040621.1653742907 -O ubuntu-22.04-desktop-amd64.iso
wget 'https://software.download.prss.microsoft.com/db/Win10_21H2_EnglishInternational_x64.iso?t=c93c2ad1-1181-4758-8383-317b54f7c560&e=1653904509&h=ac1118a66f11aeaf4302ee5d2fe84987c63aef862a32bc20513f63d575302486' -O Win10_21H2_EnglishInternational_x64.iso

wget -P /var/lib/vz/template/iso https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso

```

### Troubleshoot video

echo 1 > /sys/bus/pci/devices/0000\:00\:02.0/remove
echo 1 > /sys/bus/pci/rescan

echo "options vfio_iommu_type1 allow_unsafe_interrupts=1" >> /etc/modprobe.d/iommu_unsafe_interrupts.conf
echo "options kvm ignore_msrs=1" >> /etc/modprobe.d/kvm.conf


```