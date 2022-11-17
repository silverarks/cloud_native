# docker_practice

도커를 통한 서버제작
-----------------------

사용할 DB: mysql, 작성기준 최신버전으로 사용했고 docker-compose에서 최신버전에 대한 표기를 사용했습니다.

```
docker-compose up -d
```

해당 명령어를 터미널을 통해 실행시키면 docker-compose파일에서 지정된 mysql image가 다운로드 되고 db가 열리는 것을 알 수 있다.
image가 정상적으로 다운됫는 지 확인하는 방법은 아래의 명령어를 실행해보면 알 수 있다.

```
 docker images
```

실행할때 자신이 실행햇던 이미지에 관한 내용이 존재한다면 도커 이미지를 받는것에 성공한 것이다.

```
 docker ps 
 docker ps -a
```

각각 두 명령어는 현재 실행중인 컨테이너를 조회하고 컨테이너 전체를 조회하는 명령어이다.


