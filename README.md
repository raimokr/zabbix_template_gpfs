# zabbix_template_gpfs
Zabbix Template for GPFS (General Parallel File System) Cluster Filesystem with LLD-Discovery

v0.1 beta

This Zabbix template monitors a GPFS Cluster via a GPFS snmp_collector node.

All items, triggers and graphs are generated automatically with Low-Level-Discovery rules for:
- GPFS Cluster
- GPFS Disks Information
- GPFS Disks Performance
- GPFS File Systems
- GPFS File Systems Performance
- GPFS Nodes
- GPFS Storage Nodes

Tested with Zabbix 2.4.5 in a productive environment with GPFS Version 4.1.0.0

Please keep in mind: THIS IS BETA! Unfortunately I have no lab environment here for testing, only two productive clusters. This is the very first shot.

So any feedback is welcome! Feel free to contribute either directly here on https://github.com/raimokr/zabbix_template_gpfs/ or contact me via email at raimo.kraeuchi@gmail.com

Installation guide:
1. be sure your GPFS snmp_collector node is set up correctly according to this guide: http://www.ibm.com/developerworks/library/l-snmp-gpfs/
2. import template in Zabbix (you don't have to create any mappings beforehand)
3. create a new host and associate the template
4. define the parameters for the SNMP interface, connect it to the GPFS snmp_collector
5. Done! Wait about 20-30 minutes and Zabbix will create all items, triggers, graphs etc. automatically

Notice: You don't need to import GPFS MIB file into Zabbix.

Important:
I highly recommend to implement a Zabbix action rule of type "internal" that alerts you whenever item "GPFS Cluster Name - SNMP Ping" changes state from "normal" to "not supported". You can filter for Application "Availability". With that you can ensure, that you get alerted if the snmp_collector is not reachable (Zabbix sends out no trigger alerts if the items get status "not supported"!)

ToDo:
- at least adding {MACROS} for SNMP-Community (sorry, forgot that)
- adding more SSH Checks and with that get more information out of the GPFS Cluster (e.g. mmgetstate, mmlscluster, mmlsnode etc.)
- tuning, optimizing, debugging

Have fun!
Raimo Kräuchi
https://plus.google.com/+RaimoKrauchi
