## ch3.연습문제

---

- **도커 허브에 공유된 `diamol/ch03-lab` 이미지가 있으며, 해당 이미지 안에는 `/diamol/ch03.txt` 파일이 존재함(빈파일)**
    - 해당 파일에 Elton 이름을 추가한 다음, 수정된 파일을 새로운 도커 이미지를 만들고 빌드하기

**힌트**
- **`-it`플래그를 사용하면 컨테이너를 대화식으로 실행할 수 있음**
- **파일 시스템의 컨테이너는 컨테이너가 종료된 후에 남아 있음**
- **`docker container —-help` 명령으로 해당 과제를 수행함**

<br/>

### 문제 풀이
1. 도커 허브에서 이미지를 다운받기
``` bash
docker pull diamol/ch03-lab
```

2. 다운받은 도커 이미지로 도커 컨테이너 생성하기
``` bash
docker container run -it --name ch03-lab diamol/ch03-lab 
```

3. 도커 컨테이너의 /diamol/ch03.txt 파일 
``` bash
echo Elton >> /diamol/ch03.txt
```

4. 컨테이너 대화 모드 종료
``` bash
exit 
```

5. 새로운 도커 이미지 생성
- 현재 실행 중인 컨테이너를 도커 이미지로 저장함
``` bash
docker image commit ch03-lab before-ch03-lab  
```

6. 새로 생성된 도커의 이미지 확인하기
``` bash
docker image ls | grep before-ch03-lab 
```