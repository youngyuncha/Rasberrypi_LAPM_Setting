# Rasberrypi_LAPM_Setting


기존에 설치된 패키지들을 업그레이드
sudo apt update
sudo apt upgrade




Apache 웹서버
- 클라우드 서비스, 워드프레스 웹사이트 등을 운영하기 위해서는 웹서버가 필요하며 웹서버는 크롬, 파이어폭스, 익스플로
러 같은 웹브라우저 클라이언트에서 요청을 받으면 그에 따라 웹페이지, 파일 전송 등의 역할


apache 설치
sudo apt install apache2



"http://라즈베리파이 IP주소" // 웹서버가 정상적으로 설치되었는지 확인




PHP
- PHP(Hypertext Preprocessor)는 서버 측에서 실행되는 스크립트 언어(Server-side scripting)이며 정적인 HTML 언어로만 구성 WEB을 동적으로 사용 하는 용도




- php 모듈 설치
sudo apt install php php-fpm php-curl php-gd php-intl php-mbstring php-mysql php-soap php-xml php-xmlrpc php-zip libapache2-mod-php




PHP 설치 확인
sudo nano /var/www/html/phpinfo.php  // vi 로 열어도 되지만 vim editor 없을시 기본제공인 nano 사용



file 열고 입력
<?php phpinfo(); ?>



저장: "Ctrl + X" 
동의: "Y", "Enter"
밖으로 나가기 : "Ctrl + O"



"http://라즈베리파이 IP주소/phpinfo.php" // 설치된 php 정보를 볼 수 있다.




MariaDB
- MariaDB는 관계형 데이터베이스 관리 시스템(RDBMS, Relational DataBase Management System)입니다. 데이터베이스란 구조화된 데이터의 집합을 의미하며 이러한 데이터 집합의 관리를 위해서 MySQL, MariaDB 같은 데이터베이스 관리 시스템을 이용해야 함.




MariaDB 패키지를 설치하는 명령어
sudo apt install mariadb-server 

대부분 동의후 비밀번호 설정 영문, 숫자, 특수보호 포함 해야됨





MariaDB 접속
sudo mysql -u root -p



아래와 같은 형태가 나오면 정상 접속
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 56
Server version: 10.3.22-MariaDB-0+deb10u1 Raspbian 10
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.




비밀번호 입력후 밑에 입력  utf8 인코딩, testDB라는 이름으로 새로운 데이터 베이스를 생성하는 의미
CREATE DATABASE testDB DEFAULT CHARACTER SET utf8;




관리자 계정이 아닌 새로운 유저 계정으로 접속
CREATE USER '새로운 유저 ID'@'localhost' IDENTIFIED BY '비밀번호';




새로운 유저 ID' 에게 testDB 데이터베이스 권한을 부여하는 명령어
GRANT ALL PRIVILEGES ON testDB.* TO '새로운 유저 ID'@'localhost'





phpMyAdmin
phpMyAdmin 은 데이터베이스 관리를 시각적으로 편리하게 관리할 수 있는 웹 인터페이스이다.




phpmyadmin 패키지를 설치하는 명령어
sudo apt install phpmyadmin //apache2선택 yes, 비밀번호 입력




우분투에서는 바로 접속이 가능하지만 라즈비안은 경로가 달라 설정을 해줘야함
sudo ln -s /usr/share/phpmyadmin /var/www/html




"http://라즈베리파이 IP주소/phpmyadmin" // phpmyadmin 접속 가능 확인

초기 ID는 "phpmyadmin"이며 비밀번호는 설치시 입력한 비번





phpmyadmin 데이터베이스 권한 부여

sudo mysql

GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'localhost'



