# OSIS
Для работы по ОСИС
R1
```text
enable
configure terminal
interface loopback 100
ip address 211.0.0.254 255.255.255.248

```
R2
```text
enable
configure terminal
interface loopback 200
ip address 221.0.0.121 255.255.255.248
end
write

```
R3
```text
enable
configure terminal
interface loopback 300
ip address 31.1.1.6 255.255.255.248
end
write

```
R4
```text
enable
configure terminal
interface loopback 400
ip address 41.2.2.129 255.255.255.240
end
write


```


R1
```text
enable
configure terminal
interface fa0/0
ip address 14.1.1.2 255.255.255.224
duplex full
no shutdown
interface fa1/0
ip address 12.0.0.225 255.255.255.224
duplex full
no shutdown
end
write
```

R2
```text
enable
configure terminal
interface fa0/0
ip address 12.0.0.226 255.255.255.224
duplex full
no shutdown
interface fa1/0
ip address 23.0.0.33 255.255.255.224
duplex full
no shutdown
end
write
```

R3
```text
enable
configure terminal
interface fa0/0
ip address 23.0.0.34 255.255.255.224
duplex full
no shutdown
interface fa1/0
ip address 34.1.1.33 255.255.255.240
duplex full
no shutdown
end
write
```

R4
```text
enable
configure terminal
interface fa0/0
ip address 34.1.1.34 255.255.255.240
duplex full
no shutdown
interface fa1/0
ip address 14.1.1.1 255.255.255.224
duplex full
no shutdown
end
write
```

R1
```text
enable
configure terminal
ip route 23.0.0.0 255.255.255.0 12.0.0.226
ip route 34.1.1.0 255.255.255.128 14.1.1.1
ip route 221.0.0.0 255.255.255.128 12.0.0.226
ip route 31.1.1.0 255.255.255.0 12.0.0.226
ip route 41.2.2.128 255.255.255.0 14.1.1.1
end
write
```

R2
```text
enable
configure terminal
ip route 14.1.1.0 255.255.255.0 12.0.0.225
ip route 34.1.1.0 255.255.255.128 23.0.0.34
ip route 211.0.0.0 255.255.255.0 12.0.0.225
ip route 31.1.1.0 255.255.255.0 23.0.0.34
ip route 41.2.2.128 255.255.255.0 23.0.0.34
end
write
```

R3
```text
enable
configure terminal
ip route 12.0.0.128 255.255.255.128 23.0.0.33
ip route 14.1.1.0 255.255.255.0 34.1.1.34
ip route 211.0.0.0 255.255.255.0 23.0.0.33
ip route 221.0.0.0 255.255.255.128 23.0.0.33
ip route 41.2.2.0 255.255.255.0 34.1.1.34
end
write
```

R4
```text
enable
configure terminal
ip route 12.0.0.128 255.255.255.128 14.1.1.2
ip route 23.0.0.0 255.255.255.0 34.1.1.33
ip route 211.0.0.0 255.255.255.0 14.1.1.2
ip route 221.0.0.0 255.255.255.128 34.1.1.33
ip route 31.1.1.0 255.255.255.0 34.1.1.33
end
write
```


enable
configure terminal
access-list 10 permit 221.0.0.121
access-list 10 permit 12.0.0.226
access-list 10 permit 23.0.0.33
access-list 10 deny any
line vty 0 4
access-class 10 in
login local
transport input ssh
end
write
