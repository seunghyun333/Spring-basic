# 스프링 설정 파일

# 빌드
- 소스코드를 실행할 수 있는 소프트웨어 형태로 변환하는 과정
- 자바코드, 여러 자원(xml, jar, properties)을 JVM이나 톰캣 같은 WAS가 이해할 수 있도록 패키징
- 컴파일, 테스팅, 검사, 배포까지 일련의 작업


# pom.xml
- maven 설정파일, 라이브러리 다운, 생성, 프로젝트 빌드 작업 자동화

# web.xml
- 웹 컨테이너(톰캣)에 구성정보 전달, 서블릿 매핑 대상 정의

  <태그>
  1. filter - encoding에 관한 내용
  2. listener - 서버가 켜질 때 실행되는 클래스 정의
     서버가 켜질때 스프링에서 제공하는 ContextLoaderListener 클래스 실행됨
     ContextLoaderListener : ServletContextListener 상속받음 ( 서버가 켜지고 꺼질 때 이벤트를 제공함)
     ContextLoaderListener가 ApplicationContext 생성함 (빈 등록과 관리
  3. context-param : <value>파일을 읽어서 빈 등록
  4. servlet - DispatcherServelt이 WebApplicationContext 생성
       WebApplicationContext은 <init param>을 읽어 빈을 등록한다.



# 서버가 켜질 때
1. contextLoadListener에 의해 ApplicationContext가 생성되고 이 context는 Service, Dao 단의 빈을 등록한다. [root-context.xml]
2. DispatcherServlet에 의해 webApplicationContext가 생성되고 이 context는 Controller 단의 빈을 등록한다. [servelt-context.xml]

   1 -> 2 : 접근 불가
   2 -> 1 : 접근 가능 

