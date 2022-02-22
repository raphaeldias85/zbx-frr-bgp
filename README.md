# Monitoring FRR BGP sessions for zabbix

## Description
Discover and monitor BGP sessions with count of prefix or state like "Active" or Idle (Admin).
Trigger if session change state.

## Requirements
- Python3
- Zabbix from 3.4 version

## Installation
- copy zbx-frr-bgp to /usr/local/sbin
- give execute bit `chmod +x /usr/local/sbin/zbx-frr-bgp`
- copy file userparameter_zbx-frr-bgp.conf to /etc/zabbix/zabbix_agentd.d/
- Provide vtysh access to user zabbix
  ```
  sudo usermod -a -G frrvty zabbix
  sudo usermod -a -G frr zabbix
  ```
- restart zabbix-agent
```
systemctl restart zabbix-agent
```
- Import template file

///
Based on https://github.com/den1s/quagga_zabbix_bgp_mon
