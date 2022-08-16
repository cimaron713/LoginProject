# Spring Boot와 Spring Security

## 시작

spring Security를 이용하여 로그인을 구현하였다.

build.gradle 파일에 라이브러리 추가, [application.properties](http://application.properties) 에 내용 추가 후 실행 시 아래와 같은 로그인 페이지가 생성된다. 프로젝트내에 컨트롤러가 없기 때문에 로그인 성공 시, 에러 화면으로 자동으로 처리된다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/810a97a4-4863-475e-a724-266e5b18c21b/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71b16fc7-f319-4c72-882f-19b2d2087d2e/Untitled.png)

## PasswordEncoder

PasswordEncoder를 이용하여 패스워드를 인코딩 하였다. 패스워드를 암호화 하였다.

![인코딩 결과](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f72f82d1-8c26-40b3-aa01-c47d0a884962/Untitled.png)

인코딩 결과

## ClubMemberRepository

ClubUserDetailsService와 ClubMemberRepository을 연동하여 Member만 접근할 수 있는 기능을 구현하였다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/de9a0381-1926-4d4a-903e-5226b3350337/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fbda72f0-86b8-4973-b3e7-4a845eeedd71/Untitled.png)

## sec:authorize를 이용하여 인가와 관련된 정보를 알아내었다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/95acc339-d67f-4ae2-bba2-1074d138f0e9/Untitled.png)

## 구글 로그인

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/65ff3ffc-cee4-45d0-a5d6-e27fad676ab3/Untitled.png)

이후 구글 아이디를 통한 로그인 기능을 구현하였다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/79437067-237f-4378-88bb-4949f78ca641/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c210d755-77dc-47ff-9142-9723cfbecc4a/Untitled.png)

## Remeber me

자동로그인 기능을 구현하였다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2886d656-b4fb-4d13-a4d4-939750a7b0ef/Untitled.png)

# API 서버

### Note를 등록하는 기능

Yet Another REST Client 를 이용하여 REST 테스트를 하였다. 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7ed14ebd-24f4-45f5-a7b7-c5f00a32cfb7/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0583f0c1-fe46-4f06-99ff-01777dbd7782/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/926deb9e-8507-4d93-86f8-014d7d32343d/Untitled.png)

### 특정 회원의 모든 Note 확인

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7266e569-9a28-4852-a20f-77480ce80cd4/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c1e14fef-b6eb-4f21-8089-867668049b97/Untitled.png)

### Note 수정 기능

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f7d7b41b-3372-48cd-a090-15c7915b2b71/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/65f0f131-e758-4e37-b7ba-30aee2a9427a/Untitled.png)

## Authorization 헤더

API를 호출하는 경우 Request를 전송할 때 Http 헤더 메시지에 특별한 값을 지정해서 전송한다. Authorization 헤더는 이러한 용도로 사용한다. 전과 같이 Yet Another REST Client를 통해 테스트 하였다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/20463505-cb9a-41d6-9de3-06d8e6d8846b/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4a45d143-c6a9-4de5-b619-a0523a29ae83/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/becd52a5-5bc4-498c-9788-cdd6520488a7/Untitled.png)

Authorization가 없거나 다른 값을 전송하면 오류가 발생하는 것을 확인할 수 있다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd40e36c-410b-4664-8791-681f41749111/Untitled.png)

## UsernamePasswordAuthenticationToken

UsernamePasswordAuthenticationToken을 이용해 사용자 인증을 진행하였다.

http://localhost:8080/api/login?email=user95@zerock.org&pw=1111

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be7adbfb-46a5-477d-aa52-07c3f757a32d/Untitled.png)

인증에 실패한 경우 아래와 같다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c805260-7103-4c2b-92e7-e47f8051dba3/Untitled.png)

## JWTUtil

인증 성공 후, API를 호출할 때 사용할 적절한 데이터를 만들어서 전송해주어야 한다. 여기서 JWT를 이용한다. 인증성공 → JWT 전송 → API 호출 → 문자열 읽기

기능을 구현하여 전과 같이 테스트 하였다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/690ee9f0-916c-400b-a6a4-9972cce2af33/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/205bb897-4a50-4d83-9946-ccb7ddbbad0f/Untitled.png)
