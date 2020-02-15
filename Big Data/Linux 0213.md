## [빅데이터 플랫폼 구축을 위한 순서]

**실제 여러 대의 서버가 클러스터링 설정이 되어 있어야 하나 우리는 그냥 가상머신을 설치하여 작업한다.**

**플렛폼을 구축하기 위한 준비과정은 다음과 같다.**

  **1. vmware 설치**

  **2. vmware 가상머신 설치하기 - CentOS 7버전을 설치한다.**

  **3. 가상머신 복제하기**

​     **- 가상머신이 네 대 있다 가정하고 네 개의 가상머신을 만들어준다.**

​     **: ip확인**

  **4. 하둡 서버를 구축하기 위한 클러스터링 설정하기** ( 머신 4대 클러스터링)

* **방화벽해제**

* **네트워크 설정**

* **DNS설정** (도메인)

  * hosts 파일 등록

  * 네트워크 프로세스를 restart

  * 설정 확인 - 설정을 성공 완료했는지 확인

  * 4대에 모두 적용되도록 hadoop01머신에서 hadoop02,03,04에 직접 접속

    * [원격 서버로 copy]
    * scp copy할 파일 (위치까지 명시) copy받을 서버의 위치
    * scp /etc/hosts root@hadoop02 :/etc/hosts               -계정으로 접근, 반드시 대상까지 명시

    ```linux
    scp 		/etc/hosts 			root@hadoop02 :/etc/hosts
    ---			----------		   	------------------------
    명령어		   copy할 파일			 target서버의 위치와 파일명
    ```

    * [원격 서버에 실행 명령]

    ```linux
    ssh 서버 "실행할 명령문"
    	---
    	ip 도메인
    ```

    

  **5. 각종 프로그램 설치**

​     **- SSH 프로토콜 설정**

​     **- hadoop을 테스트하기 위해서는 자바가 반드시 필요하므로**

​     **- java, hadoop을 설치하고 설정을 한 후 테스트한다.**

  **6. hadoop의 EchoSystem을 살펴보고 EchoSystem을 설치하여 테스트한다.**

### 클러스터링 ?

*  **컴퓨터 컬러스터**는 여러 대의 컴퓨터들이 연결되어 하나의 시스템처럼 동작하는 컴퓨터들의 집합을 말한다.

웹서버 클러스터는 각기 다른 종류의 요구들을 각기 다른 노드에서 처리하도록 할당함으로써 전반적인 응답시간을 최소화 할 수 있다.

즉, **여러 대를 묶어서 처리**하는 것을 말한다.

우리는 가상머신 4대를 하나의 하둡 서버인것 처럼 사용할 것이다.

- 4대가 서로 통신해야하니까 방화벽을 해제해야 한다.
- 각 4대가 고유의 IP를 갖고 있어야 할 것이다.

![image-20200212114455447](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200212114455447.png)

* **Host-only** : 가상머신끼리 통신 가능
  * guestPC들끼리 통신하게 만든다.
  * HOST는 공유기를 통해 인터넷에 접근
* **NAT**
  * guest랑 HOST 모두 공유기를 통해 인터넷에 접근
  * GUEST를 HOST인것 처럼 사용

<pre>[root@hadoop01 ~]# rpm -Uvh jdk-8u231-linux-x64.rpm 
경고: jdk-8u231-linux-x64.rpm: Header V3 RSA/SHA256 Signature, key ID ec551f03: NOKEY
준비 중...                         ################################# [100%]
Updating / installing...
   1:jdk1.8-2000:1.8.0_231-fcs        ################################# [100%]
Unpacking JAR files...
	tools.jar...
	plugin.jar...
	javaws.jar...
	deploy.jar...
	rt.jar...
	jsse.jar...
	charsets.jar...
	localedata.jar...
</pre>



> rpm -Uv**h** : 프로그레스 바를 의미한다.
>
> ​		   	**v**:화면에 보여주겠다는 의미

![image-20200213103621700](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213103621700.png)


원격 설치

<pre>[root@hadoop01 ~]# ssh hadoop02 &quot;rpm -Uvh jdk-8u231-linux-x64.rpm&quot; 
</pre>



## 하둡 설치

![image-20200213111302444](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213111302444.png)

빅데이터 프로그램 : 하둡, 하이브, h베이스



![image-20200213111832505](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213111832505.png)

루트권한이 계속 남아있는 것을 방지해주어야 한다.

* home으로 이동해준다. 

<pre>[root@hadoop01 ~]# scp hadoop-1.2.1.tar.gz  hadoop@hadoop01:/home/hadoop/
The authenticity of host &apos;hadoop01 (192.168.111.128)&apos; can&apos;t be established.
ECDSA key fingerprint is SHA256:zb01S55iZv9KZOAAFxhnnzpHFvVAbat/noTieUv7zYI.
ECDSA key fingerprint is MD5:0d:45:b0:d5:de:b6:3c:67:84:61:ea:71:fc:68:00:8e.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added &apos;hadoop01,192.168.111.128&apos; (ECDSA) to the list of known hosts.
hadoop@hadoop01&apos;s password: 
hadoop-1.2.1.tar.gz                           100%   61MB  48.3MB/s   00:01    
</pre>

*

<pre>[root@hadoop01 ~]# su hadoop
[hadoop@hadoop01 root]$ cd ~ 
[hadoop@hadoop01 ~]$ ls
<font color="#EF2929">hadoop-1.2.1.tar.gz</font>  <font color="#005FFF">test</font>
</pre>



![image-20200213112207698](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213112207698.png)

명렁어를 통해서 복사한 것이기 때문에 hadoop 계정이 된다.

* 파일 압축 풀기

<pre>[hadoop@hadoop01 ~]$ tar -zxvf hadoop-1.2.1.tar.gz 
</pre>

![image-20200213113423054](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213113423054.png)

*  다른 hadoop 머신에 복사

<pre>[hadoop@hadoop01 ~]$ scp /home/hadoop/hadoop-1.2.1.tar.gz  hadoop@hadoop02:/home/hadoop/
</pre>

![image-20200213114356260](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213114356260.png)

![image-20200213114422644](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213114422644.png)

jar 파일은 hadoop의 라이브러리

conf 는 설정파일

![image-20200213114542340](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213114542340.png)

![image-20200213133242894](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213133242894.png)

![image-20200213133728352](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213133728352.png)

* 임시 디렉토리 만들기



![image-20200213134023723](C:/Users/sec/Desktop/TiL/Big Data/images/image-20200213134023723.png)


<pre>[hadoop@hadoop01 ~]$ scp /home/hadoop/hadoop-1.2.1/conf/* hadoop@hadoop04:/home/hadoop/hadoop-1.2.1/conf
</pre>

<pre>[hadoop@hadoop01 ~]$ /home/hadoop/hadoop-1.2.1/bin/hadoop namenode -format
</pre>

<pre>[hadoop@hadoop01 ~]$ /home/hadoop/hadoop-1.2.1/bin/start-all.sh
</pre>

[hadoop@hadoop01 ~]$ /home/hadoop/hadoop-1.2.1/bin/stop-all.sh

<pre>[hadoop@hadoop01 ~]$ scp /home/hadoop/hadoop-1.2.1/conf/* hadoop@hadoop04:/home/hadoop/hadoop-1.2.1/conf
</pre>