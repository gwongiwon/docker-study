# docker-study
 docker 공부  기록

도커란?
컨테이너를 관리하기 위해 만들어진 소프트웨어이다. 그렇다면 컨테이너는 무엇일까 큰 서버를 나눠서 사용하기 위한 가상화라는 기술이다.

먼저, 도커를 이해하기 전에 서버와 가상화 기술이 무엇인지 그리고 왜 사용하는지에 대해서 공부하고자 한다.

서버는 무엇일까
서버는 하드웨어와 그 하드웨어에서 실행중인 소프트웨어까지 모드 포함하는 단어이다. 하드웨어만 있어도 서버이고 소프트웨어만 있어도 서버이기때문에
문맥에 따라 이해하면 된다.
클라이언트에 요청에 소프트웨어에 따라 결과값은 달라질리 몰라도 결과를 주는 근본적인 역할은 모든 서버가 동일한 이야기이다

서버는 크게 4가지로 나뉜다. 파일서버, DB서버, 웹서버(WEB) ,웹애플리케이션서버(WAS)


앤터프라이즈 환경에서는 많은 양의 서버를 운영해야 하는데 크게 3가지로 방법이 나뉜다.
1. 베이멘탈
2. 하이퍼바이저
3. 컨테이너