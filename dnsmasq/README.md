dnsmasq
=========

Ansible role which installs / configures dnsmasq


Role Variables
--------------

Defaults
```

dnsmasq_domain_needed: true # Never forward plain names (without a dot or domain part)
dnsmasq_bogus_priv: true # Never forward addresses in the non-routed address spaces
dnsmasq_expand_hosts: true # To have a domain automatically added to simple names in a hosts-file
dnsmasq_no_resolv: false # If you don't want dnsmasq to read /etc/resolv.conf

dnsmasq_port: "53" # Configure a port
dnsmasq_conf_dir: "/etc/dnsmasq.d" # Include a another lot of configuration options
```

Optional variables
```
dnsmasq_interface # If you want dnsmasq to listen for DHCP and DNS requests only on specified interfaces
dnsmasq_resolv_file # If you want dns to get its upstream servers from somewhere other that /etc/resolv.conf
dnsmasq_domain # Set the domain for dnsmasq
dnsmasq_listen_address # Which interface to listen on by address
dnsmasq_address # Add domains which you want to force to an IP address here
dnsmasq_server # Add other name servers here, with domain specs if they are for non-public domains.
```

Example Playbook
----------------

```
---
- hosts: localhost
  become: yes
  roles:
    - role: dnsmasq
      dnsmasq_no_resolv: true
      dnsmasq_server: /localnet/192.168.0.1

```
