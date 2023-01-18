# docker_practice

도커를 활용한 서버제작
-----------------------


도커란 무엇인가?
소프트웨어 컨테이너 클라우드 서비스

그렇다면 컨테이너는 무엇인가?
HW 가상화를 제공하는 VM과 달리 컨테이너는 사용자 공간을 추상화함으로써 경량의 운영체제 수준의 가상화를 제공하는 환경입니다.
컨테이너는 영구적이지 않고 그 안에 이미지로부터 생성됩니다.

컨테이너 이미지는?
컨테이너로 실행될 SW모음집입니다. 저의 경우 MYSQL이 도커 이미지입니다.


사용할 DB: mysql, 작성기준 최신버전으로 사용했고 docker-compose에서 최신버전에 대한 표기를 사용했습니다.
```
docker-compose up -d
```

해당 명령어를 .yml파일이 들어있는 곳에서 커맨드로 실행시키면 docker-compose파일에서 지정된 mysql image가 다운로드 되고 docker서버가 running상태가 된 것을 확인 할 수 있다.
docker를 통하여 컨테이너가 활성화된 것을 볼 수 있다. restarting이 계속 진행된다면 detail항목을 통하여 어느 부분에서 에러가 뜨고 돌아가지 않는 지에 대하여 수정하여야 한다.
-d의 경우 백그라운드에서 진

```
 docker images
```

실행할때 자신이 실행햇던 이미지에 관한 내용이 존재한다면 도커 이미지를 받는것에 성공한 것입니다.

```
docker imgaes tag mysql:latest[레지스토리 이름:버전] [유저이름/이미지 이름:버전]
docker push [유저이름/이미지 이름:버전] #[]안은 생성했던 태그
```

docker허브에서 image를 push하기 위하여 tag이름을 바꿔주고 난후 push를 통해 docker hub에 image를 올리는 경우입니다.

```
docker login
docker info| grep Username
```

만약 도커 허브에 올라가지 않는다면 로그인 상태를 확인해보면됩니다.
첫번째는 도커를 로그인 하는 방법이고 두번째는 로그인 상태를 확인하는 명령어입니다.
로그인을 할 경우에는 자신의 도커허브의 username과 password를 입력하면 됩니다.


```
 docker ps 
 docker ps -a
```

각각 두 명령어는 현재 실행중인 컨테이너를 조회하고 컨테이너 전체를 조회하는 명령어입니다.


```
 docker start [컨테이너이름]
 docker stop [컨테이너이름]
 docker restart [컨테이너이름]
```

사용하고 싶은 컨테이너이름을 입력하여 자신이 쓰고싶은 컨테이너를 지정합니다.
제가 사용한 docker compose 파일의 경우 restart:always가 되어 있기때문에 가동중인 상태이기때문에 이러한 명령어가 있다는 것만 짚고 넘어가겠습니다.
docker stop은 내가 컨테이너를 끄고 싶을 때 컨테이너를 종료하는 방법입니다. 사용후 doker ps를 통해 꺼졋는지 확인해봅니다.
restart인경우는 재시작을 할때 쓰는 방법입니다.

```
  docker exec -it [컨테이너이름] bash
```

컨테이너가 켜진 것을 확인한 후 컨테이너에 접근할 수 있습니다.
#bash

```
mysql -u root -p
```
해당 명령어를 입력후 기존에 설정해둔 root비밀번호를 입력해주면 mysql에 성공적으로 접속할 수 있습니다

```
CREATE database mydatabase;
SHOW mydatabase;
CREATE TABLE `mydatabase`.`client` (
  `client_id` CHAR(10) NOT NULL,
  `client_phonenum` CHAR(10) NOT NULL);
```

현재 데이터베이스에 아무런 파일이 없기때문에 db를 생성하고 db가 생성되엇는지 확인 후 db안에 하나의 테이블을 생성해보는 코드입니다.
생성된 테이블을 mysql을 통해 확인해봄으로써 연동을 확인해봅니다.

```
INSERT INTO client(client_id,client_phonenum)VALUES('고객','01000000000');
SELECT*FROM mydatabase.client;
```

이제 테이블이 생성되고 그 안에 데이터들을 넣고 확인해보는 코드이다.

```
DELETE FROM client;
SEECT *FROM mydatabase.client;
```

테이블 생성이 확인까지 완료후에 데이터들이 삭제가 되는지 확인해보는 코드이다.

--------------------------------------






