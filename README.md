
# 602377101 강승희
<h2> 2023-05-04 </h2>

# 선 그래프
## [1] 하나의 선그래프 작성하기
- 선 그래프를 작성하는 함수 -> plot()
```
> month = 1:12                             # 데이터 입력
> late = c(5,8,7,9,4,6,12,13,8,6,6,4)      # 데이터 입력
> plot(month,                                # x data
     late,                                 # y data
     main='지각생 통계',                    # 제목
     type='l',                             # 그래프의 종류 선택(알파벳)
     lty=1,                                # 선의 종류(line type) 선택
     lwd=1,                                # 선의 굵기 선택
     xlab='Month',                         # x축 레이블
     ylab='Late cnt')                      # y축 레이블
```
<img src="https://user-images.githubusercontent.com/100751115/236191401-18c2febb-91fb-4120-a6b4-98abb5c2da5c.png">

## [2] 복수의 선그래프 작성하기
```
> month = 1:12                                                 
> late1 = c(5,8,7,9,4,6,12,13,8,6,6,4)
> late2 = c(4,6,5,8,7,8,10,11,6,5,7,3)
> plot(month,                      # x 데이터
     late1,                        # y 데이터
     main='Late students',                      
     type='b',                     # 그래프의 종류 선택(알파벳)
     lty=1,                        # 선의 종류(line type) 선택
     col='red',                    # 선의 색상 선택
     xlab = 'Month',               # x축 레이블
     ylab ='Late cnt'              # y축 레이블
     )
> lines(month,                     # x 데이터
      late2,                       # y 데이터
      type = 'b',                  # 선의 종류(line type) 선택
      col='blue'                   # 선의 색상 선택
      )
``` 
<img src="https://user-images.githubusercontent.com/100751115/236190510-5b2826b6-8bcc-4d8e-8511-ff8e3b17e958.png">

# 상자 그림
## [1] 상자 그림의 이해
- 상자그림 : 사분위수를 시각화하여 그래프의 형태로 나타낸 것
- 단일변수 수치형 자료를 파악하는데 자주 사용됨

```
> dist <- cars[,2]
> boxplot(dist, main='자동차 제동거리')
```
<img src="https://user-images.githubusercontent.com/100751115/236189937-e60ab342-08b4-4125-b421-3fdcd89d935a.png" width=350>

- 데이터의 전반적인 분포를 이해하는 데는 도움이 되지만, 구체적으로 최솟값, 최댓값, 중앙값 등이 정확히 얼마인지는 알기가 어려움
-> 이를 알기 위해서 => obxplot.stats() 함수 이용
```
> dist <- cars[,2]
> boxplot(dist, main='자동차 제동거리')
> boxplot.stats(dist)
```
=>  실행결과
```
> boxplot.stats(dist)
$stats
[1]  2 26 36 56 93

$n
[1] 50

$conf
[1] 29.29663 42.70337

$out
[1] 120
```
(1) $stats
- 정상 범위의 데이터 내에서 사분위수에 해당하는 값들이 표시됨
- 5개의 값은 차례로 최솟값, 1 사분위수, 중앙값, 3 사분위수, 최댓값을 의미
(2) $n
- 데이터에 있는 관측값들의 개수
- 50개의 관측값이 저장되어 있음을 의미
(3) $conf
- 중앙값에 관련된 신뢰 구간
(4) $out
- 특이값들의 목록을 저장

## [2] 그룹이 있는 데이터의 상자그림
```
> boxplot(Petal.Length~Species,                   # 데이터와 그룹 정보
          data=iris,                              # 데이터가 저장된 자료구조
          main='품종별 꽃잎의 길이',                # 그래프의 제목
          col=c('green','yellow','blue'))         # 상자들의 색
```
<img src="https://user-images.githubusercontent.com/100751115/236189552-c720a298-3285-4670-b714-e6672787d966.png" width=350>

# 산전도
- 다중변수 데이터에서 두 변수에 포함된 값들을 2차원 그래프상에 점으로 표현항 분포를 관찰할 수 있도록 하는 도구
- 관측값들의 분포를 보고 두 변수 사이의 관련성을 확인하는데 사용

## [1] 두 변수 사이의 산점도
- 산점도를 그려보면 두 변수의 데이터 분포와 변수 사이의 관계 파악 가능
- 산점도는 두 변수의 데이터 분포를 보는 것으므로 두 변수의 데이터 필요

```
> wt <- mtcars$wt                 # 중량 데이터
> mpg <- mtcars$mpg               # 연비 데이터
> plot(wt,mpg,                    # 2개 변수(x축, y축)
       main='중량-연비 그래프',    # 제목
       xlab='중량',               # x축 레이블
       ylab='연비(MPG)',          # y축 레이블
       col='red',                # point의 color
       pch=19)                   # point의 종류
```
<img src= "https://user-images.githubusercontent.com/100751115/236189388-a7d5cb87-168e-4076-9cfd-db3e72eb4a0c.png" width=350>

## [2] 여러 변수들 간의 산점도 => 다중 산점도
- plot()함수는 변수가 2개 이상인 데이터에 대해 변수를 2개씩 짝지어 산점도 작성
- 대각선을 기준으로 오른쪽 위의 산점돌과 왼쪽 아래의 산점도들이 대칭을 이룸
- 여러 변수들 간의 추세를 한눈에 파악 가능
```
> vars <- c('mpg','disp','drat','wt')     # 대상 변수
> target <- mtcars[,vars]                 # 대상 데이터 생성  
> head(target)
> plot(target,
       main='Multi plots')                # 대상 데이터
```
<img src="https://user-images.githubusercontent.com/100751115/236188240-9ea9edbd-685c-4225-b668-de4ca37419bc.png" width=350>

## [3] 그룹 정보가 2개 변수의 산점도
```
> iris.2 <- iris[,3:4]                      # 데이터 준비
> levels(iris$Species)                      # 그룹 확인
> group <- as.numeric(iris$Species)         # 점의 모양과 색
> group                                     # group 내용 출력
> color <- c('red','green','blue')          # 점의 컬러
> plot(iris.2,
       main='Iris plot',
       pch=c(group),
       col=color[group])
```
<img src="https://user-images.githubusercontent.com/100751115/236192629-af7ed5c4-dd20-4ec2-8b71-67e9251d778f.png" width=350>

---
<h2> 2023-04-27 </h2>

# 막대그래프
## [1] 막대그래프 작성의 기초
- 막대그래프 : 그래프별로 집계된 데이터를 표현하는 도구
- 데이터 시각화 : 데이터가 포함하고 있는 정보를 이해하기 쉽게 표현하는 과정
### 1. 도수분포표 계산하기
```
> favorite <- c('WINTER','SUMMER','SPRING','SUMMER','SUMMER','FALL','FALL','SUMMER','SPRING','SPRING')          # 데이터 입력
> favorite          # favorite의 내용 출력
> table(favorite)          # 도수분포 계산
```
- table() : 벡터에 저장되니 범주형 데이터에 대해 데이터값이 종류별로 몇 개인지 계산하는 함수

### 2. 막대그래프 작성하기
```
> ds <- table(favorite)                        # 도수분포표 저장
> ds                                           # 도수분포표 내용 확인
> barplot(ds, main='favorite season')          # 막대그래프 작성
```
<img src="https://user-images.githubusercontent.com/100751115/236193834-c1d5bb9e-c142-4b88-a5c6-8b5d099bb856.png">

- ds : 그래프로 표현할 도수분포효를 지정한다
- main = 'favorite seaon' : 막대그래프 상단의 그래프 제목을 지정한다
- barplot()
(1) 막대그래프를 작성하는 함수
(2) 2개의 매개변수 외에도 다양한 매개변수를 가질 수 있음
(3) 매개변수값에 따라 막대 색상을 다르게 하거나 x축, y축의 레이블을 지정할 수 있음

### 3. 막대그래프 색 지정하기
```
> barplot(ds, main='favorite seaon', 
          col='blue')                                    # 막대의 전채 색 지정
> barplot(ds, main='favorite seaon', 
          col=c('blue','red','green','yellow'))          # 막대의 색을 각각 지정
> barplot(ds, main='favorite seaon', 
          col=rainbow(4))                                # 레인보우 팔레트에서 4개의 색을 선택
```
<img src="https://user-images.githubusercontent.com/100751115/236194302-21e45aad-182f-4686-ad98-6a8fd066c6b1.png">

- col : 막대의 색을 지정하는 매개변수
- 색을 지정하는 방법
(1) 'blue', 'red', 'yellow'와 같이 색의 이름을 지정한다
(2) '#0000FF'와 같이 색상별로 지정된 코드를 이용한다
(3) rgb(0,0,0,255, maxColorValue=255)와 같이 빨강, 초록, 파랑, 투명도의 조합으로 색을 만들어서 사용한다
- 팔레트 사용을 위한 함수 : rainbow(), heat.colors(), terrain.colors(), topo.colors(), cm.colors() 대표적

### 4. x축, y축에 설명 붙이기
```
> barplot(ds, main='favorite seaon', 
          col='green',          # 막대의 색을 지정
          xlab='계절',          # x축 설명
          ylab='빈도수')          # y축 설명
```
<img src="https://user-images.githubusercontent.com/100751115/236194491-6231c123-7c15-4229-8e92-12be4ef4cbd4.png">

- x축 설명 지정 매개변수 -> xlab
- y축 설명 지정 매개변수 -> ylab

### 5. 그래프 막대를 수평 방향으로 출력하기
```
> barplot(ds, main='favorite seaon', 
          col='green',          # 막대의 색을 지정
          horiz=TRUE)          # 수평 방향 출력
```
<img src="https://user-images.githubusercontent.com/100751115/236194631-3a662d8b-1f79-40e1-bd52-b86ae3cb41a8.png">

- 그래프를 수평 방향으로 출력하도록 지정하는 매개변수 -> horiz
- horiz=TRUE : 수평방향
- horiz의 기본값 : 수직방향(FALSE)

### 6. x축의 그룹 이름 바꾸기
```
> barplot(ds, main='favorite seaon', 
          col='green',                          # 막대의 색을 지정
          names=c('FA','SP','SU','WI'),          # 그룹 이름을 바꾸어 출력
          las=2)                                # 그룹 이름을 수직 방향으로
```
<img src="https://user-images.githubusercontent.com/100751115/236194765-fe569282-8f1c-47be-bd66-615a13e710c5.png">

- names() : 그룹의 이름을 다른 것으로 바꾸어 출력할 때 사용
- las : 그룹 이름의 출력 방향을 결정하는 역할
- las값에 따른 출력 방향
(1) 0 : 축 방향(기본값)
(2) 1 : 수평 방향(축 방향과 상관없음)
(3) 2 : 축을 기준으로 수직 방향
(4) 3 : 수직 방향(축 방향과 상관없음)

## [2] 중접 그룹의 막대그래프
```
# 데이터 입력
> age.A  <- c(13709, 10974, 7979, 5000, 4250)
> age.B <- c(17540, 29701, 36209, 33947, 24487)
> age.C <-c(991, 2195, 5366, 12980, 19007)

> ds <- rbind(age.A, age.B, age.C)
> colnames(ds) <- c('1970', '1990', '2010', '2030', '2050')
> ds

# 그래프 작성
> barplot(ds, main='인구 추정',
        col=c('green', 'blue', 'yellow'),          # 연령대별로 색 다르게 지정
        beside=TRUE)                              # 연령대를 각각 막대로 표현
```
<img src="https://user-images.githubusercontent.com/100751115/236195391-b527d2a4-40dc-496e-a9a0-2185094ed503.png">

- 그룹별 색 지정 시 색의 순서 : 그래프의 막대를 기준으로 아래에서 위쪽 방향
- beside : 연령대별 인구수를 하나의 막대로 모아서 표시할지, 각각 표시할지를 지정하기 위한 매개변수

## [3] 막대그래프 범례
### 1. 막대그래프에 범례 추가
```
> barplot(ds, main='인구 추정',
        col=c('green', 'blue', 'yellow'),          
        beside=TRUE,                              
        legend.text=T)                            # 막대그래프에 범례 추가
```
<img src="https://user-images.githubusercontent.com/100751115/236195662-3316d4fa-e75e-4ee3-891f-3dfa5ea23690.png">

- legend.text=T : 그래프 위에 범례를 표시하라는 의미

### 2. 범례를 그래프 밖에 표시하기
```
> par(mfrow=c(1, 1), mar=c(5, 5, 5, 7))          # 그래프 윈도우 설정
> barplot(ds, main='인구 추정',
        col=c('green', 'blue', 'yellow'),          
        beside=TRUE ,                             
        legend.text=T,                            
        args.legend = list(x='topright', bty='n', inset=c(-0.25,0)))          # 범례 위치 설정
```
<img src="https://user-images.githubusercontent.com/100751115/236195972-12de1ce7-64f2-4488-b0c9-17a64d9c346f.png">

(1) par() : 그래프를 표시할 창에 대해 설정하는 역할
(2) mfrow=c(1,1) : 그래프를 출력할 창을 어떻게 분할할지를 지정하는데, 여기서 c(1,1)은 창을 분할하지 않음을 의미
(3) mar=c(5, 5, 5, 7)
- 그래프를 출력할 창과 그래프 출력 영역 밖의 여유 공간을 지정한다
- c(bottom, left, top, right)의 순서로 숫자를 지정한다
- 숫자가 커질수록 여유 공간이 넓어지며, 기본값은 c(5.1, 4.1, 4.1, 2.1)이다
(4) args.legend 
- barplot()에서 범례에 관한 사항을 지정하는데 사용
- 여러 개의 사항을 list() 함수로 묶어서 지정할 수 있음
- x='topright' : 범례를 출력할 기본 위치를 지정하는 데, 'topright'은 그래프 출력에서 위쪽에서 오른쪽을 의미
- bty='o' : 범례가 표시되는 영역에 테두리선을 표시할지의 여부를 지정한다 'o'은 테두리 선을 표시하고, 'n'은 테두리선을 표시하지 않는다
- inset=c(-0.25, 0) : 범례를 x축과 y축 방향으로 얼마나 이동시키지를 지정한다. -1~1 사이의 값을 지정한다(%를 의미)

### 3. 범례의 내용 바꾸기
```
> par(mfrow=c(1, 1), mar=c(5, 5, 5, 7))          # 그래프 윈도우 설정
> barplot(ds, main='인구 추정'
        col=c('green', 'blue', 'yellow')
        beside=TRUE ,
        legend.text=c('0~14세', '15~64세', '65세 이상'),                            # 범례 내용 바꾸기
        args.legend = list(x='topright', bty='n', inset=c(-0.25,0)))
> par(mfrow=c(1, 1), mar=c(5, 4, 4, 2)+0.1)          # 그래프창 설정 해제
```

# 히스토그램
- 개념 : 외관상 막대그래프와 비슷한 그래프로, 그룹이 명시적으로 존재하지 않는 수치형 자료의 분포를 시각화할 때 사용함
- R에서는 hist() 함수를 이용하여 히스토그램을 작성함
- 관측값들이 어느 구간에 어느 빈도로 분포하는지를 쉽게 파악할 수 있도록 해줌

### [1] 히스토그램 작성하기
```
> head(cars)
> dist <- cars[,2]                       # 자동차 제동거리
> dist
> hist(dist,                             # data
       main='Histogram for 제동거리',    # 제목
       xlab='제동거리',                  # x축 레이블
       ylab='빈도수',                    # y축 레이블
       border='blue',                    # 막대 테두리색
       col='green',                      # 막대 색
       las=2,                            # x축 글씨 방향(0~3)
       breaks=5)                         # 막대 개수 조절
```
- border='blue' : 막대의 테두리 색을 지정한다
- breaks=5 : 데이터 내 구간을 몇 개로 나눌지를 지정하며, 값이 커질수록 막대의 개수도 늘어난다

#### 히스토그램 vs 막대그래프
- 막대 사이에 간격이 있으면 -> 막대그래프
- 막대 사이에 간격 없이 막대들이 붙어 있으면 -> 히스토그램
- 막대 그래프에서는 막대의 면적이 의미가 X
- 히스토그램에서는 막대의 면적이 의미 O

## [2] 구간별 빈도수를 도수분포표 형태로 알아보기
```
> result <- hist(dist,                             # data
                 main='Histogram for 제동거리'     # 제목
                 breaks=5)                         # 막대 개수 조절
> result
> freq <- result$counts                            # 구간별 빈도수 저장
> names(freq) <- result$breaks[-1]                 # 구간값을 이름으로 지정
> freq                                             # 구간별 빈도수 출력
```
(1) result : 리스트 형대의 자료구조로 되어 있고 여러 값들을 포함하고 있음
- $breaks : 히스토그램을 작성하기 위한 구간의 경계값들이 저장되어 있음
- $counte : 구간별 빈도수가 저장

# 다중그래프
- 그래프 출력창을 가상으로 몇 개의 화면으로 분할한 뒤 각각의 분할된 화면에 그래프들을 출력하는 것

## [1] 4개 그래프 한 화면에시 표시
```
> par(mfrow=c(2,2), mar=c(3,3,4,2))          # 화면 분할(2x2)

> hist(irirs$Sepal.Length,                   # 그래프 1
       main='Sepal.Length',
       col='orange')
       
> barplot(table(mtcars$cyl),                 # 그래프 2
          main='mtcars',
          col=c('red','green','blue'))
          
> barplot(table(mtcars$gear),                # 그래프 3
          main='mtcars',
          col=rainbow(3),
          horiz=TRUE)
          
> pie(table(mtcars$cyl),                     # 그래프 4
      main='mtcars',
      cpl=topo.colors(3),
      radius=2)
> par(mfrow=c(1,1), mar=c(5,4,4,2)+.1)      # 화면 분할 취초
```

## [2] 그래프 파일에 저장
- Plot Zoom 팝업 창 위에서 마우스 우클릭 -> [Copy Image] -> R 그래프 복사
- [Save image as..] : 파일로 저장 (확장자 : .png/.jpg)

# 원그래프
- 하나의 원 안에 데이터값이 차지하는 비율을 넓이로 나타낸 그래프

## [1] 원 그래프 작성하기
```
> favorite <- c('SWINTER', 'SUMMER', 'SPRING', 'SUMMER', 'SUMMER', 'FALL', 'FALL', 'SUMMER', 'SPRING', 'SPRING')      # 데이터 입력
> ds <- table(favorite)                                                                                               # 도수분포 계산
> ds
> pie(ds, main-='선호 계절', radius=1)                                                                                # 원그래프 작성
```
- 원그래프 작성하는 함수 -> pie()
- radius : -1~1 사이의 값으로 원의 크기와 데이터를 표시하는 방향을 조절 (보통 1)

## [2] 파이 조각의 색 지정하기
- 막대그래프와 동일

## [3] 3차원 원그래프 작성하기
```
> install.packages('plotrix')                       # pie3D 함수 사용하기 위한 패키지 설치

> library(plotrix)
> pie3D(ds, main='선호계절',
        labels=names(ds),                           # 파이별 레이블 지정
        labelcex=1.0,                               # 레이블의 폰트 크기
        explode=0.1,                                # 파이 간 간격
        radius=1.5,                                 # 파이의 크기
        col=c('brown','green','red','yellow')       # 파이의 색 지정
```

# 선그래프
- 연도별 인구 증가 추이와 같이 시간의 변화에 따라 수집된 데이터를 시각화하는데 주로 사용
- x축을 시간축으로 하여 선그래프를 그리면 시간 변화에 따른 증감 추이를 알 수 있음
---

<h2> 2023-04-13 </h2>

# 조건문
## [1] if-else문 

- 조건문의 기본구조
> if(비교 조건) {  
  조건이 참일 때 실행할 명령문(들)  
} else {  
  조건이 거짓일 때 실행할 명령문(들)  
}

## [2] ifelse문
- if-else문을 서술할 때 조건에 따라 선택할 값이 각각 하나씩이면 ifelse문을 이용하는 것이 편리함
- ifelse문의 문법
> ifelse(비교 조건, 조건이 참일 때 선택할 값, 조건이 거짓일 때 선택할 값)

# 반복문
## [1] for문
- for문 기본구조
> for(반복 변수 in 반복 범위) {  
  반복할 명령문(들)  
}

## [2] while문
- while문 문법
> while (비교 조건){  
  반복할 명령문(들)  
}

## [3] apply() 계열 함수
- 반복 작업의 대상이 매트릭스나 데이터프레임의 행이나 열인 경우 이용
- 매트릭스나 데이터프레임에 있는 행들이나 열들이 하나하나 차례로 꺼내어 평균이나 합계 등을 구하는 작업을 수행하고자 할 때 유용
- apply() 함수 문법
> apply(데이터셋, 행/열 방향 지정, 적용 함수)
- apply() 함수에서 사용되는 매개변수의 의미  
(1) 데이터셋 : 반복 작업을 적용할 대상인 매트릭스나 데이터프레임 이름을 입력한다  
(2) 행/열 방향 지정 : 행 방향 작업의 경우 1, 열 방향 작업의 경우 2를 지정한다  
(3) 적용 함수 : 반복 작업의 내용을 알려주는 것으로, R 함수이거나 사용자 정의 함수를 지정한다
- apply() 함수의 활용법
> apply(iris[,1:4], 1, mean) 　　　　　　# 행 방향으로 함수 적용  
> apply(iris[,1:4], 2, mean) 　　　　　　# 열 방향으로 함수 적용

# 사용자 정의 함수
## [1] 사용자 정의 함수 개념
- 두 개의 값을 입력받아 둘 중에서 큰 수를 결과값으로 돌려주는 함수
```
> mymax <-function(x,y){  
  num.max <- x  
  if (y>x) {  
    num.max <- y  
  }  
  return(num.max)  
}
```

## [2] 사용자 정의 함수의 저장과 재실행
- 사용자 정의 함수 사용 절차
(1) 함수 작성
(2) 함수를 실행하여 R에 함수 등록
(3) 필요한 곳에서 함수 호출

# 조건에 맞는 데이터의 위치 찾기
## [1] which() 함수
- 조건에 맞는 값이 벡터 안에서 몇 번째 위치하고 있는지 알아내는 함수
- which.max() 함수 : 벡터 안에서의 최댓값의 인텍스를 알아내는 함수
- which.min() 함수 : 벡터 안에서의 최솟값의 인텍스를 알아내는 함수

> score <- c(76,84, 69, 50, 95, 60, 82, 71, 88, 84)  
> which(score==69)  
[1] 3  
> which(score>=85)  
[1] 5 9  
> max(score)  
[1] 95  
> which.max(score)  
[1] 5  
> min(score)  
[1] 50  
> which.min(score)  
[1] 4

---
<h2> 2023-04-06 </h2>

# 데이터프레임
- 개념 : 매트릭스와 마찬가지로 2차원 형태의 데이터를 저장하고 분석하는데 사용되는 자료 구조
- 특징  
(1) 서로 다른 종류의 값이 함께 저장 될 수 있음  
(2) 숫자형 자료와 문자형 자료가 결합되어 있는 형태  
(3) 특정 열을 잘라서 보았을 때 값을의 자료형이 동일해야 함

## [1] 데이터 프레임 만들기
> city <- c("Seoul", "Tokyo", "Washington")　　　　　　# 문자로 이루어진 벡터  
> rank <- c(1,3,2)　　　　　　　　　　　　　　　　　 # 숫자로 이루어진 벡터  
>city.info <- data.frame(city, rank)　　　　　　　　　# 데이터프레임 생성

## [2] iris 데이터셋
- 4개의 숫자형 열과 1개의 문자형 열이 결합되어 있음

# 매트릭스와 데이터프레임 다루어보기

## [1] 데이터셋의 기본 정보 알아보기
> dim(iris) 　　　　　　# 행과 열의 개수 보이기  
> nrow(iris)　　　　　　# 행의 개수 보이기  
> ncol(iris)　　　　　　# 열의 개수 보이기  
> colnames(iris)　　　　# 열 이름 보이기, name() 함수와 결과 동일  
> head(iris)　　　　　　# 데이터셋의 앞부분 일부 보기  
> tail(iris)　　　　　　 # 데디터셋의 뒷부분 일부 보기

## [2] 매트릭스와 데이터 프레임에 함수 적용
### (1) 행별, 열별로 합계와 평균 계산하기
> colSums(iris[,-5]) 　　　　　　# 열별 합계  
> colMeans(iris[,-5]) 　　　　　　# 열별 평균  
> rowSums(iris[,-5]) 　　　　　　# 행별 합계  
> rowMeans(iris[,-5]) 　　　　　　# 행별 평균
* 합계와 평균을 계산할 때 iris[,-5]와 같이 5열을 제외하는 이유  
-> 5열은 품종을 나타내는 범주형 자료이다  
그래서 팩터 형태로 저장이 되어있는데, 범주형 자료는 합계나 평균 등의 산술연산이 적용될 수 없기 때문이다

### (2) 행과 열의 방향 변환하기
> z <- matrix(1:20, nrow=4, ncol=5)  
> z  
 　　[,1] [,2] 　[,3] 　[,4] 　[,5]  
[1,] 　1 　5 　9 　 13 　17  
[2,] 　2 　6 　10 　14 　18  
[3,] 　3 　7 　11 　15 　19  
[4,] 　4 　8 　12 　16 　20  
> t(z)  　　　　　　  　　　　　　# 행과 열 방향 변환  
　　[,1] 　[,2] 　[,3] 　[,4]   
[1,] 　1 　 2 　 　3 　  4  
[2,] 　5 　 6 　 　7 　 8  
[3,] 　9 　 10 　 11 　 12  
[4,] 　13 　14 　15 　16  
[5,] 　17 　18 　19 　20

### (3) 조건에 맞는 행과 열의 값 추출하기
- subset() 함수  
: 전체 데이터에서 조건에 맞는 행들만 추출하는 기능 제공
- subset()함수에서 매개변수의 의미
(1) iris : 데이터를 추출하는 대상이 iris 데이터셋입니다
(2) Species == 'setosa' : 데이터를 추출할 조건을 지정하는 부분으로, 품종 열의 값이 'setosa'인 행만 추출하라는 의미입니다

## [3] 매트릭스와 데이터프레임의 자료구조 확인과 변환
### (1) 매트릭스와 데이터프레임의 자료구조 확인하기
> class(iris) 　　　　　　# iris 데이터셋의 자료구조 확인   
[1] "data.frame"   
> is.matrix(iris) 　　　　　# 데이터셋이 매트릭스인지 확인하는 함수  
[1] FALSE  
> is.data.frame(iris) 　　　　# 데이터셋이 데이터프레임인지 확인하는 함수  
[1] TRUE

### (2) 매트릭스와 데이터프레임의 자료구조 변환하기

> [ # 매트릭스를 데이터프레임으로 변환 ]   
> is.matrix(state.x77)  
> st <- data.frame(state.x77)  
> head(st)  
> class(st) 

> [ # 데이터프레임을 매트릭스로 변환  ]   
> is.data.frame(iris[,1:4])  
> iris.m <- as.matrix(iris[,1:4])    
> head(iris.m)  
> class(iris.m) 

# 데이터 입출력
## [1] R에서의 입력과 출력
- 분석 대상이 되는 데이터를 입력한 후 입력된 데이터를 분석하여 필요한 정보를 얻는다. 이렇게 얻은 결과는 사용자가 알기 쉽게 출력된다.
- R 프로그램에서 데이터의 입력과 결과의 출력은 기본적인 구성 요소

## [2] print() 함수와 cat() 함수
|함수|사용상의 특징|
|:---:|---|
|print()|- 하나의 값을 출력할 때<br>- 데이터프레임과 같은 2차원 자료구조를 출력할 때<br>- 출력후 자동 줄바꿈|
|cat()|-여러 개의 값을 연결해서 출력할 때<br>(벡터는 출력되나 2차원 자료구조는 출력되지 않음)<br>- 출력 후 줄바꿈을 하려면 '\n' 필요|

## [3] 작업 폴더
- 개념 : 자신이 읽거나 쓰고자 하는 파일이 위치하는 폴더를 말함
- getwd() 함수 : 현재 작업 폴더가 어디인지 알아보는 명령어
- setwd() 함수 : 현재 작업 폴더를 내가 원하는 폴더로 변경할 때 사용

## [4] .csv 파일 읽기와 쓰기
### (1) .csv 파일
- R에서 데이터 분석을 위해 가장 많이 사용하는 파일 형태
- 콤마로 열과 열을 구분한 파일
### (2) .csv 파일 데이터 읽기
> setwd('D:/602377101_ksh/Rworks')  
> air <- read.csv('airquality.csv', header = T)  
> head(air)  
  Ozone Solar.R Wind Temp Month Day  
1    41  　190 　7.4 　 　67 　 　5 　1  
2    36  　118 　8.0 　 　72 　 　5 　2  
3    12 　149 　12.6 　 　74 　 　5 　3  
4    18 　313 　11.5 　 　62 　 　5 　4  
5    NA 　NA 　14.3 　 　56 　  　5 　5  
6    28  　 NA 　14.9 　 　66 　 　5 　6  
> class(air)  
[1] "data.frame"
---
<h2> 2023-03-30 </h2>

# R Studio 명령어  
- list 조회하기  
> ls()
- list 삭제
> rm(해당되는 리스트 명 작성)
- 전체 list 삭제
> rm(list = ls())

# R에서의 자료구조
- 1차원 자료 : 벡터, 리스트, 팩터
- 2차원 자료 : 매트릭스, 데이터프레임

## 1차원 자료 vs 2차원 자료
- 1차원 자료 : 단일 주제에 대한 값들을 모아 놓은 것
- 2차원 자료 : 복수 주제에 대한 값들을 모아 놓은 자료

## 범주형 자료 vs 수치형 자료
- 범주형 자료 : '분류'의 의미를 갖는 값들로 구성된 자료로, 보통 문자로 표현되고 산술연산 적용 X
- 수치형 자료 : 값들이 크기를 가지며 산술 연산 가능

# 백터 연산
## 백터에 적용 가능한 함수
|함수명|설명|
|:---:|---|
|sum()|백터에 저장된 값들의 합|
|mean()|백터에 저장된 값들의 평균|
|max(),min()|백터에 저장된 값들의 분산|
|sort()|백터에 저장된 값들을 정렬(오름차순이 기본)|
|length()|백터에 저장된 값들의 개수(백터의 길이)|

## 백터에 논리연산자 적용
- 논리연산자 : 연산의 결과값이 TRUE/FALSE인 연산자

# 팩터
## 개념
- 문자형 데이터가 저장되는 벡터의 일종으로 저장되는 문자값들이 어떠한 종류를 나타내는 값일 때 사용

### - 팩터 생성
> bt <- c('A', 'B', 'B', 'O', 'AB', 'A')
&nbsp;&nbsp;&nbsp;&nbsp;# 문자형 벡터 bt 정의
> bt.new <- factor(bt)
&nbsp;&nbsp;&nbsp;&nbsp;# 팩터 bt.new 정의
- levels( )함수 : 팩터에 저장된 값들의종류를 알아내는 함수(백터에 적용 X)  
예)
> levels(bt.new)
&nbsp;&nbsp;&nbsp;&nbsp;# 팩터에 저장된 값의 종류를 출력  
[1] "A", "AB", "B", "O"

# 리스트
## 개념
- 자료형이 다른 값들을 한곳에 저장하고 다룰 수 있도록 해주는 수단

### - 리스트 생성
> h.list <-c('balling', 'tennis', 'ski')
&nbsp;&nbsp;&nbsp;&nbsp;# 취미를 백터에 저장  
> person <- list(name='Tom', age=25, student=TRUE, hobby=h.list)
&nbsp;&nbsp;&nbsp;&nbsp;# 리스트 생성

# 매트릭스
### 매트릭스 vs 데이터 프레임
- 공통점 : 2차원 자료를 저장하기 위한 대표적인 자료구조
- 차이점 : 매트릭스에 저장되는 모든 자료의 종류가 동일한 반변 데이터프레임에는 서로 다른 종류의 데이터가 저장될 수 있음  
=> R의 자료구조에서는 여러 개의 벡터를 모아 놓은 것을 말함

## 매트릭스 만들기
### 특징
- 2차원 테이블 형태의 자료구조
- 모드 셀에 저장되는 갑은 동일한 종류이어야 함
- 보통 숫자로만 구성된 2차원자료

### 매트릭스 생성
> z <- matrix(1:20, nrow = 4, ncol = 5)  
> z
&nbsp;&nbsp;&nbsp;&nbsp;# 매트릭스 z의 내용을 출력  
    [,1] [,2] [,3] [,4] [,5]  
[1,]    1    5    9   13   17  
[2,]    2    6   10   14   18  
[3,]    3    7   11   15   19  
[4,]    4    8   12   16   20  
---
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
ex) 1, 2, -4  
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
> mean(score) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# 평균 출력
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

### * 참고사항
> foo = 10  
> fo <- 10

=> 모두 사용 가능

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
