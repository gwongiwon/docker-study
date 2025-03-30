# docker-study
 docker 공부  기록

도커란?
---
컨테이너를 관리하기 위해 만들어진 소프트웨어이다. 그렇다면 컨테이너는 무엇일까 큰 서버를 나눠서 사용하기 위한 가상화라는 기술이다.

먼저, 도커를 이해하기 전에 서버와 가상화 기술이 무엇인지 그리고 왜 사용하는지에 대해서 공부하고자 한다.

서버는 무엇일까
서버는 하드웨어와 그 하드웨어에서 실행중인 소프트웨어까지 모드 포함하는 단어이다. 하드웨어만 있어도 서버이고 소프트웨어만 있어도 서버이기때문에
문맥에 따라 이해하면 된다.
클라이언트에 요청에 소프트웨어에 따라 결과값은 달라질리 몰라도 결과를 주는 근본적인 역할은 모든 서버가 동일한 이야기이다

서버는 크게 4가지로 나뉜다. 파일서버, DB서버, 웹서버(WEB) ,웹애플리케이션서버(WAS)

가상화 기술은 실제로 존재하는 컴퓨터가 아니지만 마치 존재하는 것처럼 만들어 주는 기술이다

앤터프라이즈 환경에서는 많은 양의 서버를 운영해야 하는데 크게 3가지로 방법이 나뉜다.
1. 베이멘탈
2. 하이퍼바이저
3. 컨테이너

여기서 하이버바이저와 컨테이너 방식이 가상화 기술을 적용한 서버 운영 방식이다.
각 방식에 대해 요약하자면 아래와 같다.

   <code>        하이퍼바이저 (VM)	    컨테이너 (Docker, Kubernetes)
실행 방식	각 VM마다 개별 OS 포함	       호스트 OS 공유 (경량)
성능	     OS 오버헤드 발생	              경량 & 빠름
격리 수준	    강한 보안 격리	            프로세스 수준 격리
사용 사례	서버 가상화 (기업, 클라우드)	 마이크로서비스, DevOps] </code>



컨테이너 가상화
---

컨테이너 가상화는 리눅스 커널이 제공하는 LXC라는 자체 격리 기술에서 출발했다

LXC기술은 커널의 네임스페이스와 CGroups라는 기능을 활용한다

네임스페이스는 리소스를 나누는 기준의 역할을 하고 CGroups는 리소스의 사용량을 배분하는 기술

컨테이너 가상화는 하이퍼바이저 없이 커널이 자체 기술을 활용한 가상화다.

컨테이너는 커널이 있는 HostOS 커널을 공유해서 사용하는데 컨테이너 가상화의 가장 중요한 특징 중 하나이다 . 그렇기 때문에 적은 오버헤드와 빠른 부팅이 가능하다

도커와 아키텍처는라는 소프트웨어는 이 커널의 컨테이너 가상화 기술을 편리하게 사용하기 위한 만들어진 소프트웨어이면 도커를 통해 컨테이너를 만들고 운영할 수 있다. 
도커는 이 커널의 가상화 기술을 활용할 수 있게 도와주는 보조 도구이다.

도커의 아키텍처
---

컨터이너 엔진과 컨테이너 런타임으로 구성돼있음

컨테이너 엔진은 사용자의 요청을 받아서 컨테이너를 관리해주는 역할을 하고 컨테이너 런타임(run c)을 직접 커널과 통신하면서 실제로 격리된 공간을 만드는 역할을 수행함

도커에도 사용자의 명령을 전달해주는 클라이언트와 실제로 컨테이너를 관리해주는 도커 데몬이 존재함

도커데몬은 컨테이너를 관리하는 기능을 제공하기 위해서 api를 클라이언트에게 줌
하지만 클라이언트가 매번 api양식에 맞게 작성하기 번거롭기 때문에 도커는 Docker CLI 라는 클라이언트 툴을 제공함 

일반적인 순서

1.클라이언트 명령어 실행
2.사용자 명령 api에 맞추어 변환
3.데몬에 api 요청
4.커널을 통해 컨테이너 리스트를 불러옴
5.json형태로 CLI로 넘겨줌
6.CLI는 클라이언트가 보기 좋게 테이블형태로 화면에 표시
7.정리하자면 도커는 클라이언트 서버 모델로 실행됨 클라이언트는 CLI, 서버는 도커 데몬으로 구성

