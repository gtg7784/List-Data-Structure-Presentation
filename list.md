---
marp: true
style: |
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
  table {
    margin-left: 30px
  }

footer: '2021 선린인터넷고등학교 자료구조 - 리스트'
---

# 리스트

### 30409 고태건, 30413 박경민

---                                                                                                                                                                          
# 목차

1. 리스트란?
2. 배열
3. 배열의 검색
5. 배열의 추가/삭제
6. 연결 리스트
7. 연결 리스트의 검색
8. 연결 리스트의 추가/삭제
9. 원형 연결 리스트
10. 이중 연결 리스트

---

# 리스트란?

**리스트는 선형적으로 값을 가지고 있는 자료구조**

두가지가 있다.

- 배열 리스트
- 연결 리스트

---

<style scoped>
table {
  margin-top: 80px;
}
</style>

# 배열 리스트

- **연속된 데이터를 저장하는 자료구조**
- 인덱스와 대응하는 데이터를 저장하여, 인덱스는 첫번째 부터 상대적인 위치를 표현
- 검색 연산은 빠르지만, 추가/삭제 연산이 느리다

0 | 1 | 2 | 3 | 4 | 5 | 6
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | Orange | Coconut | Pizza | Papaya | Melon 

---

<style scoped>
table {
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>

# 배열의 검색

- 검색은 매우 빠르다
- 아래 그림을 보면 바로 이해가 될것이다

0 | 1 | 2 | 3 | 4 | **5** | 6
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | Orange | Coconut | Pizza | **Papaya** | Melon 

```
5번째 주소에 있는건 무엇일까??

= 배열의 첫번째 주소 + 5 -> Papaya
```

---

<style scoped>
table {
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>

# 배열의 추가/삭제

- 추가나 삭제가 많은 상황에 적합하지 않다.
- 작업을 할때마다 메모리 상의 주소를 다 바꿔야 하는 문제가 생긴다

0 | 1 | 2 | 3 | **4** | 5 | 6
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | Orange | Coconut | **Pizza** | Papaya | Melon 


```
과일 배열에 웬 피자가 꼈어!

> 피자를 지워보자
```

---

0 | 1 | 2 | 3 | **4** | 5 | 6
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | Orange | Coconut | **Pizza** | Papaya | Melon 

0 | 1 | 2 | 3 | 4 | 5 | 6
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | Orange | Coconut |  | Papaya | Melon 

0 | 1 | 2 | 3 | 4 | 5 | 6
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | Orange | Coconut | Papaya |  | Melon 

0 | 1 | 2 | 3 | 4 | 5 | 6
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | Orange | Coconut | Papaya | Melon |  

---

# 연결 리스트

- **배열과 같이 연속된 데이터를 저장하기 위한 자료구조**
- 배열의 단점(추가, 삭제)을 해결하기 위해 고안 (더 좋은건 아님)
- 추가/삭제는 빠르지만 검색이 느리다.
- 배열처럼 메모리제 저장하는 방식이 아닌, **노드**라는 개념을 만들어서 사용한다.
- **노드**는 데이터를 가지고 있는 데이터 필드와 다음 노드의 주소를 갖고있는 링크 필드(포인터)로 구성되어있다.

![left](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fl0VVL%2FbtquxsmG8P6%2Fnxm8KVIBfzq4LttQHf2CvK%2Fimg.png)


---

<style scoped>
table {
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>

# 연결 리스트의 검색

- 검색은 느리다
- 아래 그림을 보면 바로 이해가 될것이다

100 | 130 | 160 | 200 | 210 | 250 | 300
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | Pizza | Orange | Coconut | Papaya | Melon 
210 | 130 | 200 | 300 | 160 | 250 |  

```
저 pizza는 뭐하는놈이야!! 찾아내!

> pizza를 찾아보자
```

---

100 | 130 | 160 | 200 | 210 | 250 | 300
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
**Banana** | Apple | Pizza | Orange | Coconut | Papaya | Melon 
**210** | 130 | 200 | 300 | 160 | 250 |  

100 | 130 | 160 | 200 | 210 | 250 | 300
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | Pizza | Orange | **Coconut** | Papaya | Melon 
210 | 130 | 200 | 300 | **160** | 250 |  

100 | 130 | 160 | 200 | 210 | 250 | 300
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | **Pizza** | Orange | Coconut | Papaya | Melon 
210 | 130 | 200 | 300 | **160** | 250 |  

---

# 연결 리스트의 추가/삭제

<style scoped>
table {
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>


- 추가/삭제는 겁나빠르다
- 아래 그림을 보면 바로 이해가 될것이다

100 | 130 | 160 | 200 | 210 | 250 | 300
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | Pizza | Orange | Coconut | Papaya | Melon 
210 | 130 | 200 | 300 | 160 | 250 |  

```
저 pizza는 뭐하는놈이야!! 지워!!

> pizza를 지워보자
```

---

100 | 130 | 160 | 200 | 210 | 250 | 300
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | **Pizza** | Orange | Coconut | Papaya | Melon 
210 | 130 | **200** | 300 | **160** | 250 |  

100 | 130 | 160 | 200 | 210 | 250 | 300
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | **Pizza** | Orange | Coconut | Papaya | Melon 
210 | 130 | **200** | 300 | **200** | 250 |  

100 | 130 | 160 | 200 | 210 | 250 | 300
:----:|:----:|:-----:|:----:|:----:|:----:|:----:
Banana | Apple | | Orange | Coconut | Papaya | Melon 
210 | 130 | | 300 | 200 | 250 |  

---

# 원형 연결 리스트

![center width:500px](https://t1.daumcdn.net/cfile/tistory/99B1E73B5A50DA8F18)

---

<style scoped>
h1 {
  margin-bottom: 80px;
}
img {
  margin-bottom: 80px;
}
</style>

# 이중 연결 리스트

![center width: 3000px](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2949.png)

---

# 자료 출처

- https://velog.io/@kiiim/10%EC%9B%9412%EC%9D%BC-%EB%B0%B0%EC%97%B4-rhcqdr1x
- https://opentutorials.org/module/1335/8940
- https://medium.com/@yeonghun4051/%EC%97%B0%EA%B2%B0%EB%A6%AC%EC%8A%A4%ED%8A%B8ii-c06443f705fd

