# Lock


session1 : insert 1111 : lock_mode S  
session2 : insert 1111 : lock_mode X : lock_waits -> insert구문 exclusive lock(X)  
session3 : insert 1111 : lock_mode S : lock_waits -> insert구문 duplicate 체크 -> duplicate 에러 shared lock 먼저 시도  

<br>

## Lock 종류
Shared Lock(S) : select
Exclusive Lock(X) : insert/update/delete -> S락에도 적용됨

<br>

## Lock 단위

Lock 단위| 설명
----|---
RID     | 행
KEY     | 인덱스 있을 때 행
PAGE    | 데이터 페이지, 인덱스 페이지
EXTENT  |
TABLE   |
DB      |

<br>

## Transaction Isolation level (잠금 수준)
Read uncommitted < read committed < repeatable read < serializble

<br>

## Blocking 경합
특정 세션이 작업을 진행하지 못하고 멈춘 상태 -> transaction commit 또는 rollback  
동일한 데이터 동시 변경하지 않도록 설계  
lock timeout 설정.  

<br>

## Dead Lock
트랜젝션 교착관계  
1번 트랜젝션, 2번 트랜젝션 동시에 상대방의 로우에 접근하려고 할 때...  
1번 트랜잭션 shared lock -> sleep / 2번 E lock 설정하려고 할 때... 무기한 교착상태.  

<br><br>
---
### 📌참고
https://blog.naver.com/happ141218/222464761103    
https://battleracoon.tistory.com/2  
https://chrisjune-13837.medium.com/db-lock-%EB%9D%BD%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-d908296d0279  
https://blog.naver.com/dnjswls23/222682435541  
https://blog.naver.com/kkkkkkya/221593875245https://myinfrabox.tistory.com/72  
  
os lock  
https://hoyeonkim795.github.io/posts/%EA%B5%90%EC%B0%A9%EC%83%81%ED%83%9C%EC%9D%98-%EA%B0%9C%EB%85%90%EA%B3%BC-%EB%B0%9C%EC%83%9D%EC%9B%90%EC%9D%B8/  

