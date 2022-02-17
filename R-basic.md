R 기초
================

# R의 연산자 우선순위

## 기본 연산자

### 지수계산

``` r
a <- 2^4  
a2 <- 2**4
```

``` r
a
```

    ## [1] 16

``` r
a2
```

    ## [1] 16

#### 제곱근 계산

``` r
sqrt(16)
```

    ## [1] 4

### 양수, 음수 부호

``` r
-a
```

    ## [1] -16

``` r
+a2
```

    ## [1] 16

### 수열생성

``` r
b <- 1:5
b
```

    ## [1] 1 2 3 4 5

``` r
c<-3:8
c
```

    ## [1] 3 4 5 6 7 8

### 특수연산자

``` r
4%%5 #나머지
```

    ## [1] 4

``` r
4%/%5 #몫
```

    ## [1] 0

``` r
4%*%5 #행렬곱
```

    ##      [,1]
    ## [1,]   20

### 사칙연산

``` r
a*a2
```

    ## [1] 256

``` r
a/a2
```

    ## [1] 1

``` r
a+a2
```

    ## [1] 32

``` r
a-a2
```

    ## [1] 0

## 비교연산자

### 논리값 출력 (TRUE, FALSE)

``` r
3 == 5
```

    ## [1] FALSE

``` r
3 != 5 # !는 부정을 의미한다.
```

    ## [1] TRUE

``` r
!(3==5) #논리 부정도 가능 
```

    ## [1] TRUE

``` r
3>=5
```

    ## [1] FALSE

``` r
3<=5 
```

    ## [1] TRUE

### 여러개의 논리 연산 데이터

``` r
(3>=5)&(3<=5)&(3==5) #False & True & False = False , 다중 논리연산데이터
```

    ## [1] FALSE

``` r
(3>=5)&&(3<=5) #False && True = False , 단일 논리연산데이터
```

    ## [1] FALSE

``` r
(3>=5)|(3<=5) #False | True = True
```

    ## [1] TRUE

``` r
(3>=5)||(3<=5) #False || True = True
```

    ## [1] TRUE

## 식 (Fomula)

    ## 종속변수1 + 종속변수2 ~ 독립변수1 + 독립변수2 + 독립변수3

## 값의 대입

``` r
3 -> d 
3->> e
f <- 3
g <<- 3
```

``` r
d
```

    ## [1] 3

``` r
e
```

    ## [1] 3

``` r
f
```

    ## [1] 3

``` r
g
```

    ## [1] 3

# 변수의 정의 및 사용

``` r
ls() #사용 중인 변수 목록 확인 
```

    ## [1] "a"  "a2" "b"  "c"  "d"  "e"  "f"  "g"

``` r
rm(list=ls()) #모든 변수 삭제
ls() #변수 삭제 확인 
```

    ## character(0)

``` r
a <- 542
ls() 
```

    ## [1] "a"

``` r
rm(a) #특정 변수 삭제 
ls()
```

    ## character(0)

``` r
a <- 25
b <- 3
cat_test <- a+b
cat("a+b","\n=",a,"+",b,"\n=",cat_test )  
```

    ## a+b 
    ## = 25 + 3 
    ## = 28

``` r
# 괄호 속 내용을 하나로 연결해 화면에 출력 
```

``` r
ls()
```

    ## [1] "a"        "b"        "cat_test"

``` r
print(a) #괄호 속 한 개 값을 화면에 출력 후 줄바꿈 
```

    ## [1] 25

## 변수 정의시 규칙

-   변수 이름은 알파벳, 숫자, \_, . 을 넣어 지을 수 있음.  
-   \_, . 이외의 특수 문자 사용 불가.  
-   첫글자는 숫자일 수 없음.

# R의 data type

-   기본형, 구조형, 복합형으로 나누어짐.  
-   Special values가 존재함.  
-   데이터 내부의 자료형을 확인할 때는 mode() 사용

## 기본형

### numeric (num)

-   정수, 실수, 복소수, 수학적 연산 및 통계적 계산  
-   int : 정수형  
-   double : 실수형

``` r
a
```

    ## [1] 25

``` r
mode(a) #앞에서 정의한 변수 
```

    ## [1] "numeric"

### character (chr)

-   문자, 단어로 구성, “” 또는 ’’ 내에 표현됨

``` r
todayis <- 'Monday'
todayis 
```

    ## [1] "Monday"

``` r
mode(todayis)
```

    ## [1] "character"

### logical

-   TRUE, FALSE, 산술 연산 시 1, 0으로 사용 됨.

``` r
logic_check <- 3 == 5
logic_check
```

    ## [1] FALSE

``` r
mode(logic_check)
```

    ## [1] "logical"

### 기본형 데이터 타입의 우선순위

-   세가지 기본형 데이터 타입의 우선순위는 다음과 같다.  
-   character > numaric > logical  
-   따라서 아래와 같이 혼합형으로 존재하는 경우, 우선순위에 따른
    데이터타입을 반환한다.

``` r
testdf <- c("char",TRUE, 10 )
mode (testdf)
```

    ## [1] "character"

### 데이터타입이 특정 형식인지 확인하는 방법

-   is.numeric() 등을 이용하여 확인  
-   logical 값을 반환해줌.

``` r
print(a)
```

    ## [1] 25

``` r
typeof(a)
```

    ## [1] "double"

``` r
is.numeric(a)
```

    ## [1] TRUE

``` r
is.integer(a)
```

    ## [1] FALSE

``` r
is.double(a)
```

    ## [1] TRUE

``` r
is.character(a)
```

    ## [1] FALSE

``` r
is.logical(a)
```

    ## [1] FALSE

``` r
is.logical(is.character(a))
```

    ## [1] TRUE

## 구조형

-   class()로 확인되는 데이터의 구조형.  
-   mode()는 자료 내부의 데이터 자료형을 확인하였다면,  
-   class()는 data 전체의 형식을 파악하게 해줌.

### scalar

-   numaric, charactor,logical
-   단일 차원, 단일원소타입
-   길이가 1인 벡터.

``` r
a
```

    ## [1] 25

``` r
class(a)
```

    ## [1] "numeric"

### factor

-   numeric,charactor

-   1차원, 단일원소타입

-   범주형 데이터(명목형, 순서형)를 표현하기 위한 데이터 타입.

    -   명목형 : 순서 없음 (혈액형, 요일분류)
    -   순서형 : 순서 있음 (등수, 사이즈 등 )

    ``` r
    bloodtype <-factor("A","B","O","AB",order =T)
    str(bloodtype)
    ```

        ##  Ord.factor w/ 1 level "O": NA

    ``` r
    grade <-factor(c("A","B","C","D"),c("A","B","C","D"))
    grade
    ```

        ## [1] A B C D
        ## Levels: A B C D

    ``` r
    str(grade)
    ```

        ##  Factor w/ 4 levels "A","B","C","D": 1 2 3 4

    ``` r
    class = c("novice","intermediate","advanced")
    class
    ```

        ## [1] "novice"       "intermediate" "advanced"

    ``` r
    factor(class)
    ```

        ## [1] novice       intermediate advanced    
        ## Levels: advanced intermediate novice

    ``` r
    factor(class, order =T)
    ```

        ## [1] novice       intermediate advanced    
        ## Levels: advanced < intermediate < novice

    ``` r
    factor(class,levels=class,order =T)
    ```

        ## [1] novice       intermediate advanced    
        ## Levels: novice < intermediate < advanced

    ``` r
    factor(class,levels=c(class,'master'),order =T)
    ```

        ## [1] novice       intermediate advanced    
        ## Levels: novice < intermediate < advanced < master

### vector

-   numaric, charactor,logical
-   1차원, 단일원소타입  
-   하나 이상의 스칼라 (길이가 1 인 벡터) 원소들을 갖는 단순한 형태의
    집합
-   숫자, 문자, 논리형 데이터를 원소(element)로 사용할 수 있음
-   동일한 자료형 을 갖는 값들의 집합으로 하나의 열(colomn)로 구성됨

#### 벡터의 생성

-   **c(value1, value2, …)**  
    직접 원소 값을 입력하여 만들 때

-   **seq(from, to, by (or length))**

    -   from 부터, to까지 by씩 건너뛰는 수로 구성된 벡터.  
    -   length를 사용할 경우, from부터 to까지의 수 중 length개 만큼의
        수를 원소로 균등 간격.

-   **rep(x, times(or each))**

    -   x : 스칼라 또는 벡터 등을 사용할 수 있음.
    -   time : x가 벡터일 경우, 처음부터 끝까지 time에 지정된 수 만큼
        반복
    -   each : x가 벡터일 경우, 각 원소를 each에 지정된 수 만큼 반복

**0. 변수 리셋**

``` r
rm(list = ls()) # 변수 제거 
```

**1. 벡터 생성 - c() 이용**

``` r
a <- c(1,2,3)
a
```

    ## [1] 1 2 3

``` r
class(a)
```

    ## [1] "numeric"

``` r
str(a)
```

    ##  num [1:3] 1 2 3

**2. 벡터 생성 - c() 이용, 문자열 원소**

``` r
b <- c("A","B","C")
b
```

    ## [1] "A" "B" "C"

``` r
class(b)
```

    ## [1] "character"

``` r
str(b)
```

    ##  chr [1:3] "A" "B" "C"

**3. 벡터 생성 - c() 이용, 논리형 원소**

``` r
c <- c(TRUE,FALSE)
c
```

    ## [1]  TRUE FALSE

``` r
class(c)
```

    ## [1] "logical"

``` r
str(c)
```

    ##  logi [1:2] TRUE FALSE

**4. 벡터 생성 - c() 이용, 정수 실수 혼합 원소**

``` r
d <- c(3.5, 4.3, 5)
d
```

    ## [1] 3.5 4.3 5.0

``` r
class(d)
```

    ## [1] "numeric"

``` r
str(d)
```

    ##  num [1:3] 3.5 4.3 5

``` r
mode(d)
```

    ## [1] "numeric"

``` r
is.integer(d)
```

    ## [1] FALSE

``` r
is.double(d)
```

    ## [1] TRUE

**5. 벡터 생성 - seq() 이용**

``` r
e <- seq(1,4,2)
e
```

    ## [1] 1 3

``` r
class(e)
```

    ## [1] "numeric"

``` r
str(e)
```

    ##  num [1:2] 1 3

**6. 벡터 생성 - rep () 이용**

``` r
f <- rep(12, 4) #디폴트 값은 time (x를 몇회 반복할 것인가. )
f
```

    ## [1] 12 12 12 12

``` r
class(f)
```

    ## [1] "numeric"

``` r
str(f)
```

    ##  num [1:4] 12 12 12 12

``` r
f2 <-rep(e,3)
f2
```

    ## [1] 1 3 1 3 1 3

``` r
f3 <-rep(4:8,3) 
f3
```

    ##  [1] 4 5 6 7 8 4 5 6 7 8 4 5 6 7 8

``` r
f4 <-rep(4:8,each=3)
f4
```

    ##  [1] 4 4 4 5 5 5 6 6 6 7 7 7 8 8 8

**7. 벡터 생성 - c() 이용, 서로 다른 타입의 벡터 연결**

``` r
g <- c(a,b,c)
g
```

    ## [1] "1"     "2"     "3"     "A"     "B"     "C"     "TRUE"  "FALSE"

``` r
class(g)
```

    ## [1] "character"

``` r
str(g) #서로 다른 타입을 연결할 경우, 우선순위에 따라 타입을 취급 
```

    ##  chr [1:8] "1" "2" "3" "A" "B" "C" "TRUE" "FALSE"

#### 벡터의 연산

``` r
v1 <- seq(2,12,2) 
v2 <-rep(c(2,3),3) 
v1 #[1:6]
```

    ## [1]  2  4  6  8 10 12

``` r
v2 #[1:6]
```

    ## [1] 2 3 2 3 2 3

``` r
str(v2)
```

    ##  num [1:6] 2 3 2 3 2 3

``` r
v1+v2 #행렬덧셈, 벡터의 길이가 동일해야 연산 가능
```

    ## [1]  4  7  8 11 12 15

``` r
v1 %*% v2 #행렬곱
```

    ##      [,1]
    ## [1,]  108

``` r
str(v1 %*% v2) #[1:6]와[1:6]를 행렬곱하면 [1,1]
```

    ##  num [1, 1] 108

``` r
t(v2) #전치 
```

    ##      [,1] [,2] [,3] [,4] [,5] [,6]
    ## [1,]    2    3    2    3    2    3

``` r
str(t(v2)) #[1,1:6]
```

    ##  num [1, 1:6] 2 3 2 3 2 3

``` r
v1 %*% t(v2) 
```

    ##      [,1] [,2] [,3] [,4] [,5] [,6]
    ## [1,]    4    6    4    6    4    6
    ## [2,]    8   12    8   12    8   12
    ## [3,]   12   18   12   18   12   18
    ## [4,]   16   24   16   24   16   24
    ## [5,]   20   30   20   30   20   30
    ## [6,]   24   36   24   36   24   36

``` r
str(v1 %*% t(v2))  #[1:6]와[1,1:6]를 행렬곱하면 [1:6, 1:6]
```

    ##  num [1:6, 1:6] 4 8 12 16 20 24 6 12 18 24 ...

``` r
v1
```

    ## [1]  2  4  6  8 10 12

``` r
v3 <- c(1,2,3) 
v3
```

    ## [1] 1 2 3

-   벡터길이가 동일하지 않을 경우, 원소의 개수가 적은 쪽의 벡터를 원소가
    많은 쪽의 벡터와 동일하게 개수를 맞춤 (배수일 경우)

``` r
v1 + 3
```

    ## [1]  5  7  9 11 13 15

``` r
v1 + v3
```

    ## [1]  3  6  9  9 12 15

#### 벡터의 인덱싱

-   대괄호를 사용하며, 위치 index를 사용하거나, 조건문 또는 순열 등을
    사용할 수 있다.

``` r
v1
```

    ## [1]  2  4  6  8 10 12

``` r
v1[1] # n=1부터, n번째 원소 반환
```

    ## [1] 2

``` r
v1[-3] # n번째 원소를 제외한 나머지 원소 반환
```

    ## [1]  2  4  8 10 12

``` r
v1[2:5] #start번째부터 end번째까지의 원소까지 반환 
```

    ## [1]  4  6  8 10

``` r
v1[v1%%3 == 0] # 조건 만족하는 원소들 반환 
```

    ## [1]  6 12

``` r
v1%%3 == 0 #조건의 결과는 TRUE/FASLE로 구성됨, 결국은 TRUE/FALSE로 구성된 벡터를 인덱스로 넣어주는 것과 같음 
```

    ## [1] FALSE FALSE  TRUE FALSE FALSE  TRUE

-   각원소에 이름을 지정하여준 후, 이름으로 인덱싱하여 호출도 가능하다.

``` r
names(v1)<-c('A','B','C','D','E','F')
str(v1)
```

    ##  Named num [1:6] 2 4 6 8 10 12
    ##  - attr(*, "names")= chr [1:6] "A" "B" "C" "D" ...

``` r
v1
```

    ##  A  B  C  D  E  F 
    ##  2  4  6  8 10 12

``` r
v1['C']
```

    ## C 
    ## 6

-   스칼라, 벡터, 팩터의 관계 정리

    -   스칼라 = 길이가 1인 벡터
    -   팩터 = 수준을 가진 벡터. 범주형 데이터를 만들 수 있다.

### matrix

-   numaric, charactor,logical
-   2차원, 단일원소타입
-   한가지의 데이터 유형만 가능.
-   역행렬은 solve()로 구함

#### 행렬의 생성

-   **matrix**(data=NA, nrow =1, ncol =1, byrow = FALSE, dimnames =
    NULL)  
    byrow = FALSE : 값의 입력 방향이 열. TRUE로 지성 시 행 방향으로
    변경. dimnames = NULL : 각 차원의 이름
-   rbind()와 cbind()를 사용하여 결합.

``` r
m1 = matrix(seq(1,10), nrow = 2)
m1
```

    ##      [,1] [,2] [,3] [,4] [,5]
    ## [1,]    1    3    5    7    9
    ## [2,]    2    4    6    8   10

``` r
m1_byrow_T = matrix(seq(1,10), nrow = 2, byrow = TRUE)
m1_byrow_T
```

    ##      [,1] [,2] [,3] [,4] [,5]
    ## [1,]    1    2    3    4    5
    ## [2,]    6    7    8    9   10

``` r
m2 = matrix(seq(1,10), nrow = 5)
m2
```

    ##      [,1] [,2]
    ## [1,]    1    6
    ## [2,]    2    7
    ## [3,]    3    8
    ## [4,]    4    9
    ## [5,]    5   10

``` r
m3 = rbind(seq(1,3),seq(4,6)) #row(행)으로 붙임 
m3
```

    ##      [,1] [,2] [,3]
    ## [1,]    1    2    3
    ## [2,]    4    5    6

``` r
m4 = cbind(seq(1,3),seq(4,6)) #col(열)으로 붙임 
m4
```

    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    2    5
    ## [3,]    3    6

#### matrix 관련 함수, 인덱싱

2차원 데이터이기 때문에 행, 열의 구분이 필요.

``` r
rm(list=ls())  #변수 삭제 
m <- matrix(seq(1,12), nrow = 4)
m
```

    ##      [,1] [,2] [,3]
    ## [1,]    1    5    9
    ## [2,]    2    6   10
    ## [3,]    3    7   11
    ## [4,]    4    8   12

``` r
dim(m) #행렬의 차원 확인 
```

    ## [1] 4 3

``` r
nrow(m) #행의 개수 
```

    ## [1] 4

``` r
ncol(m) #열의 개수
```

    ## [1] 3

``` r
m[2,3]
```

    ## [1] 10

``` r
m[3,]
```

    ## [1]  3  7 11

``` r
m[,-2] #2열은 빼고 나머지 열들만 
```

    ##      [,1] [,2]
    ## [1,]    1    9
    ## [2,]    2   10
    ## [3,]    3   11
    ## [4,]    4   12

``` r
m[-2,]
```

    ##      [,1] [,2] [,3]
    ## [1,]    1    5    9
    ## [2,]    3    7   11
    ## [3,]    4    8   12

``` r
m[c(2,3),2]
```

    ## [1] 6 7

``` r
m[c(TRUE,FALSE,FALSE,FALSE),]
```

    ## [1] 1 5 9

``` r
m[c(FALSE,TRUE,FALSE,TRUE),]
```

    ##      [,1] [,2] [,3]
    ## [1,]    2    6   10
    ## [2,]    4    8   12

``` r
m[c(FALSE,TRUE),] 
```

    ##      [,1] [,2] [,3]
    ## [1,]    2    6   10
    ## [2,]    4    8   12

``` r
#열 길이보다 짧은 인수를 넣을 경우, 반복해서 채워 넣어줌. 
m[c(FALSE,TRUE,FALSE),] 
```

    ## [1]  2  6 10

``` r
#꼭 배수가 아니어도 괜찮음. 

t(m) #전치행렬 
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    2    3    4
    ## [2,]    5    6    7    8
    ## [3,]    9   10   11   12

``` r
diag(m) #대각 원소 반환 
```

    ## [1]  1  6 11

각 차원의 이름, 행의 이름, 열의 이름을 지정하여 이것을 활용하여 인덱싱도
가능하다.

``` r
dimnames(m) #차원 이름 확인 
```

    ## NULL

``` r
rownames(m) #행이름 확인 
```

    ## NULL

``` r
colnames(m) #열이름 확인
```

    ## NULL

``` r
rownames(m) <- c('A','B','C','D') #행이름 부여
rownames(m)
```

    ## [1] "A" "B" "C" "D"

``` r
colnames(m) <- c('1','2','3') #열이름 부여
colnames(m)
```

    ## [1] "1" "2" "3"

``` r
dimnames(m)
```

    ## [[1]]
    ## [1] "A" "B" "C" "D"
    ## 
    ## [[2]]
    ## [1] "1" "2" "3"

``` r
m
```

    ##   1 2  3
    ## A 1 5  9
    ## B 2 6 10
    ## C 3 7 11
    ## D 4 8 12

``` r
str(m)
```

    ##  int [1:4, 1:3] 1 2 3 4 5 6 7 8 9 10 ...
    ##  - attr(*, "dimnames")=List of 2
    ##   ..$ : chr [1:4] "A" "B" "C" "D"
    ##   ..$ : chr [1:3] "1" "2" "3"

``` r
m['A','2']
```

    ## [1] 5

### array

-   numaric, charactor, logical
-   2차원 이상(다차원), 단일원소타입

#### array의 생성

array(data,dim = (행, 열, …))

``` r
rm(list=ls())
a0 = array(1:12, dim = c(3,2))
a0
```

    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    2    5
    ## [3,]    3    6

``` r
dim(a0)
```

    ## [1] 3 2

``` r
a1 = array(1:12, dim = c(3,2,2))
a1
```

    ## , , 1
    ## 
    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    2    5
    ## [3,]    3    6
    ## 
    ## , , 2
    ## 
    ##      [,1] [,2]
    ## [1,]    7   10
    ## [2,]    8   11
    ## [3,]    9   12

``` r
dim(a1)
```

    ## [1] 3 2 2

``` r
a2 = array(1:12, dim = c(3,2,3))
a2
```

    ## , , 1
    ## 
    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    2    5
    ## [3,]    3    6
    ## 
    ## , , 2
    ## 
    ##      [,1] [,2]
    ## [1,]    7   10
    ## [2,]    8   11
    ## [3,]    9   12
    ## 
    ## , , 3
    ## 
    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    2    5
    ## [3,]    3    6

``` r
dim(a2)
```

    ## [1] 3 2 3

``` r
str(a2)
```

    ##  int [1:3, 1:2, 1:3] 1 2 3 4 5 6 7 8 9 10 ...

## 복합형

### data.frame

-   numaric, charactor,logical
-   2차원, 원소타입 복합가능 (벡터 별로 다른 데이터 유형 가능)
-   엑셀의 worksheet와 같은 구조의 데이터
-   벡터가 모여 데이터 프레임을 구성

#### data.frame 생성 함수

-   data.frame(vectors or matrices, stringsAsFactors) :들어가는 벡터의
    길이는 모두 같아야 함.
-   data.frame(변수명 = 벡터, …, stringsAsFactors) : stringsAsFactor를
    TRUE로 지정하면 문자열을 factor형으로 저장.
-   base R과 dplyr 패키지를 이용하여 자료 구조를 조작, 관리, 전처리

``` r
name <- c('tom','jerry','cindy','mark')
gender <- c('F','M',"M","F")
kor <- c(60,70,90,60)
eng <- c(100,50,70,90)
df1 <-data.frame(name,gender,kor,eng)
df1
```

    ##    name gender kor eng
    ## 1   tom      F  60 100
    ## 2 jerry      M  70  50
    ## 3 cindy      M  90  70
    ## 4  mark      F  60  90

``` r
df2 <-data.frame(matrix(seq(1,9),nrow = 3))
df2
```

    ##   X1 X2 X3
    ## 1  1  4  7
    ## 2  2  5  8
    ## 3  3  6  9

``` r
df3 <-data.frame(gender = gender,
                 kor_score = kor,
                 eng_score=eng,
                 stringsAsFactors = T)
df3
```

    ##   gender kor_score eng_score
    ## 1      F        60       100
    ## 2      M        70        50
    ## 3      M        90        70
    ## 4      F        60        90

``` r
dim(df3)
```

    ## [1] 4 3

``` r
str(df3)
```

    ## 'data.frame':    4 obs. of  3 variables:
    ##  $ gender   : Factor w/ 2 levels "F","M": 1 2 2 1
    ##  $ kor_score: num  60 70 90 60
    ##  $ eng_score: num  100 50 70 90

#### data.frame의 인덱싱

``` r
df3[2,2] #scalar 값 output
```

    ## [1] 70

``` r
class(df3[2,2])
```

    ## [1] "numeric"

``` r
df3[2,] # 특정 행 추출 data frame 반환 
```

    ##   gender kor_score eng_score
    ## 2      M        70        50

``` r
class(df3[2,])
```

    ## [1] "data.frame"

``` r
df3[,3] # 특정 열 추출, vector 반환 
```

    ## [1] 100  50  70  90

``` r
class(df3[,3])
```

    ## [1] "numeric"

``` r
df3[2] #특정 열 추출, data.frame 반환 
```

    ##   kor_score
    ## 1        60
    ## 2        70
    ## 3        90
    ## 4        60

``` r
class(df3[2]) 
```

    ## [1] "data.frame"

``` r
df3[[2]] #특정 열 추출,vector 반환 
```

    ## [1] 60 70 90 60

``` r
class(df3[[2]]) 
```

    ## [1] "numeric"

``` r
df3[c('gender','kor_score')] 
```

    ##   gender kor_score
    ## 1      F        60
    ## 2      M        70
    ## 3      M        90
    ## 4      F        60

``` r
#해당 vector 목록에 해당하는 data.frame 반환
class(df3[c('gender','kor_score')])
```

    ## [1] "data.frame"

``` r
df3[,c(1,3)]  #해당 vector 목록에 해당하는 data.frame 반환 
```

    ##   gender eng_score
    ## 1      F       100
    ## 2      M        50
    ## 3      M        70
    ## 4      F        90

``` r
class(df3[,c(1,3)])
```

    ## [1] "data.frame"

``` r
df3[-2] #특정 열 제외하고 반환, data.frame 반환 
```

    ##   gender eng_score
    ## 1      F       100
    ## 2      M        50
    ## 3      M        70
    ## 4      F        90

``` r
class(df3[-2])
```

    ## [1] "data.frame"

``` r
df3[-2,] #특정 행 제외하고 반환, data.frame 반환 
```

    ##   gender kor_score eng_score
    ## 1      F        60       100
    ## 3      M        90        70
    ## 4      F        60        90

``` r
class(df3[-2,])
```

    ## [1] "data.frame"

``` r
df3$gender #특정 열 추출, vector 반환 
```

    ## [1] F M M F
    ## Levels: F M

``` r
class(df3$gender)
```

    ## [1] "factor"

``` r
str(df3$gender) #factor로 저장해 두었으므로, 2개의 level이 있는 것을 확인. 
```

    ##  Factor w/ 2 levels "F","M": 1 2 2 1

#### data.frame의 핸들링

``` r
#새로운 변수 만들기 
df3$hight <- c(170,154,160,167)
df3['weight'] <- c(60,70,55,52)
df3
```

    ##   gender kor_score eng_score hight weight
    ## 1      F        60       100   170     60
    ## 2      M        70        50   154     70
    ## 3      M        90        70   160     55
    ## 4      F        60        90   167     52

``` r
#조건으로 선택하기 
subset(df3,subset = hight >160) # 'subset =' 생략 가능
```

    ##   gender kor_score eng_score hight weight
    ## 1      F        60       100   170     60
    ## 4      F        60        90   167     52

``` r
#목록으로 선택 
subset(df3,subset = gender == 'F',select = c(hight,weight))
```

    ##   hight weight
    ## 1   170     60
    ## 4   167     52

``` r
#열, 열목록 제거 
subset(df3,subset = gender == 'F',select = -weight)
```

    ##   gender kor_score eng_score hight
    ## 1      F        60       100   170
    ## 4      F        60        90   167

``` r
#열 이름 바꾸기 
colnames(df3)[2] <-'score_of_kor'
df3
```

    ##   gender score_of_kor eng_score hight weight
    ## 1      F           60       100   170     60
    ## 2      M           70        50   154     70
    ## 3      M           90        70   160     55
    ## 4      F           60        90   167     52

### list

-   numaric, charactor, logical
-   2차원 이상, 원소타입 복합가능
-   list에 저장된 데이터를 index 또는 key를 사용해 접근함.

#### list 생성함수

-   list(key = value, key=value, … )
-   list의 부분집합도 list
-   pre-allocate : list를 미리 만들어 두고 추후에 data를 넣을 수 있음

``` r
a <- list(name = 'julie',age = 25, h_w = c(160,45))
a
```

    ## $name
    ## [1] "julie"
    ## 
    ## $age
    ## [1] 25
    ## 
    ## $h_w
    ## [1] 160  45

``` r
str(a)
```

    ## List of 3
    ##  $ name: chr "julie"
    ##  $ age : num 25
    ##  $ h_w : num [1:2] 160 45

``` r
class(a)
```

    ## [1] "list"

``` r
a['name']
```

    ## $name
    ## [1] "julie"

``` r
a[3]
```

    ## $h_w
    ## [1] 160  45

``` r
a[[3]]
```

    ## [1] 160  45

``` r
list1 <-vector("list",3)
list1
```

    ## [[1]]
    ## NULL
    ## 
    ## [[2]]
    ## NULL
    ## 
    ## [[3]]
    ## NULL

``` r
list1[[1]] <- "abc"
list1[[2]] <- "dfc"
list1[[3]] <- c(1,2,4)
list1
```

    ## [[1]]
    ## [1] "abc"
    ## 
    ## [[2]]
    ## [1] "dfc"
    ## 
    ## [[3]]
    ## [1] 1 2 4

### data.table

-   data frame의 확장 데이터 구조. (data frame이자 data table)
-   data.table 패키지를 이용하여 조작, 관리, 전처리 수행.
-   2차원의 테이블 형태를 가짐.

## Special Values

-   **NULL** : 변수 값이 초기화되지 않음.  
-   **NA** : Not Availiable, 데이터 값 없음 (결측치)  
-   **NaN** : Not Available Number, 계산 불가능  
-   **INF** : Infinite, 무한대  
    NA : Not Available → 사용 불가능. 데이터에 값이 존재하지 않음
-   NULL은 값이 정의되지 않아 아예 없는 것. NA는 정의되지 않은 값 -Inf
    및 Inf : 음과 양의 무한대

NaN : Not a Number → 수의 연산이 불가능한 경우(0/0, Inf/Inf 등)

## 데이터 타입의 명시적 변환

-   as.factor(객체): 요인으로 변환
-   as.numeric(객체) : 숫자를 저장한 벡터로 변환
-   as.character(객체) : 문자열을 저장한 벡터로 변환
-   as.matrix(객체) : 행렬로 변환
-   as.array(객체) : 배열로 변환
-   as.data.frame(객체) : 데이터프레임으로 변환

# 외부 데이터 사용

## CSV 파일 불러오기

-   read.csv(‘ 파일이름 ’, fileEncoding =‘UTF 8 BOM’)
-   write.csv(‘ 파일이름 ’, row.names =FALSE) # row name을 저장하지
    않음.

## text 파일 불러오기

-   read.table 파일이름 ’, sep 구분자 , col.names 컬럼이름목록
-   기본값 header=FALSE, sep =’’

## R객체 (Rdata)를 저장하고 불러오기

-   save(객체, file= “파일이름 Rdata”)
-   load(“파일이름 Rdata”)

## R의 기본 데이터셋 사용

``` r
head(iris,3) # 6줄이 기본값
```

    ##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    ## 1          5.1         3.5          1.4         0.2  setosa
    ## 2          4.9         3.0          1.4         0.2  setosa
    ## 3          4.7         3.2          1.3         0.2  setosa

``` r
tail(iris,3) # 6줄이 기본값
```

    ##     Sepal.Length Sepal.Width Petal.Length Petal.Width   Species
    ## 148          6.5         3.0          5.2         2.0 virginica
    ## 149          6.2         3.4          5.4         2.3 virginica
    ## 150          5.9         3.0          5.1         1.8 virginica

``` r
View(iris) #창을 열고, 엑셀형태로 데이터셋 보여줌. 
summary(iris) #기초통계량 (최솟값, 1사분위수, 중간값, 평균, 3사분위수, 최댓값)
```

    ##   Sepal.Length    Sepal.Width     Petal.Length    Petal.Width   
    ##  Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
    ##  1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300  
    ##  Median :5.800   Median :3.000   Median :4.350   Median :1.300  
    ##  Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199  
    ##  3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800  
    ##  Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500  
    ##        Species  
    ##  setosa    :50  
    ##  versicolor:50  
    ##  virginica :50  
    ##                 
    ##                 
    ## 

``` r
str(iris)
```

    ## 'data.frame':    150 obs. of  5 variables:
    ##  $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
    ##  $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
    ##  $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
    ##  $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
    ##  $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...

``` r
attach(iris) # 데이터 셋 고정 사용 선언. 변수명 만으로도 데이터에 접근 가능. 
detach(iris) # 고정된 데이터셋 사용을 해제 선언함. 
```
