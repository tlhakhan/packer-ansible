# packer-ansible
ansible playbook for packer deployments of virtual machines on vmware vsphere hosts

# Example run

```
[root@devbox-20 packer-ansible]# ansible-playbook deploy.yml --extra-vars @extra-vars/kube-00.yml  -i hosts

PLAY [localhost] 

TASK [packer-template : ensure that the kube-00 is not alive] 
changed: [localhost]

TASK [packer-template : end play early, kube-00 is alive] 
skipping: [localhost]

TASK [packer-template : generate packer template for kube-00] 
ok: [localhost]

TASK [packer-template : build vm kube-00] 
Kchanged: [localhost]

TASK [packer-template : packer output] 
ok: [localhost] => {
    "packer_build_output.stdout": "\u001b[1;32mvmware-iso: output will be in this color.\u001b[0m\n\n\u001b[1;32m==> vmware-iso: Retrieving ISO\u001b[0m\n\u001b[1;32m==> vmware-iso: Trying http://192.168.200.130:8081/iso/CentOS-7-x86_64-M
inimal-1908.iso\u001b[0m\n\u001b[1;32m==> vmware-iso: Trying http://192.168.200.130:8081/iso/CentOS-7-x86_64-Minimal-1908.iso?checksum=md5%3A7002b56184180591a8fa08c2fe0c7338\u001b[0m\n\u001b[1;32m==> vmware-iso: http://192.168.200.130:808
1/iso/CentOS-7-x86_64-Minimal-1908.iso?checksum=md5%3A7002b56184180591a8fa08c2fe0c7338 => /data/dev-data/packer_cache/4efd6202b248f7601db3aefb3c1c512fb8b9cc05.iso\u001b[0m\n\u001b[1;32m==> vmware-iso: Remote cache was verified skipping re
mote upload...\u001b[0m\n\u001b[1;32m==> vmware-iso: Creating required virtual machine disks\u001b[0m\n\u001b[1;32m==> vmware-iso: Building and writing VMX file\u001b[0m\n\u001b[1;32m==> vmware-iso: Registering remote VM...\u001b[0m\n\u00
1b[1;32m==> vmware-iso: Starting virtual machine...\u001b[0m\n\u001b[1;32m==> vmware-iso: Waiting 10s for boot...\u001b[0m\n\u001b[1;32m==> vmware-iso: Connecting to VM via VNC (vs-21:5900)\u001b[0m\n\u001b[1;32m==> vmware-iso: Typing the
 boot command over VNC...\u001b[0m\n\u001b[1;32m==> vmware-iso: Waiting for SSH to become available...\u001b[0m\n\u001b[1;32m==> vmware-iso: Connected to SSH!\u001b[0m\n\u001b[1;32m==> vmware-iso: Gracefully halting virtual machine...\u00
1b[0m\n\u001b[0;32m    vmware-iso: Waiting for VMware to clean up after itself...\u001b[0m\n\u001b[1;32m==> vmware-iso: Deleting unnecessary VMware files...\u001b[0m\n\u001b[0;32m    vmware-iso: Deleting: /vmfs/volumes/datastore1/kube-00/
vmware.log\u001b[0m\n\u001b[1;32m==> vmware-iso: Compacting all attached virtual disks...\u001b[0m\n\u001b[0;32m    vmware-iso: Compacting virtual disk 1\u001b[0m\n\u001b[1;32m==> vmware-iso: Cleaning VMX prior to finishing up...\u001b[0m
\n\u001b[0;32m    vmware-iso: Detaching ISO from CD-ROM device ide0:0...\u001b[0m\n\u001b[0;32m    vmware-iso: Disabling VNC server...\u001b[0m\n\u001b[1;32m==> vmware-iso: Skipping export of virtual machine...\u001b[0m\n\u001b[1;32m==> v
mware-iso: Keeping virtual machine registered with ESX host (keep_registered = true)\u001b[0m\n\u001b[1;32mBuild 'vmware-iso' finished.\u001b[0m\n\n==> Builds finished. The artifacts of successful builds are:\n--> vmware-iso: VM files in
directory: /vmfs/volumes/datastore1/kube-00"
}
```
