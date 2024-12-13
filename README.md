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
ip address 41.2.2.1 255.255.255.240
end
write


```