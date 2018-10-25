# Information Gathering

### Operating System Enumeration

The distribution and kernel versions will be key pieces of information in attempting to locate a viable local privilege escalation attack. Often a particular kernel version or linux distribution will be vulnerable to a well known specific exploit or avenue for privilege escalation.



#### Determine linux distribution and version

```bash
cat /etc/issue
cat /etc/*-release
cat /etc/lsb-release
cat /etc/redhat-release
cat /etc/os-release
```

#### Determine kernel version - 32 or 64-bit?

```bash
cat /proc/version
uname -a
uname -mrs
rpm -q kernel
dmesg | grep Linux
ls /boot | grep vmlinuz-
```

#### List environment variables

```bash
cat /etc/profile
cat /etc/bashrc
cat ~/.bash_profile
cat ~/.bashrc
cat ~/.bash_logout
env
```

### Application and Services Enumeration

#### Determine which services are running

```bash
ps aux
ps -ef
top
cat /etc/service 
```

#### Determine which services are running as root

```bash
ps aux | grep root
ps -ef | grep root
```

#### Determine installed applications

```bash
ls -alh /usr/bin/
ls -alh /sbin/
dpkg -l
rpm -qa
ls -alh /var/cache/apt/archivesO
ls -alh /var/cache/yum/
yum list | grep installed
Solaris: pkginfo
Arch Linux: pacman -Q 
```

#### Determine versions of important applications

```bash
gcc -v
mysql --version
java -version
python --version
ruby -v
perl -v
```



#### Review installed configurations

**Syslog Configuration**

```bash
cat /etc/syslog.conf
```

**Web Server Configurations**

```bash
cat /etc/chttp.conf
cat /etc/lighttpd.conf
cat /etc/apache2/apache2.conf
cat /etc/httpd/conf/httpd.conf
cat /opt/lampp/etc/httpd.conf
```

**PHP Configuration**

```text
/etc/php5/apache2/php.ini
```

**MySQL Configuration**

```text
cat /etc/my.conf
```

#### Determine scheduled jobs

```bash
crontab -l
ls -alh /var/spool/cron
ls -al /etc/ | grep cron
ls -al /etc/cron*
cat /etc/cron*
cat /etc/at.allow
cat /etc/at.deny
cat /etc/cron.allow
cat /etc/cron.deny
cat /etc/crontab
cat /etc/anacrontab
cat /var/spool/cron/crontabs/root
```

#### Locate any plaintext usernames and passwords

```bash
grep -i user [filename]
grep -i pass [filename]
grep -C 5 "password" [filename]
find . -name "*.php" -print0 | xargs -0 grep -i -n "var $password"   # Joomla 
```



### Communications and Networking Enumeration

#### Identify connected NICs and other networks

```bash
/sbin/ifconfig -a
cat /etc/network/interfaces
cat /etc/sysconfig/network
```

#### Identify connected users and hosts

```bash
lsof -nPi
lsof -i :80
grep 80 /etc/services
netstat -antup
netstat -antpx
netstat -tulpn
chkconfig --list
chkconfig --list | grep 3:on
last
w
```

#### Identify cached IP or MAC addresses

```bash
arp -a
route -n
/sbin/route -nee
ip ro show
```

#### Identify network configuration Settings \(DHCP, DNS, Gateway\)

```bash
cat /etc/resolv.conf
cat /etc/hosts
cat /etc/sysconfig/network
cat /etc/networks
iptables -L
iptables -t nat -L
hostname
dnsdomainname
```

#### Is packet sniffing possible

```bash
# tcpdump tcp dst [ip] [port] and tcp dst [ip] [port]
tcpdump tcp dst 192.168.1.7 80 and tcp dst 10.2.2.222 21
```

#### Check for ports open for local only connections

```bash
netstat -tupan
```

#### Is tunneling possible

```bash
ssh -D 127.0.0.1:9050 -N [username]@[ip] 
proxychains ifconfig
```



### User and Confidential Information Enumeration



### File System Enumeration





