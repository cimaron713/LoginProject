# Spring Boot와 Spring Security

## 시작

spring Security를 이용하여 로그인을 구현하였다.

build.gradle 파일에 라이브러리 추가, [application.properties](http://application.properties) 에 내용 추가 후 실행 시 아래와 같은 로그인 페이지가 생성된다. 프로젝트내에 컨트롤러가 없기 때문에 로그인 성공 시, 에러 화면으로 자동으로 처리된다.

![image](https://user-images.githubusercontent.com/109207727/184841979-f40191a3-25fd-4967-b1c0-cdca1ace7c52.png)


## PasswordEncoder

PasswordEncoder를 이용하여 패스워드를 인코딩 하였다. 패스워드를 암호화 하였다.

![image](https://user-images.githubusercontent.com/109207727/184842036-c7e10a65-8668-4d46-b981-1662d417d9f1.png)


## ClubMemberRepository

ClubUserDetailsService와 ClubMemberRepository을 연동하여 Member만 접근할 수 있는 기능을 구현하였다.

![image](https://user-images.githubusercontent.com/109207727/184842126-b5be5f6e-0d6a-4941-9111-19b387f2e6b1.png)

## sec:authorize를 이용하여 인가와 관련된 정보를 알아내었다.

![image](https://user-images.githubusercontent.com/109207727/184842171-1063626f-4e12-41b2-9a0c-df6853d671d7.png)

## 구글 로그인

![image](https://user-images.githubusercontent.com/109207727/184842276-2d89a2de-4dd6-4328-b594-770d4ad06f10.png)

![image](https://user-images.githubusercontent.com/109207727/184842306-e658d326-26be-4088-8fd9-f352742e93d1.png)


이후 구글 아이디를 통한 로그인 기능을 구현하였다.

![image](https://user-images.githubusercontent.com/109207727/184842349-9163daba-1318-4de4-8392-85b59ded4580.png)

## Remeber me

자동로그인 기능을 구현하였다.

![image](https://user-images.githubusercontent.com/109207727/184842380-bfaeeea3-66fc-4a78-9faa-c2ac3b0007e8.png)

# API 서버

### Note를 등록하는 기능

Yet Another REST Client 를 이용하여 REST 테스트를 하였다. 

![image](https://user-images.githubusercontent.com/109207727/184842417-add07940-3d95-413c-8c74-75031c281666.png)

### 특정 회원의 모든 Note 확인

![image](https://user-images.githubusercontent.com/109207727/184842473-06a06e66-1f2c-4e75-a4fb-d21c4803326c.png)

### Note 수정 기능

![image](https://user-images.githubusercontent.com/109207727/184842525-a2f6d805-bf8e-4485-9f4d-ec80f50d1ccb.png)

## Authorization 헤더

API를 호출하는 경우 Request를 전송할 때 Http 헤더 메시지에 특별한 값을 지정해서 전송한다. Authorization 헤더는 이러한 용도로 사용한다. 전과 같이 Yet Another REST Client를 통해 테스트 하였다.
![image](https://user-images.githubusercontent.com/109207727/184842570-cdf8f237-c16c-45ac-82de-6f0894cbb56b.png)

Authorization가 없거나 다른 값을 전송하면 오류가 발생하는 것을 확인할 수 있다.

![image](https://user-images.githubusercontent.com/109207727/184842616-be09d95f-8cf2-4cfd-82d6-38efc573ef37.png)

## UsernamePasswordAuthenticationToken

UsernamePasswordAuthenticationToken을 이용해 사용자 인증을 진행하였다.

http://localhost:8080/api/login?email=user95@zerock.org&pw=1111

![image](https://user-images.githubusercontent.com/109207727/184842647-af7e7777-294e-4b0d-a205-9fc3463817f0.png)

인증에 실패한 경우 아래와 같다.

![image](https://user-images.githubusercontent.com/109207727/184842679-ec76c47d-674c-491d-9b44-7859aa061383.png)

## JWTUtil

인증 성공 후, API를 호출할 때 사용할 적절한 데이터를 만들어서 전송해주어야 한다. 여기서 JWT를 이용한다. 인증성공 → JWT 전송 → API 호출 → 문자열 읽기

기능을 구현하여 전과 같이 테스트 하였다.
![image](https://user-images.githubusercontent.com/109207727/184842726-dee85574-e5b0-4407-a4c8-37d28a98b473.png)
