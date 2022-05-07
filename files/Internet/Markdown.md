# 마크다운 markdown 관련 문서

## 1. 마크다운이란?
---
Markdwon은 텍스트 기반의 마크업 언어로 2004년 존 그루버에 의해 만들어졌고, Html로 변환 가능하다는 점이 있다. 특수 기호와 문자를 이용한 간단한 구조의 문법을 사용하여 웹에서도 보다 빠르게 컨텐츠를 작성하고 보다 직관적으로 인식할수 있다. 마크다운이 각광 받기 시작한 이유는 깃헙에서 사용하는 readme.md라는 처음 접하게 되는 마크다운 문서 덕분이다. 이를 통해서 설치 방법, 소스코드 설명, 이슈 등을 간단하게 기록하고 가독성을 높일 수 있다는 장점이 부각 되면서 사용하고 있다.



## 2. 마크다운 사용법(문법)

---
<br><br>
## 2.1. 헤더 (HEADER)
---

```
# This is a H1
## This is a H2
### This is a H3
#### This is a H4
##### This is a H5
###### This is a H6
```
# This is a H1
## This is a H2
### This is a H3
#### This is a H4
##### This is a H5
###### This is a H6
H1 ~ H6 순으로 크기 지원한다. (숫자가 커질수록 글자 크기는 작아진다.)
<br><br><br><br>


## 2.2. BlockQuote
---
```
> This is a first blockqute.
>	> This is a second blockqute.
>	>	> This is a third blockqute.>
```
> This is a first blockqute.
>	> This is a second blockqute.
>	>	> This is a third blockqute.>

<br>
이메일에서 사용하는 > 블록인용 문자를 이용하여 처리한다.
<br><br><br><br>

## 2.3. 목록
---
```
* 빨강
  * 녹색
    * 파랑

+ 빨강
  + 녹색
    + 파랑

- 빨강
  - 녹색
    - 파랑
```
* 빨강
  * 녹색
    * 파랑

+ 빨강
  + 녹색
    + 파랑

- 빨강
  - 녹색
    - 파랑

<br>
순서가 있는 목록은 1, 2, 3 숫자를 붙여서 처리하면되고, 순서가 없는 목록을 처리할때는 
*, +, -를 지원한다.
<br><br><br><br>

## 2.4. 코드
---
4개의 공백  또는 하나의 탭으로 들여쓰기를 만나면 변환되기 시작하여 들여쓰지 않은 행은 변환이 계속 된다.
<br><br>

### 2.4.1. 들여쓰기
```
This is a normal paragraph:

    This is a code block.
    
end code block.
```
을 실제로 적용하게 되면, 

This is a normal paragraph:

    This is a code block.
    
end code block.

로 나타나게 된다. 이러한 문제점을 타파하기 위해서 2가지 방식을 이용한다.

<br><br>

### 2.4.1 코드블럭 (들여쓰기 방법안내)

* ```<pre><code>{code}</code></pre>``` 이용방식
```
<pre>
<code>
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }

}
</code>
</pre>
```

```
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}

```

* 코드블럭코드("```") 을 이용하는 방법 (이 방법이 제일 편함)
```
'''
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
'''
```
<br><br><br><br>

## 2.5. 수평선 ```<hr/>```
---
아래줄을 모두 수평선을 만든다. 마크다운 문서를 미리 보기로 출력할때 페이지 나누기 용도로 자주 사용한다.

```
* * *
***
******
- - -
-----------------------
```
* * *
***
******
- - -
-----------------------

<br><br><br><br>

## 2.6. 링크
---
* 참조 링크
```
[link keyword][id]

[id]: URL "Optional Title here"

// code
Link: [Google][googlelink]

[googlelink]: https://google.com "Go google"<br><br>
```
>Link: [Google][googlelink]

[googlelink]: https://google.com "Go google"

<br>

* 외부 링크
```
사용문법: [Title](link)
적용예: [Google](https://google.com, "google link")
```
>Link : [Google](https://google.com, "google link")

<br>

* 자동 연결
```
일반적인 URL 혹은 이메일주소인 경우 적절한 형식으로 링크를 형성한다.

* 외부링크: <http://example.com/>
* 이메일링크: <address@example.com>
```
> 외부링크: <http://example.com/>

> 이메일링크: <address@example.com>

<br><br><br><br>

## 2.7. 강조
---
```
*single asterisks*
_single underscores_
**double asterisks**
__double underscores__
~~cancelline~~
```
*single asterisks*

_single underscores_

**double asterisks**

__double underscores__

~~cancelline~~

문장 중간에 사용할 경우에는 뛰어쓰기를 하는 것이 좋다.


<br><br><br><br>

## 2.8. 이미지
---
```
![Alt text](/path/to/img.jpg)
![Alt text](/path/to/img.jpg "Optional title")
```

사이즈 조절 기능은 없기 떄문에 ``` <img width="" height=""></img> ``` 을 사용한다.

예) 
```
<img src="/path/to/img.jpg" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br/>
<img src="/path/to/img.jpg" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck"></img>
```

<br><br><br><br>

## 2.9. 줄바꿈
---
3칸 이상 뛰어쓰기를 하면 줄이 바뀐다.   
```
* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다. 
이렇게

* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다.___\\ 띄어쓰기
이렇게
```
* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다. 
이렇게

* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다.___\\ 띄어쓰기
이렇게










