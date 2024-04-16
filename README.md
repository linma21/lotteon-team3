# LotteOn-Project

### Custom Repository 생성했는데 

> **BeanCreationException** Error creating bean with name 'productRepository' 에러가 발생했다.

```java
@Slf4j
@RequiredArgsConstructor
public class ProductRepositoryImpl implements ProductRepositoryCustom {}
```
1. 생성한 RepositoryImpl과 RepositoryCustom을 모두 주석처리하니 에러 없이 실행된다.
2. 검색을 해봐도 repository의 카멜표기법을 안지켜져서 그렇다고 하는데 QueryDsl을 써서 Custom하는 거라 이름 문제는 아님. 
3. 뭐가 문제인지 이전에 다른 프로젝트에서 Custom 했던 코드랑 하나하나 비교했는데 어노테이션도 다 똑같이 제대로 했는데 이 것만 실행이 안됨.
4. BeanCreationException 이라 혹시 몰라서 Impl에 @Repository를 넣어줬더니 실행이 된다.
   ```java
   @Slf4j
@Repository
@RequiredArgsConstructor
public class ProductRepositoryImpl implements ProductRepositoryCustom{}
   ```
   > RepositoryImpl에는 @Repository 어노테이션을 명시적으로 추가할 필요가 없다고 알고 있고, 또 이전 프로젝트에서는 @Repository 없이도 실행이 되었는데 뭐가 문제일까?

> ProductRepository가 repository 하위 디렉토리인 product에 있어서 JPA가 해당 구현체를 자동으로 인식하지 못하는 문제였다.
![ProductRepository_out](https://github.com/linma21/lotteon-team3/assets/154877422/305e729c-9a46-4ce7-8000-a2eba070aded)
ProductRepository를 repository로 옮기니까 @Repository없이도 스프링이 해당 패키지를 자동으로 스캔하여 리포지토리를 인식한다.
