(2022-04-24)
- entity, repository, member service 구현.
- subject service 구현중 addsubject기능에서 오류 발견(h2버전문제, 해결)


(2022-04-27)
- subject service의 addSubject, findSubject 구현 완료, 테스트코드 작성
- home화면 구현(thymeleaf, bootstrap)

![image](https://user-images.githubusercontent.com/68144687/165510362-96adf80e-cffb-4c30-884b-6b719c0d81d8.png)

- 회원등록 화면 및 기능 구현 

![image](https://user-images.githubusercontent.com/68144687/165510408-0db627a5-6c17-4e4d-9e1e-4cddf87e4581.png)

- 다음과 같은 오류 발생

![image](https://user-images.githubusercontent.com/68144687/165510435-e1e2d6f0-6c46-49c5-9200-8df3fcd38f0d.png)

(1) 클라이언트에서는 content-type default값인 application/x-www-form-urlencoded으로 보냈지만 apiController의 @RequestsBody를 통해 서버에서는 Json혹은 xml형태로 데이터를 받아서 객체에 mapping하려고 했기 때문

(2)해결 방법으로는 그냥 @RequestBody를 지워서 x-www-form-urlencoded형태로 주고 받으면 되지만 요즘 추세가 view를 분리시킴
(일단 application/x-www-form-urlencoded형태로 주고받는 코드와 json형태로 받는 apiController코드 둘다 짜놓음, 나중에 클라이언트에서 json형태로 데이터를 보내는 코드를 짜야할 필요 있음) 


(2022-04-28)
- 회원 목록 화면 구현 및 css

![image](https://user-images.githubusercontent.com/68144687/165752089-9acfa16d-4c66-46dc-b74f-8b0f6412ccb7.png)


![image](https://user-images.githubusercontent.com/68144687/165751022-739fd67b-1a6c-4501-b882-b069d7a4d7cb.png)
(경고창)
- login: contents를 볼수 있는 페이지로 넘어감, delete: 경고창이 나온 후 삭제됨

- login기능을 구현 할때 view에서 controller로 사용자의 데이터가 넘어가지 않았음, 자바스크립트 활용하여 해결

![image](https://user-images.githubusercontent.com/68144687/165751159-d8f4b8c4-e1ce-4445-982e-68c17e88d514.png)
![image](https://user-images.githubusercontent.com/68144687/165751172-492f5c17-2663-4feb-9a42-fbbf9cbda98b.png)


(2022-04-29)
- login클릭 후 과목 정보 출력 화면 구현

(요일별)

![image](https://user-images.githubusercontent.com/68144687/165972579-4475bf88-24d2-4914-85c7-1bfb7cc3eeca.png)

- 라디오 type에서 두번체크시 해제되는 기능 구현해야 함


(과목이름 별)

![image](https://user-images.githubusercontent.com/68144687/165972589-5c308984-b5de-4639-9690-5b182d5f1d09.png)


- QueryDsl과 mvc부분을 연습하고자 검색기능을 추가, 나중에 깔끔하게 요일별로만 바꿀 것
(querydsl코드: repository-SubjectRepositoryQuery)
- thymleaf부분에서 @ModelAttribute어노테이션의 활용과 form 태그를 이용해서 controller로 데이터를 전송하는 부분에서 시간을 많이 씀, 공부필요
- 회원 delete시 오류 발생 => 외래키문제, member엔티티에 CascadeType.All을 추가하여 해결


(2022-05-02)
- 과목 추가 기능 구현

(과목 추가 버튼)

![image](https://user-images.githubusercontent.com/68144687/166415218-55d4fc9d-8eb9-4887-9e7a-0afff9da6fc1.png)


(과목 추가 화면)

![image](https://user-images.githubusercontent.com/68144687/166415234-d862f60c-0127-4a4d-a621-dc3fbbfa8f0f.png)


(결과)

![image](https://user-images.githubusercontent.com/68144687/166415251-264abe3d-7a5a-44c0-b2cd-3c0156298423.png)


- 과목 추가 할시 과목 출력 화면으로 되돌아 오는데 member의 id값이 pathvariable로 넘어와야 함. 하지만 form태그에서 해결할 수 가 없어 고민을 하던중 자바스크립트로 해결
(/contents/show/52?)

![image](https://user-images.githubusercontent.com/68144687/166415758-69893c3b-5b6d-4639-925c-a2a50c029c9c.png)

(2022-05-05)
- review 리스트 내용 출력

![image](https://user-images.githubusercontent.com/68144687/167076411-a1188b27-0e7e-45f2-92d3-b9f3ce33c929.png)


- review 추가하기

![image](https://user-images.githubusercontent.com/68144687/167076418-665af3c0-1658-48a2-b86c-924b0f8e588f.png)

- 페이징 기법 적용하여, 순서대로 볼수있게 하자!
- 글쓰기, 저장버튼 위치 옮겨야함

(2022-05-07)
- 페이징 기법 적용하여 게시판 처럼 구현

![image](https://user-images.githubusercontent.com/68144687/167348709-c6bd3334-babd-4749-87df-562f42db4478.png)


- 글쓰기 저장, 목록 버튼 구현

![image](https://user-images.githubusercontent.com/68144687/167348715-a0a2144a-1933-4b1e-96c2-828c5c3a454b.png)


(~2022-05-11)
- 프로젝트 전체적인 기능 구현
- 스프링 시큐리티를 활용한 로그인 회원가입 기능 추가 


(~2022-05-16)
- 스프링 시큐리티를 활용한 회원가입, 로그인, 로그아웃 기능 구현 완료

![image](https://user-images.githubusercontent.com/68144687/168557026-4839c263-4330-4f25-8c35-e6da877ee3de.png)

(로그인 전)

![image](https://user-images.githubusercontent.com/68144687/168557103-306b9b58-0fd9-4fe5-9eb0-f7d999409bb7.png)

(로그인 화면)

![image](https://user-images.githubusercontent.com/68144687/168557139-cf450c1b-37f9-4f3f-9845-a274d3270551.png)

(로그인 후)


- AuthFailureHandler를 커스터마이징 하여 로그인 화면에서 오류 발생시 적절한 메시지 출력 기능 
- 전체적으로 정리 후 마무리 필요
