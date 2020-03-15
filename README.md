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

### 개발 원칙


#### DDD


- Aggregate vs Lazy_loading
> 유저가 자신의 타임라인에 글을 올리는 경우를 생각해봅시다. User Aggregate 가 해당 유저에 대한 모든 글 목록을 가지고 있고 모든 글에 대한 추가/삭제/수정 요청을 처리한다고 하더라도 동시성에는 문제가 없습니다. (한 유저가 여러개의 디바이스를 통해 동시다발적으로 글을 작성하진 않을 것이므로) 하지만 이렇게 되면 User Aggregate 를 로딩할 때마다 모든 글 목록을 같이 불러와야해서 매우 비효율적이고 메모리도 많이 소모하게 됩니다. 따라서 이건 좋은 Aggregate 설계가 아닙니다. 해결책은 유저의 글 각각을 별도의 Aggregate 로 분리하는 것입니다. 이렇게 되면 Aggregate 하나하나가 작은 크기를 유지하기 때문에 Aggregate 로딩이 효율적이고 메모리도 적게 소모하게 됩니다. Aggregate 를 쪼개지 않고서 할 수 있는 다른 방법은 Lazy Loading 을 활용하는 것입니다. User Aggregate 가 로딩될 때 모든 글 목록을 같이 로딩 (eager loading) 하는게 아니라 주어진 요청을 처리하는데 필요한 글들만 로딩하는 것입니다. 보통 Aggregate 를 분리하는게 DDD 정론(?) 에 부합하는 방법이긴 하지만, Aggregate 를 분리하면 여러가지 제약사항들 (트랜잭션 경계, eventual consistency 등) 이 생기고 개발이 더 복잡해질 수 있기 때문에 경우에 따라 선택은 달라질 수 있다고 생각합니다. [출처](https://www.secmem.org/blog/2020/02/19/ddd-aggregate-pattern/)

- 복잡한 Aggregate 설계는 `Lazy_loading`으로 대체하고, 간단한 로직은 Aggregate 생명주기 관리를 위해 `Cascade`을 활용한다.