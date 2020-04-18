# 도커 엔진

## 도커 이미지와 컨테이너

- 도커 엔진에서 사용하는 기본 단위는 이미지와 컨테이너이며, 이 두 가지가 도커 엔진의 핵심 요소



### 도커 이미지

- 컨테이너 생성시 필수 요소 - 가상 머신 생성할 때 사용하는 iso 파일과 비슷한 개념
- 이미지는 도커 명령어로 내려 받을 수 있으므로 별도로 설치 필요 X



##### 형태

- \[저장소 이름]/\[이미지 이름]:\[태그]
- 예: ericj079/ubuntu:14.04 혹은 ubuntu/latest

#### 종류

- 운영체제
  - Ubuntu, CentOS
- 웹서버
  - Apache
- 데이터베이스
  - MySQL Database
- 빅 데이터 분석 도구 등
  - Hadoop, Spark, Storm

### 도커 컨테이너

- 이미지의 목적에 맞는 파일이 들어 있는 파일시스템과 격리된 시스템 자원 및 네트워크를 사용할 수 있는 독립된 공간
- 컨테이너는 이미지에서 변경된 사항만 컨테이너 계층에 저장하므로 컨테이너에서 무엇을 하든지 원래 이미지는 영향을 받지 않는다



## 도커 컨테이너 다루기

### 도커 GUI

- 도커를 편하게 쓰기 위해 GUI를 지원하는 Kitematic 이라는 도구가 있다. 그러나 CLI를 쓰는 방법은 모든 OS 상 (Windows, Mac OS X, Linux)에서 모두 동일하기 때문에 CLI를 배워두는 것이 좋다.  

### 컨테이너 생성

- 버전 확인 `docker -v`

- 컨테이너 내려받기, 생성, 시작, 접속을 단 한번의 커멘드로 실행 가능 `docker run -i -t ubuntu:10.04`
  - -i : 컨테이너와 상호 입출력 가능하게 함
  - -t : tty를 활성화 하여 bash shell을 사용하도록 컨테이너 설정
- 컨테이너 종료
  - 컨테이너 정지 및 종료 `(도커 셸 내부에서) exit` 혹은 `ctrl + D`
  - 컨테이너 정지하지 않고 종료 `ctrl + P, Q`
- 이미지 내려받기
  - docker pull centos:7
- 도커 엔진에 존재하는 이미지 목록 출력
  - docker images
- 컨테이너 생성
  - docker create -i -t --name mycentos centos:7
- 컨테이너 시작
  - docker start mycentos
- 컨테이너 내부로 접속
  - docker attach mycentos
- 컨테이너 목록 확인
  - docker ps
    - 정지되지 않은, 실행 중인 컨테이너만 출력
    - -a 옵션은 정지된 컨테이너를 포함한 모든 컨테이너 출력
- docker ps 명령어의 출력에 대한 설명
  - CONTAINER ID : 고유 ID 
    -  `docker insepct mycentos | grep Id`  이 명령어를 통해 전체 ID 확인 가능
  - COMMAND : 컨테이너가 시작될 때 실행될 명령어
    - /bin/bash 명령어가 실행되어 상호 입축력이 가능항 shell 환경이 사용 가능 했던 것
  - STATUS: 컨테이너의 상태
    - UP - 컨테이너 실행 중
    - EXITED - 종료된 상태
    - PAUSE - 일시 중지된 상태
  - NAME: 컨테이너의 고유한 이름
    - 컨테이너 생성시 --name 옵션으로 이름을 설정하지 않으면 도커 엔진이 임의로 형용사와 명사를 무작위로 조합하여 이름 설정
    - docker rename 명령어를 사용하여 컨테이너의 이름을 변경할 수 있음
    - 예: `docker rename angry_cat big_container`

### 컨테이너 삭제

- docker rm container_name
- 실행 중인 컨테이너 삭제 시 에러
  - `Stop the container before attepting removal or force remove`
- 실행 중인 컨테이너 정지 후 삭제
  - `docker stop container_name`
  - `docker stop container_name`
- 강제 삭제
  - `docker rm -f mycentos`
- 모든 컨테이너 삭제
  - `docker container prune`
- docker ps 명령어의 -a 옵션 (존재하는 모든 컨테이너)과 -q 옵션 (컨테이너의 ID만) 조합하여 컨테이너 삭제 가능
  - `docker ps -a -q` => 존재하는 모든 도커 컨테이너의 아이디 출력
  - `$(docker ps -a -q)` 출력된 컨테이너 리스트를 변수로 사용
  - `docker stop $(docker ps -a -q)`
  - `docker rm $(docker ps -a -q)`

### 컨테이너를 외부에 노출

- 컨테이너는 가상머신과 마찬가지로 가상 IP 주소를 할당 받는다.

- 기본적으로 도커는 컨테이너에 172.17.0.x 의 IP를 순차적으로 할당받는다.

- 컨테이너의 내부에서 `ifconfig` 명령어로 컨테이너의 네트워크 인터페이스를 확인 할 수 있다.

  ```
  root@e60ac551e0aa:/# ifconfig
  eth0      Link encap:Ethernet  HWaddr 02:42:ac:11:00:02
            inet addr:172.17.0.2  Bcast:172.17.255.255  Mask:255.255.0.0
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:12 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:976 (976.0 B)  TX bytes:0 (0.0 B)
  
  lo        Link encap:Local Loopback
            inet addr:127.0.0.1  Mask:255.0.0.0
            UP LOOPBACK RUNNING  MTU:65536  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  ```

- 도커의 NAT IP 인 17.17.0.2를 할당받은 eth0 인터페이스와 로컬호스트인 lo 인터페이스가 있다. 아무런 설정을 하지 않았다면 이 컨테이너는 외부에서 접근할 수 없으며 도커가 설치된 호스트에서만 접근할 수 있다. 외부에 컨테이너의 애플리케이션을 노출하기 위해서는 eth0의 IP와 포트를 호스트의 IP와 포트에 바인딩해야 한다.

- `docker run -i -t --name mywebserver -p 80:80 ubuntu:14.04`

- 이 컨테이너에 아파치 웹 서버를 설치해야 함.

- -p 옵션은 컨테이너의 포트를 호스트의 포트와 바인딩해 연결할 수 있게 설정한다. (ex: [호스트포트]:[컨테이너 포트])

- -p 옵션을 여러번 사용사여 여러 개의 포트를 외부에 가능하는 것도 가능하다.

- 아파치 웹서버는 기본적으로 80번 포트를 사용하므로 컨테이너의 80번 포트를 호스트와 연결한다.

- 컨테이너 내부로 들어와서 패키지 매니저를 업데이트하고 아파치를 설치하고 실행한다

  ```
  apt-get update
  apt-get install apache2 -y
  service apache2 start
  ```

- 호스트의 브라우저를 통해 [호스트 IP]:80 으로 접속하여 apache 실행을 확인한다.

### 컨테이너 어플리케이션 구축