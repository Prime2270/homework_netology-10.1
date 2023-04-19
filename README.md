
# Домашнее задание к занятию "`10.1 «Keepalived/vrrp»`" - `Яковлев Константин`

### Задание 1 Разверните топологию из лекции и выполните установку и настройку сервиса Keepalived

![job1](https://github.com/Prime2270/homework_netology-10.1/blob/main/screenshots/job1.png)

![job1.1](https://github.com/Prime2270/homework_netology-10.1/blob/main/screenshots/job1.1.png)

`keepalived-1, 1 noda`

```
vrrp_instance test-yakovlev {
state MASTER
interface eth0
virtual_router_id 17
priority 110
advert_int 4
authentication {
auth_type AH
auth_pass 1234
}
unicast_peer {
10.128.0.9
}
virtual_ipaddress {
10.128.0.40 dev eth0 label eth0:vip
}
}
```

`keepalived-2, 2 noda`

```
vrrp_instance test-yakovlev-1 {
state BACKUP
interface eth0
virtual_router_id 17
priority 110
advert_int 4
authentication {
auth_type AH
auth_pass 1234
}
unicast_peer {
10.128.0.18
}
virtual_ipaddress {
10.128.0.40 dev eth0 label eth0:vip
}
}
```
