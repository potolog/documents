# CentOS 8.0 에 MariaDB 10.4 설치하기

## MariaDB repository 설정
CentOS 8.0 의 default mariadb version 은 10.3 인데, 이것을 10.4 로 변경한다.

https://downloads.mariadb.org/mariadb/repositories/#distro=CentOS&distro_release=centos8-amd64--centos8&mirror=i3dnet&version=10.4

위의 내용을 참고로 하여 아래와 같이 MariaDB.repo 를 편집한다.

vi /etc/yum.repos.d/MariaDB.repo
<pre>
# MariaDB 10.4 CentOS repository list - created 2019-10-27 14:37 UTC
# http://downloads.mariadb.org/mariadb/repositories/
[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.4/centos8-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
</pre>

편집을 마친 후에 아래와 같이 명령을 실행하면, MariaDB 10.4 가 설치된다.

<pre>
sudo dnf install boost-program-options
sudo dnf install MariaDB-server MariaDB-client --disablerepo=AppStream 
sudo dnf install MariaDB-devel --disablerepo=AppStream  # mariadb_config 가 필요할 때
sudo systemctl start mariadb
# sudo systemctl enable mariadb  # 10.4 에서는 할 필요가 없다.
</pre>

<hr>

## Repository Key 설정 (옵션)

rpm --import https://yum.mariadb.org/RPM-GPG-KEY-MariaDB

dnf update

<hr>

## MariaDB 설치 (옵션)

dnf --disablerepo=AppStream install MariaDB-server MariaDB-client

<hr>

## root 사용자 설정

MariaDB 를 설치한 후에 초기 root 비밀번호를 설정한다.
<pre>
# /usr/bin/mysqladmin -u root password '설정하려는 비밀번호'
# mysql -u root -p
(비밀번호 입력)
MariaDB [(none)]> use mysql;
# 원격에서 root 로 접속이 가능하게 설정한다.
MariaDB [mysql]> GRANT ALL ON *.* to 'root'@'%' IDENTIFIED BY '비밀번호' WITH GRANT OPTION;
MariaDB [mysql]> flush privileges;
</pre>

<hr>

## 방화벽 해제

<pre>
firewall-cmd --permanent --zone=public --add-port=3306/tcp
firewall-cmd --reload
</pre>

