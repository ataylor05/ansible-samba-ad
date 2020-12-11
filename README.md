# BIND DNS server
something here

## Example 
Here is an example of the main.yml file to deploy this playbook.<br>
<pre>
---
- hosts: localhost
  gather_facts: True
  become: True
  roles:
    - role: common
      vars:
        fqdn_hostname: dns.anet.local
        selinux_state: disabled
    - role: BIND
      vars:
        forward_zone_name: anet.internal
        dns_sec: no
    - role: Samba-PDC
      vars:
        samba_version: "4.13.2"
        domain_name: anet
        realm: anet.internal
        administrator_password: Passw@ord123!
        dns_backend: BIND9_DLZ
</pre>
<br><br>
**ansible-playbook -i hosts main.yml**