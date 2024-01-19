[스프링 동작원리]

1. DispatcherServlet은 모든 연결을 담당하며 웹브라우저의 요청을 받는다.
2. HandlerMapping 객체에게 handler(컨트롤러)검색을 요청한다. HandlerMapping은 클라이언트 요청 경로를 이용해 컨트롤러 객체를 찾아서 DispatcherServlet에 리턴한다.
3. DispathcerServlet는 @Controller클래스와 기타 응답 처리 클래스를 처리하기 위해 HandlerAdapter 객체를 가져와 요청처리를 위임한다.
4. HandlerAdaptor객체는 컨트롤러의 알맞은 메서드를 호출해서 요청을 처리하고
5. 컨트롤러는 여러가지 기능을 수행한 후 결과 값을 리턴한다.
6. HandlerAdaptor는 컨트롤러 결과 값을 ModelAndView 객체에 담아 DispatcherServlet에 리턴한다.
7. ModelAndView 객체를 받은 DispatcherServlet은 View Resolver 객체를 이용해 결과를 보여줄 View를 검색한다. 담긴 view name을 이용해 view 객체를 찾거나 생성하여 리턴한다.
8. DispatcherServlet은 View Resolver가 리천한 view 객체에게 응답 결과를 생성 요청한다.
9. JSP를 사용하는 경우, view 객체는 JSP를 실행함으로서 브라우저에게 전송할 응답 결과를 생성한다.
   ModelAndView의 Model에 담겨 있는 데이터가 응답 결과에 필요하면 Model에서 데이터를 꺼내 JSP에서 사용할 수 있다.
