---
layout: post
title:  "How to setup kvm on redhat 7 "
date:   2016-09-20 +0800
categories:
- linux
- kvm setup
tags:
- linux
- centos
- redhat
- kvm setup
---

{% highlight shell %}
[prabhu@localhost ~]$ sudo yum groupinfo  "Virtualization Host"
Failed to set locale, defaulting to C
Loaded plugins: product-id, search-disabled-repos, subscription-manager

Environment Group: Virtualization Host
 Environment-Id: virtualization-host-environment
 Description: Minimal virtualization host.
 Mandatory Groups:
   +base
   +core
   +virtualization-hypervisor
   +virtualization-tools
 Optional Groups:
   +debugging
   +network-file-system-client
   +remote-system-management
   +virtualization-platform
[prabhu@localhost ~]$ yum groupinstall "Virtualization Host" -y
{% endhighlight %}

after installation enable libvirtd service 

{% highlight shell %}
[prabhu@localhost ~]$ sudo systemctl enable libvirtd 
Created symlink from /etc/systemd/system/sockets.target.wants/virtlockd.socket to /usr/lib/systemd/system/virtlockd.socket.
[prabhu@localhost ~]$ sudo systemctl start libvirtd
[prabhu@localhost ~]$ sudo systemctl status libvirtd
● libvirtd.service - Virtualization daemon
   Loaded: loaded (/usr/lib/systemd/system/libvirtd.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2016-12-25 14:14:51 SGT; 10h ago
     Docs: man:libvirtd(8)
           http://libvirt.org
 Main PID: 10966 (libvirtd)
   CGroup: /system.slice/libvirtd.service
           ├─ 2409 /sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro --dhcp-script=/usr/libexec/libvirt_leaseshelper
           ├─ 2411 /sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro --dhcp-script=/usr/libexec/libvirt_leaseshelper
           ├─10966 /usr/sbin/libvirtd
           ├─11070 /sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro --dhcp-script=/usr/libexec/libvirt_leaseshelper
           └─11071 /sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro --dhcp-script=/usr/libexec/libvirt_leaseshelper
{% endhighlight %}

To verifiy that everything is working 
( i have docker container service enabled on this host so it displays lxc status, for kvm only QEMU servies are important )
{% highlight shell %}
[prabhu@untrinilium ~]$ virt-host-validate 
setlocale: No such file or directory
  QEMU: Checking for hardware virtualization                                 : PASS
  QEMU: Checking if device /dev/kvm exists                                   : PASS
  QEMU: Checking if device /dev/kvm is accessible                            : PASS
  QEMU: Checking if device /dev/vhost-net exists                             : PASS
  QEMU: Checking if device /dev/net/tun exists                               : PASS
  QEMU: Checking for cgroup 'memory' controller support                      : PASS
  QEMU: Checking for cgroup 'memory' controller mount-point                  : PASS
  QEMU: Checking for cgroup 'cpu' controller support                         : PASS
  QEMU: Checking for cgroup 'cpu' controller mount-point                     : PASS
  QEMU: Checking for cgroup 'cpuacct' controller support                     : PASS
  QEMU: Checking for cgroup 'cpuacct' controller mount-point                 : PASS
  QEMU: Checking for cgroup 'cpuset' controller support                      : PASS
  QEMU: Checking for cgroup 'cpuset' controller mount-point                  : PASS
  QEMU: Checking for cgroup 'devices' controller support                     : PASS
  QEMU: Checking for cgroup 'devices' controller mount-point                 : PASS
  QEMU: Checking for cgroup 'blkio' controller support                       : PASS
  QEMU: Checking for cgroup 'blkio' controller mount-point                   : PASS
  QEMU: Checking for device assignment IOMMU support                         : WARN (No ACPI DMAR table found, IOMMU either disabled in BIOS or not supported by this hardware platform)
   LXC: Checking for Linux >= 2.6.26                                         : PASS
   LXC: Checking for namespace ipc                                           : PASS
   LXC: Checking for namespace mnt                                           : PASS
   LXC: Checking for namespace pid                                           : PASS
   LXC: Checking for namespace uts                                           : PASS
   LXC: Checking for namespace net                                           : PASS
   LXC: Checking for namespace user                                          : PASS
   LXC: Checking for cgroup 'memory' controller support                      : PASS
   LXC: Checking for cgroup 'memory' controller mount-point                  : PASS
   LXC: Checking for cgroup 'cpu' controller support                         : PASS
   LXC: Checking for cgroup 'cpu' controller mount-point                     : PASS
   LXC: Checking for cgroup 'cpuacct' controller support                     : PASS
   LXC: Checking for cgroup 'cpuacct' controller mount-point                 : PASS
   LXC: Checking for cgroup 'cpuset' controller support                      : PASS
   LXC: Checking for cgroup 'cpuset' controller mount-point                  : PASS
   LXC: Checking for cgroup 'devices' controller support                     : PASS
   LXC: Checking for cgroup 'devices' controller mount-point                 : PASS
   LXC: Checking for cgroup 'blkio' controller support                       : PASS
   LXC: Checking for cgroup 'blkio' controller mount-point                   : PASS
{% endhighlight %}

optionally can install virtual machine manager gui

{% highlight shell %}
[prabhu@untrinilium ~]$ yum search virt-manager
{% endhighlight %}

**this is simple/basic installation of the kvm on redhat 7**
