---
category: products
layout: products
title: CODI
permalink: /products/sns
intro: 마크다운
banner: ../assets/img/banner/banner-4.jpg
video: <iframe width="100%" height="315" src="https://www.youtube.com/embed/RROqH1DgisQ?ecver=2" frameborder="0" allowfullscreen="" class="style-scope uengine-products"></iframe>
github: https://github.com/TheOpenCloudEngine/process-codi

---

<br>

# 설치 방법

### 1. Tomcat 다운로드

[Tomcat Download](http://tomcat.apache.org/download-70.cgi) 좌측의 'Tomcat Download' 버튼을 클릭하여 Tomcat사이트로 이동 후, 하단의 Binary Distributions의 core - zip을 선택하여 다운받는다. (해당 Tomcat 버전은 Tomcat7버전)

***
<br>
### 2. Tomcat 설치

다운 받은 Tomcat은 원하는 경로에 압축을 해제 후, webapp에 있는 기존 파일을 모두 삭제한다.

***
<br>
### 3. MySQL 설치
이 설치 방법은 MySQL을 기준으로 작성되어 있습니다.
[MySQL 설치 방법](http://withcoding.com/26) 필요한 경우, 좌측의 MySQL 설치 방법을 참조하시면 됩니다.

MySQL 설치 후, Schema 생성을 한다.

생성된 Schema에 Tomcat/webapps/ROOT/resource/mysql 안에있는 processcodi.sql을 Import 한다.

***
<br>
### 4. ProcessCodi war 다운로드
[WAR Download](https://oss.sonatype.org/content/repositories/snapshots/org/uengine/process-codi/1.0.0r-SNAPSHOT/process-codi-1.0.0r-20170803.045936-1.war) 좌측의 'WAR Download'버튼을 클릭하여 ProcessCodi war파일을 다운받은후, 2번에서 해제한 Tomcat 폴더의 webapp 폴더로 이동시킨다.

***  
<br>
### 5. war파일 해제
command창을 이용하여 Tomcat/webapp 폴더에 접근 후, 
```
jar -xvf [war파일 명].war
```
을 실행한다.
***
<br>
### 6. uengine.properties 수정
Tomcat/webapp/ROOT/WEB-INF/classes/org/uengine 경로로 이동하여, uengine.properties 파일을 수정한다.

uengine.properties에서 수정 되는 부분은 다음과 같다.
```
1. ###############		settings for process codi platform		###############
    => filesystem.path=/repository/filesystem =>  파일시스템의 경로를 의미한다.

2. ###############		database connectionfactory			###############
    => 해당 부분에 daofactory들이 있는데
daofactory.class=org.uengine.persistence.dao.MySQLDAOFactory 를 제외한 나머지 daofactory들은 모두 #을 붙여 주석처리를 해놓는다.

3. ###############		database connection				###############
    해당 부분에서 수정해야 할 부분은
    1) jdbc.driverClassName=com.mysql.jdbc.Driver 부분을 제외한 나머지 jdbc.driverClassName은 모두 #을 붙여 주석처리를 해놓는다.
    2) jdbc.url=jdbc:mysql로 시작되는 줄을 제외한 나머지 jdbc.url=jdbc:[db종류]는 #을 붙여 주석처리를 해놓는다.
    3) jdbc.url=jdbc:mysql://[DB접속 주소]:[DB포트]/[DB스키마 명]?useUnicode=true&amp;characterEncoding=UTF8 로 mysql 접속을 설정한다.
    4) 하단의 jdbc.username=[DB 접속 계정명] jdbc.password=[DB 접속 패스워드]를 설정한다.
4. 최하단의 Domain="processcodi.com"으로 작성 되어있는 부분을 수정하면 회원가입 확인 이메일 주소가 바뀐다.
```
***
<br>
### 7. applicationContext.xml 수정
Tomcat/webapp/ROOT/WEB-INF 경로로 이동하여, applicationContext.xml 파일을 수정한다.

applicationContext.xml에서 수정 되는 부분은 다음과 같다.
```
1. <!-- DataAccess --> 내용 안에 <!-- MySQL Data Source -->가 있다.
2. <property name="url" value="jdbc:mysql://[DB 접속 주소]:[DB 접속 포트]/[DB Schema 이름]?useUnicode=true&amp;characterEncoding=UTF8&amp;useOldAliasMetadataBehavior=true" /> 
3. <property name="username" value="DB 계정" />
4. <property name="password" value="DB 암호" />
5. 하위에 있는 CUBRID DATA Source는 사용하지 않으므로, <!-- -->로 주석이 되어있다.
```
***
<br>
### 8. Tomcat 실행
1~7단계를 모두 완료 하였다면, Tomcat을 실행한다.
```
Tomcat/bin 폴더로 이동한다.
1. Windows의 경우 startup.bat을 실행한다.
2. Linux의 경우, startup.sh을 실행한다.
2.1 Linux의 경우 콘솔창이 확인이 바로 되지 않으므로, Tomcat/logs 폴더로 이동 후, tail -f catalina.out을 입력하면 콘솔을 확인 할 수 있다.
```
***
<br>
### 9. Process Codi 접속
Tomcat이 정상적으로 실행되었다면 콘솔창에,
```
 Server startup in (00000) ms 와 같은 형식으로 작성된다.
```
서버가 정상적으로 실행되었다면, 브라우저에서 localhost:8080/으로 접속하면 된다.

계정은 새로 회원가입을 진행하여 로그인 하면 된다.
