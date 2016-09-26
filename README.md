docs.openstack.org

server 0.th.pool.ntp.org
server 1.asia.pool.ntp.org
server 2.asia.pool.ntp.org

http://docs.openstack.org/mitaka/install-guide-rdo/
https://etherpad.openstack.org/p/sipa
http://vasabilab.cs.tu.ac.th/presentations/OpenStack-tutorial-day1-july2015.pdf

$ git clone https://github.com/itbakery/training.git
$ cd openstack1  && vagrant destroy
$ vagrant status
$ vagrant ssh controller
[vagrant@controller ~]$
 
$ ping compute -c 4
$ sudo su -
# openssl rand -hex 10
bf487bc7590bb3e44e32
# echo "export DB_PASS=bf487bc7590bb3e44e32"  >> password

!!!
Security   NOVA   =>  NOVA_PASS, NOVA_DBPASS
                CINDER =>  CINDER_PASS, CINDER_DBPASS
                
!!! 
Host network   controller  -> ip a

    eth0   -> Gateway to internet

    eth1 (10.10.10.10) -> management network / api-network


!!! 
DNS  ->  /etc/hosts  (local dns)
!!! 
NTP  ->  time sync -> controller  ------ sync --------- time server 

    list ntp server:        

           server 0.th.pool.ntp.org
           server 1.asia.pool.ntp.org
           server 2.asia.pool.ntp.org

cp /etc/chrony.conf  /etc/chrony.conf.back

systemctl start chronyd
systemctl enable chronyd
systemctl status chronyd

chronyc sources
cd openstack1docs.openstack.org
http://docs.openstack.org/mitaka/install-guide-rdo/
https://etherpad.openstack.org/p/sipa
http://vasabilab.cs.tu.ac.th/presentations/OpenStack-tutorial-day1-july2015.pdf
 
$ git clone https://github.com/itbakery/training.git
$ cd openstack1  && vagrant destroy
$ vagrant status
$ vagrant ssh controller
[vagrant@controller ~]$
 
$ ping compute -c 4
$ sudo su -
# openssl rand -hex 10
bf487bc7590bb3e44e32
# echo "export DB_PASS=bf487bc7590bb3e44e32"  >> password
 
!!!
Security   NOVA   =>  NOVA_PASS, NOVA_DBPASS
                CINDER =>  CINDER_PASS, CINDER_DBPASS
                
!!! 
Host network   controller  -> ip a

    eth0   -> Gateway to internet

    eth1 (10.10.10.10) -> management network / api-network

     

!!! 
DNS  ->  /etc/hosts  (local dns)
 
!!! 
NTP  ->  time sync -> controller  ------ sync --------- time server 

    list ntp server:        

           server 0.th.pool.ntp.org
           server 1.asia.pool.ntp.org
           server 2.asia.pool.ntp.org
!!!
install ntp (Chrony)
 
# yum install
           
[root@controller ~]# rpm -qa | grep chrony
chrony-2.1.1-1.el7.centos.x86_64
[root@controller ~]# rpm -ql chrony-2.1.1-1.el7.centos.x86_64 | grep conf              
[root@controller ~]# cp /etc/chrony.conf  /etc/chrony.conf.back 
[root@controller ~]# vi /etc/chrony.conf
 
           server 0.th.pool.ntp.org  iburst
           server 1.asia.pool.ntp.org iburst
           server 2.asia.pool.ntp.org iburst:
 
[root@controller ~]# systemctl start chronyd
[root@controller ~]# systemctl enable chronyd
[root@controller ~]# systemctl status chronyd
 
[root@controller ~]# chronyc sources
210 Number of sources = 4
MS Name/IP address         Stratum Poll Reach LastRx Last sample
===============================================================================
^- 124.109.2.169                 3  10   377   392  +1165us[+1165us] +/-   43ms
^* 122.155.169.213               2  10   377   440    -68us[ -269us] +/- 9224us
^- 203.146.215.116               2  10   377   649   +656us[ +456us] +/-   21ms
^- 203.158.247.150               2   9   377   204  +1553us[+1553us] +/-   33ms

!!!
NTP on Controller
# yum install chrony
# vi /etc/chrond.conf
:
server 10.10.10.10 iburst

systemctl restart chronyd


!!!
Timezone  (controll + compute)
# timedatectl
[root@controller ~]# timedatectl list-timezones | grep Bangkok
Asia/Bangkok
[root@controller ~]# timedatectl set-timezone Asia/Bangkok
[root@controller ~]# timedatectl 
      Local time: Mon 2016-09-26 10:50:15 ICT
  Universal time: Mon 2016-09-26 03:50:15 UTC
        RTC time: Mon 2016-09-26 03:50:17
       Time zone: Asia/Bangkok (ICT, +0700)
     NTP enabled: yes
NTP synchronized: yes
 RTC in local TZ: no
      DST active: n/a
[root@controller ~]# 









 





