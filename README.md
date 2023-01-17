# docker_practice

도커를 통한 서버제작
-----------------------

사용할 DB: mysql, 작성기준 최신버전으로 사용했고 docker-compose에서 최신버전에 대한 표기를 사용했습니다.

```
docker-compose up -d
```

해당 명령어를 터미널을 통해 실행시키면 docker-compose파일에서 지정된 mysql image가 다운로드 되고 db가 열리는 것을 알 수 있습니다.
image가 정상적으로 다운됫는 지 확인하는 방법은 아래의 명령어를 실행해보면 알 수 있습니다.

```
 docker images
```

실행할때 자신이 실행햇던 이미지에 관한 내용이 존재한다면 도커 이미지를 받는것에 성공한 것입니다.

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

사용하고 싶은 컨테이너이름을 입력하여 자신이 쓰고싶은 컨테이너를 지정합니다. 저의 경우 docker start mysql을 통하여 컨테이너를 지정해줍니다.
혹시 디버깅에러가 난다면 포트가 열려있는 지 확인해보고 포트를 열고 다시한번 실행한다.
docker stop은 내가 컨테이너를 끄고 싶을 때 컨테이너를 종료하는 방법이다. 사용후 doker ps를 통해 꺼졋는지 확인해본다.
restart인경우는 재시작을 할때 쓰는 방법이다.

```
  docker exec -it [컨테이너이름] bash
```

컨테이너가 켜진 것을 확인한 후 컨테이너에 접근할 수 있습니다.
접속을하면 콘솔화면에서 mysql database가 나오게 됩니다.

```
CREATE database mydatabase;
SHOW database;
CREATE TABLE `mydatabase`.`client` (
  `client_id` CHAR(10) NOT NULL,
  `client_phonenum` CHAR(10) NOT NULL);
```

현재 데이터베이스에 아무런 파일이 없기때문에 db를 생성하고 db가 생성되엇는지 확인 후 db안에 하나의 테이블을 생성해보는 코드입니다.

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






