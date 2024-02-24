# NFS-RPI

ansible configuration for setting up a network file share my raspberry-pi 


## Why would you do this? 
why not?


## Interesting how do i use? 

If you haven't already, install [ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) on your host machine

**Edit the vars as required**
```yaml 
# nfs/vars/main.yml 
---
# vars file for ./nfs
shared_dir_name: void_drive
usb_drive: /dev/sda1 
```

**Edit the inventory**

```ini 
# inventory.ini
[all]
yourserver.local
```

*Run the playbook*  

```bash 
 ansible-playbook playbook.yaml
```

**mount the drive to you machine**


```bash
sudo mount -o vers=4,resvport -t nfs serverip:/mnt/void_drive ~/location/on/your/machine
``` 

### Troubleshooting

if for some reason this doesn't seem to work here are somethings to try

- Check if the drive is indeed mounted on your rpi or target machine ( `df -h`) is your friend ;) 
    - if it's not try mounting it manually 

- restart nfs `sudo systemctl restart nfs-server`


Happy hacking!! 




