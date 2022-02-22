# Monitoring FRR BGP sessions for zabbix

## Description
Discover and monitor BGP session with count of prefix or state like "Active" or Idle (Admin).
Trigger if session change state.

## Requirements
- Python3
- Zabbix from 3.4 version

## Installation
- copy bgpmon to /usr/local/sbin
- give execute bit `chmod +x /usr/local/sbin/bgpmon`
- write file for zabbix agent for example /etc/zabbix/zabbix_agentd.d/userparameter_zbx-frr-bgp.conf
```sh
UserParameter=bgp.peers.discovery,/usr/local/sbin/bgpmon discovery
UserParameter=bgp.peer.state[*],/usr/local/sbin/bgpmon neighbor_state -n $1
```
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
