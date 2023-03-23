
# 602377101 강승희
<h2> 2023-03-23 </h2>

# R 패키지
- R에서의 패키지 -> 라이브러리와 같은 개념

## [1] 패키지 설치하기
- R 스튜디오 Console 창에 install.packages("ggplot2") 입력
- Packages -> Install -> cowsay 입력 후 install 클릭

## [2] 패키지 불러오기

- Console 창에 library(ggplot2) 입력
- Console 창에 library(cowsay) 입력

# 변수
- 개념 : 프로그램 내에서 어떤 값을 저장해 놓을 수 있는 '보관상자'의 역할 
- 문자에 값 대입하기
> total <- 5050    
> a <- 10  
> b <- 20  
> c <- a + b
<br>
## [1] 변수명의 작명 규칙
- 첫 글자는 영문자나 마침표(.)으로 시작
- 변수명에서 대문자와 소문자는 별개의 문자 취급
- 공백 불가

## [2] 변수에 저장될 수 있는 값의 종류
### - 자료형 : 변수에 저장할 수 있는 값의 종류
### (1) 숫자형 
- 자연수를 포함하여 양의 정수, 음의 정수, 0, 실수 등의 값으로, 산술연산 가능   
ex) 1,2,-4  
### (2) 문자형 
- 숫자형과는 달리 산술연산을 할 수 없고, 문자형의 값은 반드시 작은 따옴표나 큰따옴표로 묶어 표시해야함 
ex) 'Tom',"Jane"  
### (3) 논리형 
- T/F로 줄여서 사용 가능  
- 보통 비교연산의 결과값으로 주어짐
- 덧셈과 같은 산술연산을 적용하면   
TRUE -> 1 / FALSE -> 0으로 변환되어 사용  
ex) TRUE, FALSE  
### (4) 특수 값 
- NULL : 정의되어 있지 않음 의미,  
비어있는 객체를 나타내는 값
- NA : Not Available의 약자,  
사용 불가능한 데이터 의미
- NaN : Not A Number의 약자,   
수학적으로 정의가 불가능한 값  

=> 모두 R 프로그래밍 언어에서 사용되는 값으로, 데이터 처리에서 중요한 역할

# 백터
- 백터의 form     
> score <- c(68, 95, 83, 76, 90, 80, 85, 91, 82, 70)
> mean(score) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# 평균 출력
<br>

## [1] 개념
- R에서 제공하는 혀러 개의 값을 한꺼번에 저장하는 기능
- 일반적인 프로그래밍 용어로는 1차원 배열이라고도 함

## [2] 목적
- 여러 개의 값들을 하나의 묶음으로 처리하기 위한 것

## [3] 벡터 만들기
- 백터를 만드는데 사용되는 함수 -> c(&nbsp;&nbsp;&nbsp;)
### (1) 연속적인 숫자로 이루어진 백터
> foo <- 20:100  
> foo  
 [1]  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35  36  
[18]  37  38  39  40  41  42  43  44  45  46  47  48  49  50  51  52  53  
[35]  54  55  56  57  58  59  60  61  62  63  64  65  66  67  68  69  70  
[52]  71  72  73  74  75  76  77  78  79  80  81  82  83  84  85  86  87  
[69]  88  89  90  91  92  93  94  95  96  97  98  99 100

### (2) 일정한 간격의 숫자로 이루어진 백터
> v3 <- seq(1,101,3) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# 시작, 종료, 간격  
> v3  
 [1]   1   4   7  10  13  16  19  22  25  28  31  34  37  40  43  46  49  
[18]  52  55  58  61  64  67  70  73  76  79  82  85  88  91  94  97 100

### (3) 반복된 숫자로 이루어진 백터
> v5 <- rep(1,times-5) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # 1을 5번 반복  
> v5  
1&nbsp;&nbsp;&nbsp; 1&nbsp;&nbsp;&nbsp; 1&nbsp;&nbsp;&nbsp; 1&nbsp;&nbsp;&nbsp; 1

## [4] 벡터 이름값 붙이기
> absent <- c(8,4,3,4,6)  
> names(absent) <- c('mon','tue','wed', 'thu', 'fri')  
> absent  
mon tue wed thu fri   
  &nbsp;&nbsp;&nbsp;8   &nbsp;&nbsp;&nbsp;4   &nbsp;&nbsp;&nbsp;3   &nbsp;&nbsp;&nbsp;4   &nbsp;&nbsp;&nbsp;6 

 ## [5] 백터에 저장된 원소값 변경하기
 > absent  
mon tue wed thu fri   
  &nbsp;&nbsp;&nbsp;8   &nbsp;&nbsp;&nbsp;4   &nbsp;&nbsp;&nbsp;3   &nbsp;&nbsp;&nbsp;4   &nbsp;&nbsp;&nbsp;6   
> absent[1] <- 100  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#absent에서 1번째 값을 100으로 변경  
> absent  
mon tue wed thu fri   
&nbsp;&nbsp;&nbsp;100   &nbsp;&nbsp;&nbsp;4   &nbsp;&nbsp;&nbsp;3   &nbsp;&nbsp;&nbsp;4   &nbsp;&nbsp;&nbsp;6   
> absent[3:4] <- c(30,70)  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#absent에서 3번째, 4번째 값 변경  
> absent  
mon tue wed thu fri   
&nbsp;&nbsp;&nbsp;100   &nbsp;&nbsp;&nbsp;4   &nbsp;&nbsp;&nbsp;30   &nbsp;&nbsp;&nbsp;70   &nbsp;&nbsp;&nbsp;6  
> absent <- c(200,300,400)  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#absent를 200, 300, 400으로 변경  
> absent  
[1] 200&nbsp;&nbsp; 300&nbsp;&nbsp; 400


# 함수
## [1] 함수의 매개변수
- 개념 : 함수의 입력값을 받는 변수
- 함수의 정의에 맞추어 매개변수를 입력하면 정의된 결과값을 얻을 수 있음
### * 연습문제
- 1~12월 배열하기
> foo <- paste(1:12, '월', sep = '')  
> foo  
 [1] "1월"  "2월"  "3월"  "4월"  "5월"  "6월"  "7월"  "8월"  "9월"   
[10] "10월" "11월" "12월"

---
<h2> 2023-03-16 </h2>

# README.md 작성요령
- 히스토리 작성 시 최근 내용을 맨 위로 오게끔 작성

# R 언어의 특징
## 1.  데이터 분석에 특화된 언어
- 통계를 포함한 데이터 분석 작업에 활용할 목적으로 개발된 언어
- 컴파일 과정 없이도 바로 실행하여 결과를 확인할 수 있음

## 2. 탄탄한 사용자 커뮤니티
- 초보자를 위한 학습 자료도 풍부하게 존재함
- 사용자층이 두텁기 때문에 다양한 커뮤니티가 존재함

## 3. 다양한 패키지 제공
- 여기서 패키지는 라이브러리 정도의 개념으로 생각하면 됨
- 데이터 분석에 사용되는 함수들을 종류별로 묶어 패키지 형태로 제공
- 데이터 분석에 필요한 거의 모든 기능이 제공
- 쉽게 시각화 가능 </br>
(데이터 분석에 있어서 분석 결과를 시각적으로 표현하는 것은 매우 중요함)

## 4. 편리한 프로그래밍 환경
- R 스튜디오가 제공되어 모든 작업을 R 스튜디오 내에서 처리할 수 있음
- 무료 오픈소스 제공

# R 스튜디오
## 1. 화면 구성
- 소스 영역, 콘솔 영역, 환경 영역, 파일 영역으로 구성
### [1] 소스 영역
- R 명령문을 작성하고 실행하는 영역
- 메모장과 같은 문서 편집기와 유사함

### [2] 콘솔 영역
- 콘솔창 : 소스창에서 작성한 R 명령문을 실행시켰을 때 명령문의 실행 과정 및 결과가 표시되는 영역
- 터미널창 : 윈도우의 '명령 프롬프트'와 동일한 기능을 제공함

### [3] 환경영역
- 환경창 : R 명령문이 실행되는 동안 만들어지는 각종 변수나 자료구조의 내용을 보여주는 영역
- 히스토리창 : R 스튜디오에서 실행한 명령문, 결과, 패키지 설치,오류 등 거의 모든 작업 과정에 대한 이력이 표시
- 커넥션창, 튜토리얼창

### [4] 파일영역
- 파일창 : 윈도우의 파일 탐색기와 동일한 역할을 함
- R 스튜디오로 불러오거나 복사, 삭제, 이동 등의 작업을 수행할 수 있음
- 플룻창 : R 명령문으로 작성한 그래프가 표시되는 여역
- 패키지 창 : R 에서는 수많은 함수를 제공하고 있는데, 이러한 함수들은 작성 목적이나 개발자에 따라 패키지 형태로 묶여 제공
- 도움말창, 뷰어창

# R 스튜디오에서의 명령문 실행
- <- : 대입연산자  
ex) A <- 51 : 80  
결과 : A &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;int [1:30] 51 52 52 54 55 56 57...
### [1]  산술연산자 
- +(덧셈), -(뺄셈), *(곱셈), /(나눗셈), %%(나눗셈의 나머지), ^(제곱)
- 주석 : # 기호로 시작
- 함수를 사용하여 계산 가능  
ex) log(), max(), min() 등

# R 패키지
### [1] 패키지
- 개념 : 함수들을 기능별로 묶어놓은 일종의 '꾸러미'

---
<h2> 2023-03-09 </h2>

# git 사용자 설정
cmd 창에서 다음과 같이 입력
- $ git config --global user.name "foo" 
- $ git config --global user.email "foo@example.com"

# 프로젝트 폴더 git으로 초기화
- 'source control' -> 'Initialize Repository' 버튼 클릭

# commit 방법
- 'source control' -> ‘✔commit’ 버튼 클릭

# github로 push
- 'source control' -> 'Publich Branch '버튼 클릭
- 저장소 private/public 중에 선택

# R 언어
- 비교적 최근에 개발된 언어(1993년도 개발)
- 통계계산과 그래픽을 위한 프로그래밍 언어

---