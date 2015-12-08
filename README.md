# dns-socket-count-cacti-template

====
<br>
## Requirement<br>
OS:CentOS6<br>
Package:cacti-0.8.8b-7.el6.noarch<br>
<br>
## Install<br>
-- edit snmpd.conf<br>
$ cat snmpd.conf.add >> /etc/snmp/snmpd.conf<br>
<br>
-- check example<br>
$ cat /etc/snmp/snmpd.conf|grep dns-socket<br>
extend .1.3.6.1.4.1.18689.0.6 dns-socket-count /usr/local/bin/dns-socket-count<br>
<br>
-- copy dns-socket-count<br>
$ cp dns-socket-count /usr/local/bin/<br>
$ chmod 755 /usr/local/bin/dns-socket-count<br>
<br>
-- check example<br>
$ /usr/local/bin/dns-socket-count<br>
outputsocket:13<br>
<br>
## Notes
