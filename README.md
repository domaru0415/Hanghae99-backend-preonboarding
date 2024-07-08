![spartacodingclub](https://noticon-static.tammolo.com/dgggcrkxq/image/upload/v1719643111/noticon/yeqwdeuiybor5m4hh7zj.png)
# Hanghae99 Preonboarding Backend Course

**취업시장에 침투하기 전에, 실전과 같은 훈련으로 코딩의 감(떫음)을 찾아서 세상에 스파르타st를 보여주자.<br />
어렵다고 느끼는 제군들도 있겠지만, 힌트를 보면서 잘 따라 와주기를 바란다.**



### 🎖️ 훈련 메뉴

---
- [ ]  Junit를 이용한 테스트 코드 작성법 이해
- [ ]  Spring Security를 이용한 Filter에 대한 이해
- [ ]  JWT와 구체적인 알고리즘의 이해
- [ ]  PR 날려보기
- [ ]  리뷰 바탕으로 개선하기
- [ ]  EC2에 배포해보기

### Day 1 - 시나리오 설계 및 코딩 시작!

---
**Spring Security 기본 이해**

- [ ]  Filter란 무엇인가?(with Interceptor, AOP)
 1. Filter(필터)
말그대로 요청과 응답을 거른뒤 정제하는 역할을 한다
서블릿 필터는 DispatcherServlet 이전에 실행이 되는데 필터가 동작하도록 지정된 자원의 앞단에서 요청내용을 변경하거나,  여러가지 체크를 수행할 수 있다
또한 자원의 처리가 끝난 후 응답내용에 대해서도 변경하는 처리를 할 수가 있다
보통 web.xml에 등록하고, 일반적으로 인코딩 변환 처리, XSS방어 등의 요청에 대한 처리로 사용된다
 2. Interceptor(인터셉터)
요청에 대한 작업 전/후로 가로챈다고 보면 된다
필터는 스프링 컨텍스트 외부에 존재하여 스프링과 무관한 자원에 대해 동작한다
하지만 인터셉터는 스프링의 DistpatcherServlet이 컨트롤러를 호출하기 전, 후로 끼어들기 때문에 스프링 컨텍스트(Context, 영역) 내부에서 Controller(Handler)에 관한 요청과 응답에 대해 처리한다
스프링의 모든 빈 객체에 접근할 수 있다
인터셉터는 여러 개를 사용할 수 있고 로그인 체크, 권한체크, 프로그램 실행시간 계산작업 로그확인 등의 업무처리가 가능하다
인터셉터의 실행메서드
preHandler() - 컨트롤러 메서드가 실행되기 전
postHanler() - 컨트롤러 메서드 실행직 후 view페이지 렌더링 되기 전
afterCompletion() - view페이지가 렌더링 되고 난 후
 3. AOP
OOP를 보완하기 위해 나온 개념
객체 지향의 프로그래밍을 했을 때 중복을 줄일 수 없는 부분을 줄이기 위해 종단면(관점)에서 바라보고 처리한다
주로 '로깅', '트랜잭션', '에러 처리'등 비즈니스단의 메서드에서 조금 더 세밀하게 조정하고 싶을 때 사용합니다
Interceptor나 Filter와는 달리 메소드 전후의 지점에 자유롭게 설정이 가능하다
Interceptor와 Filter는 주소로 대상을 구분해서 걸러내야하는 반면, AOP는 주소, 파라미터, 애노테이션 등 다양한 방법으로 대상을 지정할 수 있다
AOP의 Advice와 HandlerInterceptor의 가장 큰 차이는 파라미터의 차이다
Advice의 경우 JoinPoint나 ProceedingJoinPoint 등을 활용해서 호출한다
반면 HandlerInterceptor는 Filter와 유사하게 HttpServletRequest, HttpServletResponse를 파라미터로 사용한다

AOP의 포인트컷
@Before: 대상 메서드의 수행 전
@After: 대상 메서드의 수행 후
@After-returning: 대상 메서드의 정상적인 수행 후
@After-throwing: 예외발생 후
@Around: 대상 메서드의 수행 전/후
- [ ]  Spring Security란?
홈페이지에 인증 및 권한 기능을 빠르게 부여해 인증 및 권한 보호 기능을 손쉽게 추가할 수 있는 Spring Framework
필요한 데이터에 안전하고 빠르게 접근하도록 지원하며 동시에 고객 정보 및 거래 데이터를 승인되지 않는 접근으로부터 보호하여 고객 데이터를 효율적으로 관리하는 데 도움을 준다
Spring Security는 인증, 권한 관리 그리고 데이터 보호 기능을 포함하여 웹 개발 과정에서 필수적인 사용자 관리 기능을 구현하는데 도움을 주는 Spring의 강력한 프레임워크 이다
**JWT 기본 이해** 

- [ ]  JWT란 무엇인가요?
JWT는 Json Web Token의 약자로 일반적으로 클라이언트와 서버 사이에서 통신할 때 권한을 위해 사용하는 토큰이다
 웹 상에서 정보를 Json형태로 주고 받기 위해 표준규약에 따라 생성한 암호화된 토큰으로 복잡하고 읽을 수 없는 string 형태로 저장되어있다
JWT는 헤더(header), 페이로드(payload), 서명(signature) 세 파트로 나눠져 있으며, 아래와 같은 형태로 구성되어 있다
헤더 (Header)
어떠한 알고리즘으로 암호화 할 것인지, 어떠한 토큰을 사용할 것 인지에 대한 정보가 들어있다
정보 (Payload)
전달하려는 정보(사용자 id나 다른 데이터들, 이것들을 클레임이라고 부른다)가 들어있다
payload에 있는 내용은 수정이 가능하여 더 많은 정보를 추가할 수 있다. 그러나 노출과 수정이 가능한 지점이기 때문에 인증이 필요한 최소한의 정보(아이디, 비밀번호 등 개인정보가 아닌 이 토큰을 가졌을 때 권한의 범위나 토큰의 발급일과 만료일자 등)만을 담아야한다
서명 (Signature)
가장 중요한 부분으로 헤더와 정보를 합친 후 발급해준 서버가 지정한 secret key로 암호화 시켜 토큰을 변조하기 어렵게 만들어준다
한가지 예를 들어보자면 토큰이 발급된 후 누군가가 Payload의 정보를 수정하면 Payload에는 다른 누군가가 조작된 정보가 들어가 있지만 Signatute에는 수정되기 전의 Payload 내용을 기반으로 이미 암호화 되어있는 결과가 저장되어 있기 때문에 조작되어있는 Payload와는 다른 결과값이 나오게 된다
이러한 방식으로 비교하면 서버는 토큰이 조작되었는지 아닌지를 쉽게 알 수 있고, 다른 누군가는 조작된 토큰을 악용하기가 어려워진다
**토큰 발행과 유효성 확인**

- [ ]  Access / Refresh Token 발행과 검증에 관한 **테스트 시나리오** 작성하기
액세스 토큰 발행 테스트

유효한 사용자 자격 증명(아이디, 비밀번호)을 사용하여 액세스 토큰 요청
요청이 성공적으로 처리되어 액세스 토큰이 발급되는지 확인
발급된 액세스 토큰의 유효성 검증(JWT 토큰 구조 확인, 서명 유효성 검증 등)

액세스 토큰 검증 테스트

유효한 액세스 토큰을 사용하여 보호된 리소스에 대한 요청
요청이 성공적으로 처리되고 리소스에 대한 접근이 허용되는지 확인
만료된 액세스 토큰을 사용하여 보호된 리소스에 대한 요청
요청이 거부되고 적절한 오류 응답이 반환되는지 확인
위조된 액세스 토큰을 사용하여 보호된 리소스에 대한 요청
요청이 거부되고 적절한 오류 응답이 반환되는지 확인

리프레시 토큰 발행 테스트

유효한 리프레시 토큰을 사용하여 새 액세스 토큰 요청
요청이 성공적으로 처리되어 새 액세스 토큰이 발급되는지 확인
만료된 리프레시 토큰을 사용하여 새 액세스 토큰 요청
요청이 거부되고 적절한 오류 응답이 반환되는지 확인
위조된 리프레시 토큰을 사용하여 새 액세스 토큰 요청
요청이 거부되고 적절한 오류 응답이 반환되는지 확인

리프레시 토큰 검증 테스트

유효한 리프레시 토큰을 사용하여 새 액세스 토큰 요청
요청이 성공적으로 처리되어 새 액세스 토큰이 발급되는지 확인
만료된 리프레시 토큰을 사용하여 새 액세스 토큰 요청
요청이 거부되고 적절한 오류 응답이 반환되는지 확인
위조된 리프레시 토큰을 사용하여 새 액세스 토큰 요청
요청이 거부되고 적절한 오류 응답이 반환되는지 확인

토큰 만료 테스트

액세스 토큰과 리프레시 토큰의 만료 시간을 설정하고, 만료 시점에 토큰 사용 시도
만료된 토큰 사용 시도가 거부되고 적절한 오류 응답이 반환되는지 확인
**유닛 테스트 작성**

- [ ]  JUnit를 이용한 JWT Unit 테스트 코드 작성해보기

  - https://preasim.github.io/39

  - [https://velog.io/@da_na/Spring-Security-JWT-Spring-Security-Controller-Unit-Test하기](https://velog.io/@da_na/Spring-Security-JWT-Spring-Security-Controller-Unit-Test%ED%95%98%EA%B8%B0)


### Day 2 - 백엔드 배포하기

---
**테스트 완성**

- [ ]  백엔드 유닛 테스트 완성하기

**로직 작성**

- [ ]  백엔드 로직을 Spring Boot로
    - [ ]  회원가입 - /signup
        - [ ]  Request Message

           ```json
           {
               "username": "JIN HO",
               "password": "12341234",
               "nickname": "Mentos"
           }
           ```

        - [ ]  Response Message

           ```json
           {
               "username": "JIN HO",
               "nickname": "Mentos",
               "authorities": [
                       {
                               "authorityName": "ROLE_USER"
                       }
               ]		
           }
           ```

    - [ ]  로그인 - /sign
        - [ ]  Request Message

           ```json
           {
               "username": "JIN HO",
               "password": "12341234"
           }
           ```

        - [ ]  Response Message

           ```json
           {
               "token": "eKDIkdfjoakIdkfjpekdkcjdkoIOdjOKJDFOlLDKFJKL",
           }
           ```


**배포해보기**

- [ ]  AWS EC2 에 배포하기

**API 접근과 검증**

- [ ]  Swagger UI 로 접속 가능하게 하기

### Day 3 - 백엔드 개선하기

---
[Git 커밋 메시지 잘 쓰는 법 | GeekNews](https://news.hada.io/topic?id=9178&utm_source=slack&utm_medium=bot&utm_campaign=TQ595477U)

**AI-assisted programming**

- [ ]  AI 에게 코드리뷰 받아보기

**Refactoring**

- [ ]  피드백 받아서 코드 개선하기

**마무리**

- [ ]  AWS EC2 재배포하기
