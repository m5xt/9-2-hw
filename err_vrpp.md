Домашнее задание к занятию 10.1 «Keepalived/vrrp»
**

Домашнее задание выполните в Google Docs и отправьте в личном кабинете на проверку ссылку на ваш документ.

Название файла должно содержать номер лекции и фамилию студента. Пример названия: «10.1 Keepalived/vrrp — Александр Александров»

Перед тем как выслать ссылку, убедитесь, что её содержимое не приватно, т. е. открыто на просмотр всем, у кого есть ссылка. Если нужно прикрепить дополнительные ссылки, просто добавьте их в Google Docs.

Любые вопросы по решению задач задавайте в чате учебной группы.

Задание 1
Разверните топологию из лекции и выполните установку и настройку сервиса Keepalived.

vrrp_instance test {

state "name_mode"

interface "name_interface"

virtual_router_id "number id"

priority "number priority"

advert_int "number advert"

authentication {

auth_type "auth type"

auth_pass "password"

}

unicast_peer {

"ip address host"

}

virtual_ipaddress {

"ip address host" dev "interface" label "interface":vip

}

}





1)

                    /etc/keepalived/keepalived.conf
                    
vrrp_instance test {

state MASTER

interface ens37

virtual_router_id 10

priority 150

advert_int 4

authentication {

  auth_type PASS
  
  auth_pass 12345
  
  }
  
unicast_peer {

  192.168.10.12
  
  }
  
  virtual_ipaddress {
  
  192.168.10.50/24 dev ens37 label ens37:vip
  
  }
  
}


![alt text](https://github.com/m5xt/9-2-hw/blob/srlb-14/img/pic_10_01_2.png)

2)

                        /etc/keepalived/keepalived.conf
                        
vrrp_instance test {

state BACKUP

interface ens38

virtual_router_id 10

priority 90

advert_int 4

authentication {

auth_type PASS

auth_pass 12345

}

unicast_peer {

192.168.10.11

}

virtual_ipaddress {

192.168.10.50/24 dev ens38 label ens37:vip

}

}




![alt text](https://github.com/m5xt/9-2-hw/blob/srlb-14/img/pic_10_01_1.png)





