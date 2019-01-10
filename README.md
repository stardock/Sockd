# sockd
dante-server / sockd ? The private sockd service 

Environment:

$ cat /etc/redhat-release 
CentOS Linux release 7.3.1611 (Core) 
$ uname -a
Linux xxx 3.10.0-514.6.2.el7.x86_64 #1 SMP Thu Feb 23 03:04:39 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Start to build:
1. Download Source code

wget https://www.inet.no/dante/files/dante-1.4.2.tar.gz

2. Install dependence package

yum install -y autoconf automake binutils gcc make rpm-build rpmdevtools

yum install -y bison flex glibc-devel libtool pam-devel

yum install -y gcc make rpm-build bison flex pam-devel

3. Build package

rpmbuild -ta dante-1.4.2.tar.gz

4. Install the RPM

rpm -ivh rpmbuild/RPMS/x86_64/dante-1.4.2-1.el7.centos.x86_64.rpm

rpm -ivh rpmbuild/RPMS/x86_64/dante-server-1.4.2-1.el7.centos.x86_64.rpm

5. Setup configure

vim /etc/sockd.conf
vim /etc/socks.conf

Configure for reference

    sockd.conf
    https://gist.github.com/kagasu/6be00c08f8eb8cbec56fe1b32ac82034/revisions
    socks.conf
    https://gist.github.com/kagasu/279edf63e8e1b64f432ceb27e2a79bf5/revisions

6. Setup firewall to allowed

firewall-cmd --zone=public --add-port=1080/tcp --permanent
firewall-cmd --reload

7. Start your service

systemctl restart sockd



Special thanks for the reference:
https://kagasu.hatenablog.com/entry/2017/08/26/173052     (thumb)

http://lixingcong.github.io/2018/05/25/dante-socks5/

https://lvii.gitbooks.io/outman/content/dante.html
