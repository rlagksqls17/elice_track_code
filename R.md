# R  for data analysis  

## 패키지

### 사용가능한 패키지 리스트

```R
as.data.frame(installed.packages()[,c(3:4)])
```
askpass              1.1        <NA>
base64enc          0.1-3        <NA>
BH              1.75.0-0        <NA>
brio               1.1.2        <NA>
callr              3.7.0        <NA>
caret             6.0-86        <NA>
CARRoT             2.5.1        <NA>
Ckmeans.1d.dp      4.3.3        <NA>
cli                2.5.0        <NA>
clipr              0.7.1        <NA>
colorspace         2.0-0        <NA>
commonmark           1.7        <NA>
cpp11              0.2.7        <NA>
crayon             1.4.1        <NA>
cyclocomp          1.1.0        <NA>
data.table        1.14.0        <NA>
desc               1.3.0        <NA>
DiagrammeR       1.0.6.1        <NA>
diffobj            0.3.4        <NA>
digest            0.6.27        <NA>
doParallel        1.0.16        <NA>
downloader           0.4        <NA>
dplyr              1.0.5        <NA>
e1071              1.7-6        <NA>
ellipsis           0.3.1        <NA>
evaluate            0.14        <NA>
fansi              0.4.2        <NA>
farver             2.1.0        <NA>
float              0.2-4        <NA>
foreach            1.5.1        <NA>
generics           0.1.0        <NA>
ggplot2            3.3.3        <NA>
glue               1.4.2        <NA>
gower              0.2.2        <NA>
gridExtra            2.3        <NA>
gtable             0.3.0        <NA>
highr                0.9        <NA>
hms                1.0.0        <NA>
htmltools        0.5.1.1        <NA>
htmlwidgets        1.5.3        <NA>
httpuv             1.6.0        <NA>
hunspell           3.0.1        <NA>
igraph             1.2.6        <NA>
influenceR         0.1.0        <NA>
ipred             0.9-11        <NA>
isoband            0.2.4        <NA>
iterators         1.0.13        <NA>
jpeg             0.1-8.1        <NA>
jsonlite           1.7.2        <NA>
knitr               1.33        <NA>
labeling           0.4.2        <NA>
later              1.2.0        <NA>
lava               1.6.9        <NA>
lazyeval           0.2.2        <NA>
lifecycle          1.0.0        <NA>
lmtest            0.9-38        <NA>
lubridate         1.7.10        <NA>
magrittr           2.0.1        <NA>
markdown             1.1        <NA>
mime                0.10        <NA>
mockery            0.4.2        <NA>
ModelMetrics     1.2.2.2        <NA>
munsell            0.5.0        <NA>
numDeriv      2016.8-1.1        <NA>
pillar             1.6.0        <NA>
pkgconfig          2.0.3        <NA>
pkgload            1.2.1        <NA>
plyr               1.8.6        <NA>
png                0.1-7        <NA>
praise             1.0.0        <NA>
pROC            1.17.0.1        <NA>
processx           3.5.1        <NA>
prodlim       2019.11.13        <NA>
promises         1.2.0.1        <NA>
proxy             0.4-25        <NA>
ps                 1.6.0        <NA>
purrr              0.3.4        <NA>
R6                 2.5.0        <NA>
randomForest      4.6-14        <NA>
rbibutils          2.1.1        <NA>
RColorBrewer       1.1-2        <NA>
Rcpp               1.0.6        <NA>
Rdpack             2.1.1        <NA>
readr              1.4.0        <NA>
recipes           0.1.16        <NA>
rematch2           2.1.2        <NA>
remotes            2.3.0        <NA>
reshape            0.8.8        <NA>
reshape2           1.4.4        <NA>
rex                1.2.0        <NA>
rlang             0.4.10        <NA>
rmarkdown            2.7        <NA>
rprojroot          2.0.2        <NA>
rstudioapi          0.13        <NA>
scales             1.1.1        <NA>
SQUAREM           2021.1        <NA>
stringi            1.5.3        <NA>
stringr            1.4.0        <NA>
sys                  3.4        <NA>
testthat           3.0.2        <NA>
tibble             3.1.1        <NA>
tidyr              1.1.3        <NA>
tidyselect         1.1.0        <NA>
timeDate        3043.102        <NA>
tinytex             0.31        <NA>
titanic            0.1.0        <NA>
utf8               1.2.1        <NA>
vcd                1.4-8        <NA>
vctrs              0.3.7        <NA>
viridis            0.6.0        <NA>
viridisLite        0.4.0        <NA>
visNetwork         2.0.9        <NA>
waldo              0.2.5        <NA>
withr              2.4.2        <NA>
xfun                0.22        <NA>
xgboost          1.4.1.1        <NA>
xmlparsedata       1.0.5        <NA>
yaml               2.2.1        <NA>
zoo                1.8-9        <NA>
base               3.6.3        base
boot              1.3-25 recommended
class             7.3-17 recommended
cluster            2.1.0 recommended
codetools         0.2-18 recommended
compiler           3.6.3        base
datasets           3.6.3        base
foreign           0.8-76 recommended
graphics           3.6.3        base
grDevices          3.6.3        base
grid               3.6.3        base
KernSmooth       2.23-18 recommended
lattice          0.20-41 recommended
MASS              7.3-53 recommended
Matrix             1.3-2 recommended
methods            3.6.3        base
mgcv              1.8-33 recommended
nlme             3.1-151 recommended
nnet              7.3-14 recommended
parallel           3.6.3        base
rpart             4.1-15 recommended
spatial           7.3-11 recommended
splines            3.6.3        base
stats              3.6.3        base
stats4             3.6.3        base
survival           3.2-7 recommended
tcltk              3.6.3        base
tools              3.6.3        base
utils              3.6.3        base

### 패키지 다루는 법  

```R
"""
패키지는 설치와 로드의 과정을 거친 후 사용 가능  
"""

# 패키지 설치
install.packages("패키지 명")

# 패키지 로드  
library(dplyr)  

# 패키지 업데이트  
update.packages("패키지 명")

# 설치된 목록 확인  
search()
```

## R 기초  

### 스크립트 다루기  

```R
"""
R 
Code 한 줄 실행 : 컨트롤 + R
Code 여러 줄 실행 : 드래그 후 컨트롤 + R  
주석 : #  
도움말 help(함수명)
명령어의 끝 명시 : ;
"""

# 현재 작업 중인 폴더의 경로 산출 
getwd()

# 현재 작업 중인 폴더에 있는 파일 목록 산출  
dir()  

# 파일 이름 확인하기  
list.files()  

# 변수 목록 보기  
ls()  

# 메모리의 모든 객체 삭제  
rm(list=ls())  
```

### 변수  생성

```R
"""
지수 : '^'
단항 플러스와 마이너스 부호 : '+', '-'
수열 생성 : '1:30'
특수 연산자 : '%any%'
	%/% = 나눗셈의 몫
	%% = 나눗셈의 나머지 
	%*% = 행렬곱 
곱하기, 나누기 : '*', '/'
더하기, 빼기 : '+'. '-'
좌우의 값이 같은지 비교 : 3==5 (return Boolean)  
좌우의 값이 다른지 비교 : 3!=5 (return Boolean)
					  3<>5 (return Boolean)
이상, 이하 비교 : 3<=5, 3>=5 (return Boolean)  
논리 부정 : '!' ex) !(3==4)
논리 AND 
	'&' : 논리 연산 데이터가 하나 이상인 경우 사용 
	'&&' : 논리 연산 데이터가 하나인 경우 사용
논리 OR  
	'|' : 논리 연산 데이터가 하나 이상인 경우 사용
	'||' : 논리 연산 데이터가 하나인 경우 사용  
왼쪽 값을 오른쪽으로 대입 3->a a=3  
오른쪽값을 왼쪽으로 대입 a<-3
"""

# 함수 내 인자 호출  
# x값은 10, y값은 1, z값은 TRUE 지정하여 abc 함수에 인수로 전달
abc(x=10, y=1, z=TRUE)

# 같은 의미
abc(10, 1, TRUE)
abc(10, y=1)
```

### 데이터 타입  

#### 스칼라  

R의 기본 데이터 타입은 벡터인데, 스칼라는 길이가 1인 벡터와 같음   

```R
# 숫자형  
a <- 1     # 정수 1 저장
b <- 2.7   # 소수 2.7 저장
mode(a)    # a 변수의 데이터 타입 확인
mode(b)    # b 변수의 데이터 타입 확인
[1] "numeric"


# 문자형  
a <- "가" # a라는 변수에 "가" 저장  
mode(a)
[1] "character"

	# 문자형 붙이기  
	hello <- "hello"
	x1 <- paste("a", hello, "b", sep="") # sep 사용하여 구분자 제거
	x1
	[1] "ahellob"

# 논리형  
a = TRUE  
mode(a)
[1] "logical"

# 팩터형
"""
범주형 자료를 표현하기 위한 데이터 타입
factor(data, levles, labels, ordered)

options:
	data = 범주형으로 표현하고자 하는 데이터
	levels = 구분하고자 하는 범주 목록을 지정
	labels = 범주별 표시값 지정
	ordered 
		TRUE = (상, 중, 하)와 같이 순서를 정할 수 있는 값  
		FALSE = (왼쪽, 오른쪽)과 같이 값에 대한 크기 비교를 할 수 없는 값  
"""  
factor(c("m", "m", "f", "f", "f"), levels=c("f", "m"),
      labels=c("여", "남"), ordered=F)  
[1] 남 남 여 여 여  
levels: 여 남  

# 결측치  
NA : 데이터 값이 없음을 의미 (상수)  
NULL : 정의되지 않은 값을 나타냄 (객체)
NAN : 수학적으로 계산이 불가능한 값  
INF : 무한대를 의미

# 데이터타입확인, 데이터 타입 확인, 데이터 타입
mode(객체명) # 객체의 데이터 타입 확인
is.numeric(객체명) # 객체가 숫자형 벡터인지 판단  
is.integer(객체명) # 객체가 정수형 벡터인지 판단  
is.double(객체명) # 객체가 실수형 벡터인지 판단  
is.character(객체명) # 객체가 문자형 벡터인지 판단  
is.factor(객체명) # 객체가 팩터인지 판단  
is.logical(객체명) # 객체가 논리형인지 판단  
is.null(객체명) # 객체가 NULL인지 판단  
is.na(객체명) # 객체가 NA인지 판단  

# 데이터타입 변환, 데이터 타입 변환, 데이터 타입  
as.numeric(객체명) # 객체를 숫자형으로 변환  
as.integer(객체명) # 객체를 숫자형(정수)로 변환  
as.double(객체명) # 객체를 숫자형(실수)로 변환  
as.character(객체명) # 객체를 문자형으로 변환  
as.factor(객체명) # 객체를 팩터로 변환   
```

#### 벡터

벡터는 R 프로그래밍의 기본적인 데이터 단위로 **다른 프로그래밍 언어의 1차원 배열**과도 같은 개념  

하나의 벡터는 같은 데이터 타입을 가진 원소들만 저장 가능  

예를 들어 문자열만 저장하는 배열 혹은 숫자들만 저장하는 배열이 벡터라고 할 수 있음  

```R
# c()를 사용한 벡터 저장
a = c(1, 2, 3)
a
[1] 1 2 3

# :를 사용한 벡터 저장
b = 1:3
b
[1] 1 2 3

# c(1, 2, 3)을 3번 반복   
rep(c(1, 2, 3), 3)
[1] 1 2 3 1 2 3

# 1을 1번 반복, 2를 2번 반복  
rep(c(1, 2), c(1, 2))  

# 1부터 10까지 2씩 증가하는 수열을 변수 c에 저장  
c = seq(1, 10, 2)  

----------------------------------------------------
# 인덱싱
# z 벡터 생성하고 두 번째 원소 출력  
> z = c(1: 5)
> z[2]
[1] 2

# z 벡터의 첫 번째, 세 번째 원소 출력  
> z[c(1, 3)] # 첫 번째 방법
> z[1:3] # 두 번째 방법  
[1] 1 3  

# z 벡터의 다섯 번째 원소만 제외하고 출력  
> z[-5]
[1] 1 2 3 4

# z 벡터의 원소 중 3보다 큰 값만을 출력  
> z[z>3]
[1] 4 5  

# names()를 이용하여 벡터의 각 원소에 대한 이름을 부여 가능  
	# 1 ~ 3 까지의 값이 저장된 벡터 x 생성
	> x <- c(1, 2, 3)
	# x의 각 요소에 대해 Kim, Park, Lee 라는 이름을 지정  
	> names(x) <- c("Kim", "Park", "Lee")  
	# x벡터에서 이름이 Kim인 원소 출력  
	> x["Kim"]
	Kim
	  1

# 벡터의 연산
벡터 간 연산을 실행할 때는 같은 위치의 원소들을 대응시켜 계산 함  
 2 4 6 8
    +  
 1 3 7 9
    =   
3 7 13 17  

# 벡터 간 연산의 예시 1
> x = c(1:4)
> x
[1] 1 2 3 4

> x*3
[1] 3 6 9 12

> x+5
[1] 6 7 8 9  

# 벡터 간 연산의 예시 2  
> y=c(5:8)

> x + y
[1] 6 8 10 12  
```

##### 벡터의 집합 연산  

```R
# x와 y가 동일하면 TRUE, 동일하지 않으면 FALSE를 반환  
identical(x, y) 

# x와 y의 합집합 데이터를 산출 (x, y는 벡터)
union(x, y)

# x와 y의 교집합 데이터를 산출 (x, y는 벡터)
intersect(x, y)

# x와 y의 차집합 데이터를 산출 (x, y는 벡터)
setdiff(x, y)

# x와 y가 같은 집합인지를 판단하여 TRUE 혹은 FALSE를 반환  
setequal(x, y)
```

##### 벡터의 기초통계  

```R
mean(x) # 벡터의 평균
sum(x) # 벡터의 합계  
max(x) # 벡터의 최댓값
min(x) # 벡터의 최솟값 
median(x) # 벡터의 중앙값  
abs(x) # 벡터의 절댓값  
log(x) # 벡터의 로그  
sd(x) # 벡터의 표준편차  
var(x) # 벡터의 분산 
cov(x, y) # 벡터의 공분산  
cor(x, y) # 벡터의 상관계수  
length(x) # 벡터 변수의 길이 값  
```

#### 행렬  

2차원의 벡터로 행과 열의 수가 지정된 구조의 데이터 타입  

벡터와 마찬가지로 하나의 행렬은 한 가지 유형의 스칼라 데이터만 저장 가능  

```R
matrix(data, nrow, ncol, byrow, dimnames)  

data : 행렬에 저장할 데이터  
nrow : 행의 수
ncol : 열의 수  
byrow : 행렬의 데이터 입력 순서 (TRUE : 행우선, FALSE: 열우선)
dimnames : 행렬의 각 차원에 부여할 이름 지정  


# 행렬 생성  
> matrix(1:9, nrow=3, ncol=3, dimnames=list(c("r1", "r2", "r3"), c("a", "b", "c")))

    a  b  c
r1  1  4  7  
r2  2  5  8
r3  3  6  9  


# 행렬 다루기  
행렬 차원 확인 및 부여  :  dim(x) <- c(3, 2) # x 행렬에 3 x 2 차원 부여  
행의 수 확인 : nrow(x) (부여 시 <- 추가) 
열의 수 확인 : ncol(x) (부여 시 <- 추가)
행렬의 원소 추출 : x[nrow, ncol] # x행렬의 3행3열의 원소 추출  
행렬의 특정 행 접근 : 
	x[nrow,] # x 행렬의 3행 추출
	x[-nrow,] # x 행렬의 3행을 제외한 나머지 행 추출  
행렬의 특정 열 접근 : 
	x[,ncol] # x 행렬의 3열 추출  
	x[,-ncol] # x 행렬의 3열을 제외한 나머지 열 추출  
행렬의 각 차원의 이름 확인 및 부여  (부여 시 <- 추가) 
	dimnames(x)<-list(c("r1", "r2", "r3"), c("a", "b", "c"))
행 이름 출력 및 부여 (부여 시 <- 추가)
	rownames(x)<-c("r1", "r2", "r3")
열 이름 출력 및 부여 (부여 시 <- 추가)
	colnames(x)<-c("a", "b", "c")


# 행렬의 연산
# 행렬 x가 존재할 경우
전치행렬 : t(X)  
대각행렬 : diag(x)  
역행렬 : solve(x)  
+, - 연산
	# x 행렬과 y 행렬의 각 원소 간의 덧셈
	x + y  
	# x 행렬과 y 행렬의 각 원소 간의 뺄셈  
	x - y  
	# x 행렬의 각 원소에 숫자 3을 더함  
	x + 3  
*, / 연산
	# x 행렬의 각 원소에 숫자 3을 곱함  
	x * 3  
행렬곱 : x %*% y  
```

#### 데이터 프레임  

데이터프레임은 벡터들의 모임이며, **데이터프레임에 속한 벡터들은 서로 다른 데이터 타입을 가질 수 있다.**  

**벡터는 데이터 프레임의 열을 이루며, 열은 변수, 행은 개체에 해당한다.**  

```R
data.frame(변수명1 = 벡터1, 변수명2 = 벡터2, ... 변수명 n = 벡터 n,
          stringsAsFactors=default.stringsAsFactors())
options:
	stringsAsFactors 
		FALSE : 문자열은 문자형으로 저장  
		TRUE : 문자열은 팩터형으로 저장

# 데이터프레임 생성  
x <- data.frame(이름 = c("이유리", "최민준", "김민지"),
               전공 = c("경영학과", "컴퓨터공학과", "데이터과학과"),
               성별 = c("여", "남", "여"), 나이=c(20, 22, 21))

# 데이터 출력 
> x 
	이름			전공	성별	나이
1  이유리		경영학과    여    20
2  최민준	 컴퓨터공학과	  남    22
3  김민지	 데이터과학과	  여    21

# 데이터의 구조 확인  
str(x)  

# pandas의 iloc과 유사한 기능
    # x의 3행 6열의 원소 출력
    x[3, 6]
    # x의 3행을 제외한 데이터 출력
    x[-3,]
    # x의 6열의 모든 행 출력  
    x[,6]

# pandas의 loc과 유사한 기능  
	# iris 데이터의 Species열 출력  
	iris$Species  

# 열이름 출력 및 부여 (부여 시 <- 추가)
colnames(x)<-c("a", "b", "c")  

# 행결합  
rbind(df1, df2, ...)
**결합할 두 객체의 열의 개수와 열의 이름이 동일해야 함  

# 열결합  
cbind(df1, df2, ...)
**결합할 두 객체의 행의 개수가 동일해야 함  

# 데이터 조회 
dataFrame[조건]
	# ex : x 데이터프레임에서 var1이 4보다 크고, var2가 5인 조건을 만족하는 레코드
	x[x$var1>4 & x$var2==5]  

subset(데이터명, 조건)
	# ex : x 데이터프레임에서 var1이 4보다 크고, var2가 5인 조건을 만족하는 레코드  
	subset(x, var1>4 & var2==0)

subset(데이터명, 조건, select = 열 이름)
	# ex : x 데이터프레임에서 var1이 4보다 큰 레코드의 
	# 		var2, var3 데이터 셋 조회
	# 		이때 변수명에 ""를 표시하지 않음  
	subset(x, var1>4, select=c(var2, var3))

# 데이터프레임의 상위 행을 반환  
head(데이터프레임명, n=반환할 행의 개수)
	# ex : x데이터의 상위 10개의 행 반환, n 인자의 기본값은 6  
	head(x, n=10)

# 데이터프레임의 하위 행을 반환
tail(데이터프레임명, n=반환할 행의 개수)
	# ex : x데이터의 하위 10개의 행 반환, n 인자의 기본값은 6  
	tail(x, n=10)  

# 데이터 뷰어 호출  
View(iris)

# 데이터 병합  
merge(df1, df2, by="df1과 df2의 공통 열이름(병합할 기준이 되는 열)")
	# ex : x와 y를 z라는 공통변수를 기준으로 병합  
	merge(x, y, by=z)

# NA값이 있는 행 삭제  
na.omit(데이터프레임)
	# ex : df에서 NA가 있는 행을 삭제하여 NA_Cleaning 변수에 저장
	NA_Cleaning<-na.omit(df)
```

#### 리스트  

벡터, 데이터프레임, 배열, 함수 등과 같은 R의 모든 객체를 담을 수 있는 데이터 구조  

```R
# 사용법  
list(key1 = value1, key2 = value2, ... , keyN = valueN)

    # 문자형 벡터 생성
    v1 <- c("가", "나", "다")
    v2 <- c(T, F, F)

    # 데이터프레임 생성  
    df<-data.frame(subject=c("미술", "음악", "체육"), class=c("1교시", "2교시", "3교시"))  

    # key를 지정하지 않고 리스트 생성  
    ls1 <- list(v1, v2, df, sum)  

    # key를 지정하여 리스트 생성  
    ls2 <- list(v1=v1, v2=v2, df=df, fun=sum)

# 리스트 다루기  
    # a라는 리스트에서 키 값이 key에 해당하는 원소 출력
    a&key

    # a라는 리스트에서 n번째 키 값에 해당하는 원소 출력
    a[n]

    # key값의 이름으로 원소 선택
    a[['key']]
    a$key
```

#### 배열  

행렬이 2차원이라면 배열은 3차원 또는 n차원 까지 확장된 형태의 다차원 데이터  

```R
array(data=NA, dim=length(data), dimnames=NULL)
"""
options
	data : 배열에 저장할 데이터 지정  
	dim : 배열의 차원을 c()로 묶어서 지정  
	dimnames : 차원의 이름 지정  
"""

# ex  
rname=c("1행", "2행", "3행")
cname=c("1열", "2열", "3열")
mname=c("matrix_1", "matrix_2", "matrix_3")
ar<-array(1:27, dim=c(3, 3, 3), dimnames=list(rname, cname, mname))
```

### 자주사용하는 함수  

```R
print(객체) # 객체를 콘솔에 출력  
cat(객체1, 객체2, ...) # 인자로 주어진 객체들을 연결하여 콘솔에 출력  
rm(변수) # 변수 삭제  
class(객체) # 객체의 물리적자료형 확인  
mode(객체) # 객체의 추상적자료형 확인  
data(데이터명) # R에 내장된 데이터 셋을 불러들임  
attach(데이터명) # 데이터를 R 검색경로에 추가하여 변수명만으로 바로 데이터에 접근 가능하도록 함  
detach(데이터명) # 데이터를 R 검색경로에서 제거  
length(벡터) # 벡터의 길이 산출  
nrow(데이터) # 행의 개수 산출
ncol(데이터) # 열의 개수 산출  
order(벡터) # 벡터에 저장된 값들을 정렬한 순서대로 순서값 부여  
sort(벡터) # 지정한 데이터를 정렬  
summary(데이터 명) # 데이터의 기초통계량 산출  
append(원본벡터, 추가할 벡터, 새로운 벡터를 추가할 위치)
# ex)  
> a <- c(1, 2, 5, 6)
> b <- c(3, 4)
> append(a, b, 3)
[1] 1 2 5 3 4 6  

table(객체) # 객체에 대한 도수분포표 생성  
table(객체1, 객체2) # 두 객체에 대한 이원 분할표 생성  
prop.table(table) # 도수분포표에 대한 범주별 비율 계산

# 데이터를 기준에 따라 분리
split(데이터프레임, 기준) 
split(문자열벡터, 기준)

# 데이터에서 by인자에 지정한 컬럼을 기준으로 지정한 함수를 적용  
aggregate(데이터, by="기준정렬", FUN=적용함수)
aggregate(데이터, data, FUN) # 데이터 전체에 적용  
```

### 문자열 다루기  

```R
문자열길이 반환 : nchar("문자열")
join : paste("문자열1", "문자열2", ..., sep=" ")
split : strsplit("문자열", 구분자)

# str(문자열)에서 대상문자열을 찾아 변경문자열로 한 번만 대치
replace : sub("대상문자열", "변경문자열", str)

# str에 있는 모든 대상문자열을 변경문자열로 대치  
		gsub("대상문자열", "변경문자열", str) 

# str에서 찾을 문자열이 포함된 문자열 혹은 인덱스 출력 
grep("찾을 문자열", str)  
```

### 데이터 입출력

```R
# 경로 확인하기
getwd()

# 폴더 안에 어떤 파일 있는지 확인하기
list.files()

# csv 데이터 파일 읽기  
read.csv("파일명", header=FALSE, sep="구분자", stringAsFactors=TRUE, ...)
"""
options
	header : 첫 행을 변수명으로 지정할지에 대한 여부  
	sep : 데이터셋을 불러올 때 사용할 열 구분자  
	stringsAsFactors : 문자형 데이터를 팩터로 인식하여 데이터를 불러올지에 대한 여부 
"""  

# csv 데이터 파일 저장  
write.csv(저장할 데이터, file="파일경로/파일명", sep="구분자", row.names=TRUE, col.names=TRUE, ...)
```

### 함수 정의 문법 

```R
function(인자1, 인자2, 인자3, ..., 인자n){
    표현식1 
    표현식2
    ... 표현식n
    return(반환 값)
}
```

### 조건문  

```R
# if/else
if(조건1){
    조건1이 참일 때 수행할 코드
} else if (조건2) {
    조건1이 거짓이고
    조건2가 참일 때 수행할 코드
} else {
    모든 조건이 거짓일 때 수행할 코드  
}  

# ifelse  
ifelse(조건, a, b) 
"""
조건이 참이면 a자리의 코드를 실행하고, 거짓이면 b자리의 코드를 실행
내부에 또 다른 ifelse 구문을 중첩하여 사용이 가능  
"""
```

### 반복문  

```R
# for  
for(변수 in 데이터){
    반복할 코드  
}

# while
변수 <- 초기값

while(조건){
    조건이 참일 때 수행할 코드  
}

# repeat  
repeat{
    반복할 코드  
}  
"""
끝없이 실행되기 때문에 주로 if문, break문과 함께 사용  
"""  
```

## 데이터 변환  

### 파생변수 추가

```R
# $
데이터프레임$변수명<-추가할 변수의 데이터 벡터

# []
데이터프레임["변수명"]<-추가할 변수의 데이터 벡터  

# transform  
transform(데이터프레임, var1=data1, var2=data2, ...)
# ex
transform(iris, Sum.Length=Sepal.Length + Petal.Length)

# within  
within(데이터, 표현식)
# ex
score_df <- within(score_df, {
    grade = character(0)
    grade[score < 60] = "가"
    grade[score >= 60 & score < 70] = "양"
})
```

### 주성분분석  

```R
prcomp(데이터, center=TRUE, scale.=FALSE, ...)
"""
options
	데이터 : 주성분분석을 수행할 행렬 혹은 데이터프레임
	center : 값을 TRUE로 지정할 경우 데이터의 중심이 0이 되게 함  
	scale : 값을 TRUE로 지정할 경우 데이터를 표준화함
"""

princomp(데이터, cor=FALSE, scores=TRUE, ...)
"""
options
	데이터: 주성분분석을 수행할 행렬 혹은 데이터프레임
	cor:
		FALSE: 공분산행렬로 주성분 분석 수행
		TRUE: 상관행렬로 주성분 분석 수행
		공분산행렬은 변수의 측정 단위를 반영한 것이고,
		상관행렬은 변수의 측정 단위를 표준화한 것임
	scores: 각 주성분의 점수를 계산해야 하는지의 여부를 나타내는 논리 값  
"""

# ex  
# 주성분분석 객체를 만듦
Us.prin<-princomp(USArrests, cor=TRUE)
# 결과에 대한 요약 확인  
summary(Us.prin)
# 로딩을 통해 주성분 계수 가중치를 확인  
Us.prin$loadings  
# 차원축소로 얻어지는 주성분 점수를 확인  
Us.prin$scores  


```

### 요인분석  

```R
factanal(데이터, factors=n, rotation="varimax", scores="regression", ...)
"""
options
	데이터 : 요인분석을 수행할 숫자형 행렬 혹은 데이터 프레임
	factors : 요인의 개수 지정  
	rotation : 요인 회전방법을 선택 ("varimax", "promax", "none")
	scores : 요인점수 계산방법을 선택 ("regression", "Bartlett")
"""
```

### 표준화와 정규화  

```R
# 표준화 : 평균을 기준으로 거리 조정
scale(데이터, center=TRUE, scale=TRUE)
"""
options
	데이터 : 숫자형 벡터
	center : TRUE 면 데이터에서 해당 벡터의 평균을 뺌  
	scale
		center=TRUE, scale=TRUE 이면 데이터를 해당 벡터의 표준편차로 나눔
		cneter=FALSE, scale=TRUE 이면 데이터를 해당 벡터의 제곱평균제곱근(RMS)으로 나눔
		scale=FALSE이면 데이터를 어떤 값으로도 나누지 않음  
"""

# 정규화 : 데이터의 분포를 조정
# ex) Min, Max 정규화 (Xi - min) / (max - min)
> Min<-min(iris$Sepal.Length)
> Max<-max(iris$Sepal.Length)
> iris$SL_new<-scale(iris$Sepal.Length, center=Min, scale=Max-Min)

# ex) 사용자 정의 함수를 이용해서도 가능
> normalize<-function(x){
+ return((x - min(x)) / (max(x) - min(x)))
+ }
> num=c(50:500)
> num_new<-normalize(num)
> head(num_new)
[1] 0.000000000 0.002222222 0.004444444 0.006666667 0.008888889 0.011111111
```



## 데이터 시각화  

### 산점도

```R
# 데이터 확인 및 산점도를 통한 변수 간 상관관계 파악
library(datasets)
data(USArrests)
head(USArrests)

# pairs(): 둘 이상의 변수에 대해 모든 가능한 산점도를 그려줌  
pairs(USArrests, panel=panel.smooth, main="제목")
```

### 행렬도  

```R
# 제1주성분과 제2주성분으로 이루어진 좌표평면 상에 원 데이터 행들의 주성분점수를 산점도의 형태로 나타내고, 각 변수에 대한 주성분계수를 화살표로 시각화하여 그래프로 표현해줌
biplot(US.prin, scale = 0)
```

## **마이블로그 2팀 1차 스터디 발표**

------

### 1️⃣ 스터디를 통해 이루고 싶었던 목표

- 기술 블로그 개설하기
- 꾸준히 블로그에 글 올리기
- 배운 것을 블로그에 정리하여, 학습에 대한 완성도 높이기
- 학습 및 프로젝트 관련 기록 포트폴리오 작성
- CS 공부
- 다른 블로그를 참고하며 기술 블로그에 작성된 콘텐츠 알아보기
- 혼자 공부한 내용을 다른 사람도 읽고 이해할 수 있도록 정리하기

### 2️⃣ 4주 동안 스터디를 하며 이룬 것

- 편향적이지 않고 다양한 내용에 대한 꾸준한 블로그 포스팅
- 공부한 것을 글로써 표현하는 능력 (글쓰는 능력 향상) 및 정보 검색 능력의 향상
- 스터디원들을 통한 학습에 대한 자극
- 개인 블로그, github 블로그 개설  및 주 1회 이상 블로그 포스팅
- 개인 블로그 제작 프로젝트 및 기타 프로젝트 시작

### 3️⃣ 스터디를 진행하며 느낀 점

### 😋 좋았어요

- 스터디원들끼리 블로그 댓글을 통해 소통할 수 있었다.
- 스터디원들의 블로그를 통해 본인이 작성했던 내용에 대한 재학습  및 모르는 내용에 대한 학습이 이루어질 수 있었다.
- 다른 스터디원들의 블로그 포스팅을 통한 포스팅 방법, 포스팅 주제 등을 참고 및 경험할 수 있었다.
- 학습한 내용을 타인이 알 수 있게끔 설명하는 과정을 통해 학습의 완성도를 높일 수 있었다.
- 꾸준히 무엇인가를 기록하고, 흔적으로써 성취에 대한 흔적을 남겼다.
- 작문 및 정보 검색 능력 향상이 될 수 있는 기회였다.

### 😔 아쉬웠어요

- 새로운 것들을 많이 배우다보니, 모든 것을 소화할 수 없었고, 모든 것들에 대해 포스팅할 시간이 부족했다.
- 정해진 스터디 목표를 다 이루지 못했다.
- 코드가 삽입된 글을 작성해보지 못했다.
- 같은 주제로 공부하고 의견을 교환하지 못하고, 개인 포스팅 주제가 달라서 아쉬웠다.
- 엘리스 과정과 함께 진행하니 블로그 포스틍을 위해 시간을 내는게 힘들어 활동을 제대로 하지 못하였다.

### 4️⃣ 2차 스터디에서 시도해 보고 싶은 개선점 및 계획

- 현재 주 2회 포스팅에서 주 1회 포스팅으로 스터디 참여의 벽을 낮춘다.
- 스터디원 끼리 미니 프로젝트를 실시, 블로그에 프로젝트 관련 포스팅을 한다.
- 스터디원들과 함께 하나의 주제를 선정하고, 그에 관한 포스팅을 시도한다.
- 직접 제작한 블로그를 운영하고, IT 관련 다양한 주제에 대해 포스팅한다.

스터디 회고 의견 공유: https://docs.google.com/document/d/1kqoTFcEtuEWGrXkAfGNfn4DigsARfB0pC_ZfMEKixvk/edit