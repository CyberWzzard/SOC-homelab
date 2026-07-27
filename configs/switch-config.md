# Cisco Catalyst 3850 Switch Commands & Verification Log

This document contains the complete command history and verification logs

## 1. Core Verification

### A. VLAN (`show vlan br`)
```text
VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active
10   Endhosts_Users                   active    Gi1/0/7, Gi1/0/8, Gi1/0/9
                                                Gi1/0/10, Gi1/0/11, Gi1/0/12
20   Attacker                         active    Gi1/0/13, Gi1/0/14, Gi1/0/15
                                                Gi1/0/16, Gi1/0/17, Gi1/0/18
30   SOC                              active    Gi1/0/20, Gi1/0/21, Gi1/0/22
                                                Gi1/0/23, Gi1/0/24
40   Endhosts_Servers                 active    Gi1/0/25, Gi1/0/26, Gi1/0/27
                                                Gi1/0/28, Gi1/0/29, Gi1/0/30
99   Management                       active    Gi1/0/1, Gi1/0/2, Gi1/0/3
                                                Gi1/0/4, Gi1/0/5, Gi1/0/6
999  Unused_Ports                     active    Gi1/0/31, Gi1/0/32, Gi1/0/33
                                                Gi1/0/34, Gi1/0/35, Gi1/0/36
                                                Gi1/0/37, Gi1/0/38, Gi1/0/39
                                                Gi1/0/40, Gi1/0/41, Gi1/0/42
                                                Gi1/0/43, Gi1/0/44, Gi1/0/45
                                                Gi1/0/46, Gi1/0/47, Gi1/0/48
                                                Gi1/1/1, Gi1/1/2, Te1/1/3
                                                Te1/1/4
```

### B. Access Control List (`show ip access-lists`)
```text
Extended IP access list 100
    10 deny ip any 192.168.3.0 0.0.0.255
    20 permit ip any any
```
### C. ACL applied to VLAN 20 Inbound (`show ip int vlan 20 | include Inbound`)
```text
  Inbound Common access list is not set
  Inbound  access list is 100
```
### D. SPAN (`show monitor session all`)
```text
Session 1
---------
Type                     : Local Session
Source VLANs             :
    Both                 : 10,20,40
Destination Ports        : Gi1/0/19
    Encapsulation        : Native
          Ingress        : Disabled

```
### E. Interface Status (`show ip int br`)
```text
Interface              IP-Address      OK? Method Status                Protocol
Vlan1                  unassigned      YES NVRAM  up                    down
Vlan10                 192.168.1.1     YES NVRAM  up                    up
Vlan20                 192.168.2.1     YES NVRAM  up                    up
Vlan30                 192.168.3.1     YES NVRAM  up                    up
Vlan40                 192.168.4.1     YES NVRAM  up                    up
Vlan99                 10.0.0.1        YES NVRAM  up                    up
GigabitEthernet0/0     unassigned      YES unset  down                  down
GigabitEthernet1/0/1   unassigned      YES unset  down                  down
GigabitEthernet1/0/2   unassigned      YES unset  down                  down
GigabitEthernet1/0/3   unassigned      YES unset  up                    up
GigabitEthernet1/0/4   unassigned      YES unset  down                  down
GigabitEthernet1/0/5   unassigned      YES unset  down                  down
GigabitEthernet1/0/6   unassigned      YES unset  down                  down
GigabitEthernet1/0/7   unassigned      YES unset  down                  down
GigabitEthernet1/0/8   unassigned      YES unset  down                  down
GigabitEthernet1/0/9   unassigned      YES unset  up                    up
GigabitEthernet1/0/10  unassigned      YES unset  down                  down
GigabitEthernet1/0/11  unassigned      YES unset  up                    up
GigabitEthernet1/0/12  unassigned      YES unset  down                  down
GigabitEthernet1/0/13  unassigned      YES unset  down                  down
GigabitEthernet1/0/14  unassigned      YES unset  down                  down
GigabitEthernet1/0/15  unassigned      YES unset  up                    up
GigabitEthernet1/0/16  unassigned      YES unset  down                  down
GigabitEthernet1/0/17  unassigned      YES unset  down                  down
GigabitEthernet1/0/18  unassigned      YES unset  down                  down
GigabitEthernet1/0/19  unassigned      YES unset  up                    down
GigabitEthernet1/0/20  unassigned      YES unset  down                  down
GigabitEthernet1/0/21  unassigned      YES unset  up                    up
GigabitEthernet1/0/22  unassigned      YES unset  down                  down
GigabitEthernet1/0/23  unassigned      YES unset  up                    up
GigabitEthernet1/0/24  unassigned      YES unset  down                  down
GigabitEthernet1/0/25  unassigned      YES unset  up                    up
GigabitEthernet1/0/26  unassigned      YES unset  down                  down
GigabitEthernet1/0/27  unassigned      YES unset  down                  down
GigabitEthernet1/0/28  unassigned      YES unset  down                  down
GigabitEthernet1/0/29  unassigned      YES unset  down                  down
GigabitEthernet1/0/30  unassigned      YES unset  down                  down
GigabitEthernet1/0/31  unassigned      YES unset  administratively down down
GigabitEthernet1/0/32  unassigned      YES unset  administratively down down
GigabitEthernet1/0/33  unassigned      YES unset  administratively down down
GigabitEthernet1/0/34  unassigned      YES unset  administratively down down
GigabitEthernet1/0/35  unassigned      YES unset  administratively down down
GigabitEthernet1/0/36  unassigned      YES unset  administratively down down
GigabitEthernet1/0/37  unassigned      YES unset  administratively down down
GigabitEthernet1/0/38  unassigned      YES unset  administratively down down
GigabitEthernet1/0/39  unassigned      YES unset  administratively down down
GigabitEthernet1/0/40  unassigned      YES unset  administratively down down
GigabitEthernet1/0/41  unassigned      YES unset  administratively down down
GigabitEthernet1/0/42  unassigned      YES unset  administratively down down
GigabitEthernet1/0/43  unassigned      YES unset  administratively down down
GigabitEthernet1/0/44  unassigned      YES unset  administratively down down
GigabitEthernet1/0/45  unassigned      YES unset  administratively down down
GigabitEthernet1/0/46  unassigned      YES unset  administratively down down
GigabitEthernet1/0/47  unassigned      YES unset  administratively down down
GigabitEthernet1/0/48  unassigned      YES unset  administratively down down
GigabitEthernet1/1/1   unassigned      YES unset  administratively down down
GigabitEthernet1/1/2   unassigned      YES unset  administratively down down
GigabitEthernet1/1/3   unassigned      YES unset  administratively down down
GigabitEthernet1/1/4   unassigned      YES unset  administratively down down
Te1/1/1                unassigned      YES unset  administratively down down
Te1/1/2                unassigned      YES unset  administratively down down
Te1/1/3                unassigned      YES unset  administratively down down
Te1/1/4                unassigned      YES unset  administratively down down

```

## 2. Complete Command History
<details>
<summary><b>Click to expand the full command log</b></summary>

| Device | Mode               | Command                                                                         | Task                                                         |
|:-------|:-------------------|:--------------------------------------------------------------------------------|:-------------------------------------------------------------|
| Switch | >                  | en                                                                              |                                                              |
| SW1    | #                  | conf t                                                                          |                                                              |
| Switch | (config)#          | hostname SW1                                                                    | hostname setup                                               |
| SW1    | (config)#          | line con 0                                                                      |                                                              |
| SW1    | (config-line)#     | logging synchronous                                                             | logging type                                                 |
| SW1    | (config)#          | no ip http server                                                               | disable config through web                                   |
| SW1    | (config)#          | no ip http secure-server                                                        |                                                              |
| SW1    | (config)#          | no cdp run                                                                      | disable cdp                                                  |
| SW1    | (config)#          | clock timezone timezoneName offset#                                             | set time settings (specifics redacted for privacy)           |
| SW1    | (config)#          | clock summer-time timezoneName 1 Saturday March 00:00 1 Saturday November 00:00 |                                                              |
| SW1    | (config)#          | service timestamps log datetime localtime show-timezone year                    |                                                              |
| SW     | (config)#          | ip routing                                                                      | enable routing on switch                                     |
| SW1    | (config)#          | vlan 10                                                                         | VLANS                                                        |
| SW1    | (config-vlan)#     | name Endhosts\_Users                                                             |                                                              |
| SW1    | (config-vlan)#     | vlan 20                                                                         |                                                              |
| SW1    | (config-vlan)#     | name Attacker                                                                   |                                                              |
| SW1    | (config-vlan)#     | vlan 30                                                                         |                                                              |
| SW1    | (config-vlan)#     | name SOC                                                                        |                                                              |
| SW1    | (config-vlan)#     | vlan 40                                                                         |                                                              |
| SW1    | (config-vlan)#     | name Endhosts\_Servers                                                           |                                                              |
| SW1    | (config-vlan)#     | vlan 99                                                                         |                                                              |
| SW1    | (config-vlan)#     | name Management                                                                 |                                                              |
| SW1    | (config-vlan)#     | vlan 999                                                                        |                                                              |
| SW1    | (config-vlan)#     | name Unused\_Ports                                                               |                                                              |
| SW1    | (config)#          | int range g1/0/7-12                                                             | Apply VLANS to interfaces                                    |
| SW1    | (config-if-range)# | switchport mode access                                                          |                                                              |
| SW1    | (config-if-range)# | switchport access vlan 10                                                       |                                                              |
| SW1    | (config)#          | int range g1/0/13-18                                                            |                                                              |
| SW1    | (config-if-range)# | switchport mode access                                                          |                                                              |
| SW1    | (config-if-range)# | switchport access vlan 20                                                       |                                                              |
| SW1    | (config)#          | int range g1/0/19-24                                                            |                                                              |
| SW1    | (config-if-range)# | switchport mode access                                                          |                                                              |
| SW1    | (config-if-range)# | switchport access vlan 30                                                       |                                                              |
| SW1    | (config)#          | int range g1/0/25-30                                                            |                                                              |
| SW1    | (config-if-range)# | switchport mode access                                                          |                                                              |
| SW1    | (config-if-range)# | switchport access vlan 40                                                       |                                                              |
| SW1    | (config)#          | int range g1/0/1-6                                                              |                                                              |
| SW1    | (config-if-range)# | switchport mode access                                                          |                                                              |
| SW1    | (config-if-range)# | switchport access vlan 99                                                       |                                                              |
| SW1    | (config)#          | in range g1/0/31-48, g1/1/1-4, t1/1/1-4                                         |                                                              |
| SW1    | (config-if-range)# | switchport mode access                                                          |                                                              |
| SW1    | (config-if-range)# | switchport access vlan 999                                                      |                                                              |
| SW1    | (config-if-range)# | shutdown                                                                        | Disabled unused ports                                        |
| SW1    | (config)#          | int range g1/0/1-30                                                             | enable portfast and bpduguard                                |
| SW1    | (config-if-range)# | spanning-tree portfast                                                          |                                                              |
| SW1    | (config-if-range)# | spanning-tree bpduguard enable                                                  |                                                              |
| SW1    | (config)#          | monitor session 1 source vlan 10 , 20 , 40 both                                 | SPAN for SOC Server                                          |
| SW1    | (config)#          | monitor session 1 destiniation int g1/0/19                                      |                                                              |
| SW1    | (config)#          | int vlan 10                                                                     | SVIs                                                         |
| SW1    | (config-if)#       | ip address 192.168.1.1 255.255.255.0                                            |                                                              |
| SW1    | (config-if)#       | no shut                                                                         |                                                              |
| SW1    | (config-if)#       | int vlan 20                                                                     |                                                              |
| SW1    | (config-if)#       | ip address 192.168.2.1 255.255.255.0                                            |                                                              |
| SW1    | (config-if)#       | no shut                                                                         |                                                              |
| SW1    | (config-if)#       | int vlan 30                                                                     |                                                              |
| SW1    | (config-if)#       | ip address 192.168.3.1 255.255.255.0                                            |                                                              |
| SW1    | (config-if)#       | no shut                                                                         |                                                              |
| SW1    | (config-if)#       | int vlan 40                                                                     |                                                              |
| SW1    | (config-if)#       | ip address 192.168.4.1 255.255.255.0                                            |                                                              |
| SW1    | (config-if)#       | no shut                                                                         |                                                              |
| SW1    | (config-if)#       | int vlan 99                                                                     |                                                              |
| SW1    | (config-if)#       | ip address 10.0.0.1 255.255.255.0                                               |                                                              |
| SW1    | (config-if)#       | no shut                                                                         |                                                              |
| SW1    | (config)#          | int vlan 10                                                                     | DHCP relay agent for Endhosts\_Users vlan                     |
| SW1    | (config-if)#       | ip helper-address 192.168.4.3                                                   |                                                              |
| SW1    | (config)#          | ip route 0.0.0.0 0.0.0.0 10.0.0.10                                              | Default gateway (for temporary internet access)              |
| SW1    | (config)#          | ip access-list extended 100                                                     | ACL: Prevent Attacker from talking to SOC |
| SW1    | (config-ext-nacl)# | 10 deny ip any 192.168.3.0 0.0.0.255                                            |                                                              |
| SW1    | (config-ext-nacl)# | 20 permit ip any any                                                            |                                                              |
| SW1    | (config-ext-nacl)# | int vlan 20                                                                     |                                                              |
| SW1    | (config-if)#       | ip access-group 100 in                                                          |                                                              |

</details>
