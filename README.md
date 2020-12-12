# Samba Active Directory server
This playbook deploys a Samba Domain Controller for an Active Directory domain.  

# Commands
List shares<br>
<pre>
smbclient -L localhost -N
</pre><br>

Verify authentication by logging on to the netlogon share using the domain administrator account<br>
<pre>
smbclient //localhost/netlogon -UAdministrator -c 'ls'
</pre><br>

Test AD DNS<br>
<pre>
host -t SRV _ldap._tcp.anet.internal.
host -t SRV _kerberos._udp.anet.internal.
host -t A ad.anet.internal.
</pre><br>

Request a Kerberos ticket for the domain administrator account<br>
<pre>
kinit administrator
</pre><br>

List the cached Kerberos tickets<br>
<pre>
Klist
</pre><br>
