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
$ cat /etc/snmp/snmpd.conf|grep dns-socket-count<br>
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
## change config<br>
$ vi /usr/local/bin/dns-socket-count<br>
<table width="800"><tr><td>
#!/bin/bash<br>
##############################################################<br>
#BIND<br>
#PID=`cat /var/run/named.pid`<br>
<br>
#UNBOUND<br>
#PID=`cat /var/run/unbound/unbound.pid`<br>
<br>
#PowerDNS Recursor<br>
#PID=`cat /var/run/pdns_recursor.pid`<br>
<br>
#DNSDIST<br>
PID=`cat /var/run/dnsdist.pid`<br>
##############################################################<br>
</td></tr></table>
## Notes
プロセスが開いているsocket数をカウントしてみる。<br>
ls -al /proc/${PID}/fd|grep socket|wc -l　でカウント<br>
