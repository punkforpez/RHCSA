 *To enable X-11 forwarding over ssh*

    $ ssh -X root@server virt-manager


## Network outline for test network needed per Ch. 2

| Domain 1 | example.com       |
| -------- | ----------------- |
| Clients  | server1 / tester1 |
| IP       | 192.168.122.0/24  |

| Domain 2 | example.org      |
| -------- | ---------------- |
| Client   | outsider1        |
| IP       | 192.168.100.0/24 |

*For a total 3 VMs.  Server1 should be configured with minimal install w/GUI*

##### KVM-based VMs:

- Normally configured in /etc/libvirt and /var/lib/libvirt

##### virt-install

- terminal command to install VM without the GUI
- key switches for the command:

| switch            | purpose                                              |
| ----------------- | ---------------------------------------------------- |
| -n(name)          | Sets the name of the VM                              |
| - -vcpus          | Configures number of virtual CPUs                    |
| -r (- -ram)       | Configures amount of RAM in MB                       |
| - -disk           | Defines the virtual disk                             |
| -l (- -location)  | Specifies directory or URL of install files          |
| - -graphics       | Graphical display (vnc, spice, and none)             |
| -x(--extra-args=) | Includes extra data, such as URL of a Kickstart file |

##### virsh

- command line installer
- when run alone it will start it's own prompt
- type 'help' to show options
- useful virsh commands:

| command            | purpose                                   |
| ------------------ | ----------------------------------------- |
| autostart <domain> | configures domain to start with host boot |
| capabilities       | list capabilities of local hypervisor     |
| edit <domain>      | edits XML configuration for domain        |
| list --all         | lists all domains                         |
| start <domain>     | boots given domain                        |
| shutdown <domain>  | shuts down given domain                   |
| destroy <domain>   | immediate shutdown of a domain            |

##### virt-clone

- used to clone an existing VM
- make sure system being cloned is shutdown
- if on a production network, it is best to boot to clone machine's rescue target
  * this is to enable modification of hostname and ip address
- when cloning a machine with multiple disks, each one must be specified with the --file switch

![5d4234abd8f8d19763](https://i.loli.net/2019/08/01/5d4234abd8f8d19763.png)



#### Kickstart

- Red Hat Solution for automated install of RHEL

- doesn't include custom settings created after basic installation is complete.
  
  - can base these settings on a post-install script (beyond scop of RHCSA exam)

- two methods for creating kickstart config file
  
  1. anaconda-ks.cfg file in /root
  
  2. use gui (**system-config-kickstart** command)



##### 


