## ch2. 연습문제

---

- **앞서 실행했던 웹 사이트 컨테이너를 실행하고, `index.html` 파일을 교체하여 웹 페이지의 내용을 수정함**

**힌트**

1. **`docker container` 명령을 사용하여 컨테이너를 대상으로 할 수 있는 일의 목록을 볼 수 있음**
2. **모든 `docker` 명령에 `—-help` 옵션을 통해 도움말을 참고함**
3. **도커 이미지 `diamol/ch02-hello-diamol-web`안의 웹 페이지가 위치한 경로는 `/usr/local/apach2/htdocs`로 설정**


<br/>

### 문제 풀이
1. hello-diamol-web 컨테이너 실행
``` bash
docker container run --detach --publish 8088:80 diamol/ch02-hello-diamol-web
```

2. 실행 중인 도커 컨테이너에서의 index.html 파일이 존재하는지 확인하기
``` bash
docker container exec <컨테이너ID> ls /usr/local/apach2/htdocs/index.html
```

3. 연습문제로 주어진 변경된 index.html을 도커 컨테이너에 복사하기
- 변경된 index.html파일이 존재한 위치로 이동 or 절대 경로를 이용하기
``` bash
docker container cp index.html /usr/local/apach2/htdocs/index.html
```

4. 새로고침을 통해 변경된 도커 컨테이너의 index.html 파일 확인하기

``` http request
http://localhost:8088/
```