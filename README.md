# Time Line 개발

> 금도윤, 정상원, 제민욱

## 기술 스택

- Front
  - thyme-leaf
- Backend
  - Nginx
  - Redis
  - Hadoop / Casandra
  - Kafka
  - Spring-boot/ MVC / security / 
- DevOPs
  - Jenkins
  - Docker
  - AWS / Naver / TOAST



## 프로젝트 설명

>  TimeLine을 제공하여, 사용자들이 post를 공유할 수 있는 웹사이트를 제공한다.



### 기능

1. `Real Time`으로 TIme line에 `Post` 글들이 보여지도록 함.
2. 로그인 / 회원가입
3. 친구 추가 / 친구 목록 / 친구 허용

## 구현

1. `MSA` + `RESTful` + `Docker container`, `Cloud` 기반
2. 분산 네트워크 `load Balancing` 제공 및 무중단/ 테스팅 / 자동배포
3. 