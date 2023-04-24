
# Домашнее задание к занятию "`10.1 «Keepalived/vrrp»`" - `Яковлев Константин`

### Задание 1 Разверните топологию из лекции и выполните установку и настройку сервиса Keepalived

![job.v2.1](https://github.com/Prime2270/homework_netology-10.1/blob/main/screenshots/job.v2.1.png)

![job.v2.2](https://github.com/Prime2270/homework_netology-10.1/blob/main/screenshots/job.v2.2.png)

`keepalived`

```
vrrp_instance test-yakovlev-1.2 {

state MASTER

interface eth0

virtual_router_id 11

priority 110

advert_int 4

authentication {

auth_type AH

auth_pass 1111

}

unicast_peer {

10.128.0.28

}

virtual_ipaddress {

10.128.0.200 dev eth0 label eth0:vip

}

}
```

`keepalived-2`

```
vrrp_instance test-yakovlev-1.2 {

state MASTER

interface eth0

virtual_router_id 11

priority 110

advert_int 4

authentication {

auth_type AH

auth_pass 1111

}

unicast_peer {

10.128.0.24

}

virtual_ipaddress {

10.128.0.200 dev eth0 label eth0:vip

}

}
}
```
