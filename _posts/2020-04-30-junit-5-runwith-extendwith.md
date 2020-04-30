Spring5 + JUnit5 에서 테스트를 위하여 @RunWith(SpringRunner.class)를 선언해 사용하려고 하니 
class를 찾을 수 없다며 JUnit4를 다운받아서 classpath에 추가하라고한다.

<img src="https://cjred.net/img/blog/20200430-blog-01.png" alt="20200430-blog-01.png"  style="zoom:50%;" />

인터넷을 찾아보니 @RunWith가 @ExtendWith(..) 으로 바꿨다고 한다..

<img src="https://cjred.net/img/blog/20200430-blog-02.png" alt="20200430-blog-02.png" style="zoom:50%;" />


참고 : https://www.baeldung.com/junit-5-runwith

