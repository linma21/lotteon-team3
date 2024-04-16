![transparent](https://capsule-render.vercel.app/api?type=transparent&fontColor=FF0000&text=LotteON&height=150&fontSize=60&desc=%20프로젝트&descAlignY=75&descAlign=60)

## 🛒프로젝트 소개
롯데e-커머스 LOTTE ON 쇼핑몰 개발


## ⏱프로젝트 기간
2024.04.15. ~ 2024.05.16 (1개월)


## 👫멤버 소개

## 🌟프로젝트 페이지 소개


## 📚기술스택
<div align=center> 
  <img src="https://img.shields.io/badge/html5-E34F26?style=for-the-badge&logo=html5&logoColor=white">
  <img src="https://img.shields.io/badge/css-1572B6?style=for-the-badge&logo=css3&logoColor=white">
  <br>
  
  <img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white"> 
  <br>
  
  <img src="https://img.shields.io/badge/springboot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white">
  <img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=java&logoColor=white"> 
  <img src="https://img.shields.io/badge/gradle-221E1F?style=for-the-badge&logo=java&logoColor=white"> 
  <br>

  <img src="https://img.shields.io/badge/github-181717?style=for-the-badge&logo=github&logoColor=white">
  <img src="https://img.shields.io/badge/git-F05032?style=for-the-badge&logo=git&logoColor=white">
  <br>

  <img src="https://img.shields.io/badge/jira-0052CC?style=for-the-badge&logo=jira&logoColor=white">
  <img src="https://img.shields.io/badge/figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white">
  <img src="https://img.shields.io/badge/slack-4A154B?style=for-the-badge&logo=slack&logoColor=white">
  


</div>

<br>


## 🌝프로젝트 주요 기능 소개 

## 🖥개발 환경
- OS : Window10
- Framework : Spring Boot 3.2.0
- Language : Java 17, HTML5, CSS3, Javascript, jQuery 3.1
- DBMS : MySQL 8.0

## 🏗정보구조(IA : Information Architecture)

## 🌟발표 PPT


## 🎱프로젝트 결과

----
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

> ProductRepository가 repository 하위 디렉토리인 product에 있어서 JPA가 해당 구현체를 자동으로 인식하지 못하는 문제였다.<br>
![ProductRepository_out](https://github.com/linma21/lotteon-team3/assets/154877422/305e729c-9a46-4ce7-8000-a2eba070aded)<br>
ProductRepository를 repository로 옮기니까 @Repository없이도 스프링이 해당 패키지를 자동으로 스캔하여 리포지토리를 인식한다.
