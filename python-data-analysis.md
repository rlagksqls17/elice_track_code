# 데이터 구조  

## 리스트

### 리스트 내포  

```python
numbers = [1, 3, 4, 5, 6, 7]
odd = [n + 1 for n in numbers if n % 2 == 0]
```



## 딕셔너리  

```python
# 기본
accounts = {
    "kdhong.elice" : "Kildong Hong"
}

print(accounts["kdhong.elice"])


# 변할 수 없는 값만이 key가 될 수 있다.  
kdhong = ("kdhong", "cantcalldad")

accounts = {
    kdhong: ('Kildong Hong', ...)
}

kdhong[0] = "kdhong.elice"  # Error


# 딕셔너리의 키 확인하기  
# {id: 이름}
accounts = {
    "kdhong" : "Kildong Hong"
}

print("kdhong" in accounts)  # True
print("elice" in accounts)  # False

```

### .items()

```python
# 딕셔너리 순회하기
accounts = {
    "kdhong" : "Kildong Hong"
}

for username, name in accounts.items():
    print(username + "-" + name)
```



## 문자열

### .startswith()  

```python
word = "superman"
print(word.startswith('s')) # True

if word.startswith('a'):
    print("a로 시작하는 단어입니다.")
```

### .split()

```python
numbers = "   1   2   3   "
print(numbers.split()) # ['1', '2', '3']

print(numbers.split(' ')) # ['', '', '1', '' ,'2', '', '3', '', '']
```

### .append()

```python
numbers = []
numbers.append(1)

print(numbers)  # [1]

numbers.append(2)
print(numbers) # [1, 2]
```

### .lower()

```python
intro = "My name is Elice"
lower_intro = intro.lower()
print(lower_intro)

# "my name is elice"
```

### .replace()

```python
intro = "제 이름은 Elice입니다."
print(intro.replace(' ', ''))
# "제이름은Elice입니다."


'/* elice */'.replace('/', '').replace('*', '').replace(' ', '')
# 'elice'
```

## JSON

```json
// 웹 환경에서 데이터를 주고 받는 가장 표준적인 방식 
// 키를 이용하여 원하는 데이터만 빠르게 추출 가능  
// 데이터가 쉽게 오염되지 않음 
// 다른 포맷에 비해 용량이 조금 큰 편 
// JSON과 딕셔너리간 딱히 오가는데 문제 없음
```

### .loads

```python
json.loads(json_string) : JSON 형태의 문자열을 딕셔너리로 반환
json.dumps(dict_string) : 딕셔너리를 JSON 형태의 문자열로 반환
```





## 데이터 정렬하기  

```python
numbers = [-1, 3, -4, 5, 6, 100]
sort_by_abs = sorted(numbers, key=abs)
# [-1, 3, -4, 5, 6, 100]

fruits = ['cherry', 'apple', 'banana']
sort_by_alphabet = sorted(fruits)
# ['apple', 'banana', 'cherry']

def reverse(word):
    return str(reversed(word))
# apple => elppa

fruits = ['cherry', 'apple', 'banana']
sort_by_last = sorted(fruits, key=reverse)
# ['banana', 'apple', 'cherry']



#(단어, 빈도수) 쌍으로 이루어진 튜플을 받아, 빈도수를 리턴합니다.    
def get_freq(pair):
    return pair[1]

#(단어, 빈도수) 꼴 튜플의 리스트를 받아, 빈도수가 낮은 순서대로 정렬하여 리턴합니다.
def sort_by_frequency(pairs):
    return sorted(pairs, key=get_freq)


pairs = [
    ('time', 8),
    ('the', 15),
    ('turbo', 1),
]
# 아래 주석을 해제하고 결과를 확인해보세요.  
print(sort_by_frequency(pairs))
```



## 파일

```python
# 파일 읽기 1
file = open('data.txt')
content = file.read()
file.close()

# 파일 읽기 2 (file.close 필요없음) 
with open('data.txt') as file:
    content = file.read()

# 줄 단위로 읽기
contents = []
with open('data.txt') as file:
    for line in file:
        contents.append(line)
        
# 쓰기 모드로 파일을 연다.
with open('data.txt', 'w') as file:
    file.write('Hello')
```

## CSV  

```python
# Comma Separated Value
# 각 열이 특정한 의미를 가짐

# movies.csv
# 국문제목, 영문제목, 개봉 연도
# 다른 구분 문자(|)도 사용 가능
다크나이트, The Dark Knight, 2008
겨울왕국, Frozen, 2013
슈렉, Shrek, 2001
슈퍼맨, Superman, 1978

# 데이터에 구분 문자가 포함된 경우
"Eat, Pray, Love", 2010 처럼 따옴표를 넣어줌

# 오타가 날 경우 데이터 오염에 취약함 (구분문자 잘못 넣어준 경우 등)
```

### csv 파일 다루기  

```python
import csv

# csv 파일 읽기
with open('movies.csv') as file:
    # 구분자를 이용하여 csv를 읽음
    reader = csv.reader(file, delimiter=',')
    for row in reader:
        print(row[0])
```



## 집합  

```python
# 셋 다 같은 값 (순서와 중복이 없는 데이터 구조)
set1 = {1, 2, 3}
set2 = set([1, 2, 3])
set3 = {3, 2, 3, 1}


# 집합 다루기
num_set = {1, 3, 5, 7}
num_set.add(9)
num_set.update([3, 15, 4])
num_set.remove(7)  # 7이 없으면 에러 발생됨
num_set.discard(13)  # 13이 없어도 무시 가능

num_set = {1, 3, 5, 7}
print(6 in num_set)  # false
print(len(num_set))  # 4


# 집합 연산
union = set1 | set2  # 합집합
interaction = set1 & set2  # 교집합
diff = set1 -set2  # 차집합
xor = set1 ^ set2  # XOR
```

# 고오급 함수

### lambda

```python
def square(x):
    return x * x

square = lambda x: x*x
```

### 함수 안의 함수

```python
def adder(n):
    def helper(x):
        return x + n
    return helper

add_three = adder(3) # helper(n) return 3+n
print(add_three(6)) # 9
```

### map  

```python
def get_eng_title(row):
    split = row.split(',')
    return split[1]

# 1
eng_titles = map(get_eng_title, movies)
# 2
eng_titles = (lambda row: row.split(',')[1], movies)

=> list가 아닌 map object가 반환됨
=> 꺼낼 때마다 함수를 적용하여 응답하기 때문에
```

### filter()

```python
def starts_with_r(word):
    return word.startswith('r')

words = ['real', 'man', 'rhythm']
r_words = filter(starts_with_r, words)
# True로 나온 word에 대해서만 필터링하여
# 리스트가 아닌 filter 타입을 가짐
```

# ---

# Numpy

```python
np.arrary([1, 2, 3, 4, 5])
np.array([[1, 2], [3, 4]])


# array([1., 2., 3., 4.])
arr = np.array([1, 2, 3, 4], dtype='float')


---
# 배열 데이터 타입 dtype
arr.dtype # dtype('float64')
arr.astype(int) # array([1, 2, 3, 4])


---
# 다양한 배열 만들기
# array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0])
np.zeros(10, dtype=int)


# array([[1., 1., 1.], [1., 1., 1.], [1., 1., 1.]])
np.ones((3, 3), dtype=float)


# array([0, 2, 4, 6, 8, 10, 12, 14, 16, 18])
np.arange(0, 20, 2)


# array([0., 0.25, 0.5, 0.75, 1.])
np.linspace(0, 1, 5)


--- 
# np.random
# array([[난수, 난수], [난수, 난수]])
np.random.random((2, 2))


# 평균이 0이고 표준편차가 1인 데이터 중 랜덤값
# 표준 정규 분포에서 추출한 랜덤값
np.random.normal(0, 1, (2, 2))


# 0이상 10미만의 랜덤한 값이 들어있는 2 x 4크기의 배열 저장
array = np.random.randint(0,10,(2,4))
```

## 배열의 기초

```python
x2 = np.random.randint(10, size=(3, 4))
# array([[2, 2, 9, 0], [4, 2, 1, 0], [1, 8, 7, 3]])

x2.ndim # 차원 : 2 
x2.shape # 배열의 형태 : (3, 4)
x2.size # 배열의 크기 : 12
x2.dtype # 배열의 타입 : dtype('int64')

x = np.arange(7)
x[3] # 3
x[7] # IndexError
x[0] = 10
# array([10, 1, 2, 3, 4, 5, 6])


# 인덱싱
x = np.arange(7)

x[1:4]
# array([1, 2, 3])

x[1:]
# array([1, 2, 3, 4, 5, 6])

x[:4]
# array([0, 1, 2, 3])

x[::2]
# array([0, 2, 4, 6])


# 2차원 배열 인덱싱  
	# 1부터 15까지 들어있는 (3, 5)짜리 배열을 만듦
matrix = np.arange(1, 16).reshape(3, 5)

	# matrix의 (2, 3) 인덱스의 요소 출력
print(matrix[2, 3])

	# matrix의 행은 인덱스 0부터 인덱스 1까지, 열은 인덱스 1부터 인덱스 3까지 출력
print(matrix[0:2, 1:4])
```

## np.reshape

```python
x = np.arange(8)
x.shape 
# (8, )

x2 = x.reshape((2, 4))
# array([[0, 1, 2, 3], [4, 5, 6, 7]])

x2.shape # (2, 4)
```

## np.concatenate

```python
x = np.array([0, 1, 2])
y = np.array([3, 4, 5])
np.concatenate([x, y])
# array([0, 1, 2, 3, 4, 5])

matrix = np.arange(4).reshape(2, 2)
# array([0, 1], [2, 3])
np.concatenate([matrix, matrix], axis=0) # 세로 방향 붙임
# array([0, 1], [2, 3], [0, 1], [2, 3])

matrix = np.arange(4).reshape(2, 2)
np.concatenate([matrix, matrix], axis=1) # 가로 방향 붙임
```

## np.split

```python
# axis 축을 기준으로 나눔  
matrix = np.arange(16).reshape(4, 4)
# array([[0, 1, 2, 3], [4, 5, 6, 7], [8, 9, 10, 11], [12, 13, 14, 15])

upper, lower = np.split(matrix, [3], axis=0)
# array1([[0, 1, 2, 3], [4, 5, 6, 7], [8, 9, 10, 11]])
# array2([12, 13, 14, 15])

left, right = np.split(matrix, [3], axis=1)
# array1([[0, 1, 2], [4, 5, 6], [8, 9, 10]])
# array2([[3], [7], [11], [15]])
```

## 기본 연산

```python
# array는 +, -, *, /에 대한 기본 연산을 지원한다.  

x = np.arange(4) # array([0, 1, 2, 3])
x + 5 # array([5, 6, 7, 8])
x - 5 # array([-5, -4, -3, -2])    
x * 5 # array([0, 5, 10, 15])
x / 5 # array([0. , 0.2, 0.4, 0.6])


x = np.arange(4).reshape((2, 2))
y = np.random.randint(10, size=(2, 2))
x + y  # array([[1, 7], [6, 5]])
x - y # array([[-1, -5], [-2, 1]])
```

## 브로드캐스팅  

![image-20210902012152601](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210902012152601.png)

![image-20210902012343362](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210902012343362.png)

```python
# Numpy로 생성한 배열의 크기가 다를 경우 연산을 하면
# Numpy에서는 브로드캐스팅이라는 연산 방식으로 처리함
```

## 집계연산  

```python
x = np.arange(8).reshape((2, 4))

np.sum(x) # 28
np.min(x) # 0
np.max(x) # 7
np.mean(x) # 3.5

np.sum(x, axis=0)
# array([4, 6, 8, 10]) 컬럼별로 더해줌

np.sum(x, axis=1)
# array([6, 22]) 로우별로 더해줌
```

## 마스킹 연산  

```python
x = np.arange(5)
# array([0, 1, 2, 3, 4])

x < 3
# array([True, True, True, False, False])

x > 5
# array([False, False, False, False, False])

x[x < 3]
# array([0, 1, 2])
```

# ---  

# pandas  

```python
# 구조화된 데이터를 효과적으로 처리하고 저장할 수 있는 파이썬 라이브러리, Array 계산에 특화된 numpy를 기반으로 만들어져서 다양한 기능들을 제공한다.
```

## Series

```python
import pandas as pd

data = pd.Series([1, 2, 3, 4])
```

![image-20210902014529632](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210902014529632.png)

```python
# 인덱스 지정 가능
data = pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])
data['b'] # 2

# 딕셔너리로도 시리즈 만들 수 있음  
population_dict = {
    'korea': 5180,
    'japan': 12718,
    'china': 141500,
    'usa': 32676
}
population = pd.Series(population_dict)
```

### options = fill_value

```python
# 연산시 비어있는 값들이 생길 경우 특정 값으로 채워줌
A = pd.Series([2, 4, 5], index=[0, 1, 2])
B = pd.Series([1, 3, 5], index=[1, 2, 3])

A.add(B, fill_value=0)
```



## DataFrame  

## 데이터 확인

```python
gdp = pd.Series(gdp_dict)
country = pd.DataFrame({
    'population' : population, # Series1
    'gdp' : gdp # Series2
})
```

![image-20210902015635580](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210902015635580.png)

```python
# 전체 데이터를 볼 수 있도록 확인
pd.set_option('display.max_columns', None)
pd.set_option('display.max_rows', None)

# index 값 확인  
country.index

# column 값 확인
country.columns  

country['gdp']
type(country['gdp'])
# pandas.core.series.Series


# 계산한 값이 적용되어진 새 컬럼 만듦
gdp_per_capita = country['gdp'] / country['population']
country['gdp per capita'] = gdp_per_capita
```

### 저장과 불러오기  

```python
country.to_csv("./country.csv")
country.to_excel('country.xlsx')

country = pd.read_csv("./country.csv")
country = pd.read_excel('country.xlsx')
```

### 결측치 확인  

```python
df.isnull().sum()
```



## 데이터 전처리

### 인덱싱과 슬라이싱  

```python
# 하나의 행을 참조 인덱싱
country.loc['china'] 

# 행과 열을 슬라이싱
	# 해당 끝 열까지 포함
country.loc['japan' : 'korea', :'population']

# 파이썬 스타일 정수 인덱싱
country.iloc[0]

# 파이썬 스타일 정수 슬라이싱
	# 해당 끝 열을 안 포함
country.iloc[1:3, :2]
```

### DataFrame 새 데이터 추가와 수정 , 삭제

```python
dataframe = pd.DataFrame(columns=['이름', '나이', '주소'])

# add
dataframe.loc[0] = ['임원균', '26', '서울']
dataframe.loc[1] = {'이름' : '철수', '나이' : '25', '주소':'인천'}

# update
dataframe.loc[1, '이름'] = '영희'

# drop
	# 삭제와 동시에 저장
pd.drop(columns='year', inplace=True) 
```

![image-20210902021503664](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210902021503664.png)

```python
# 컬럼 추가
dataframe['전화번호'] = np.nan
dataframe.loc[0, '전화번호'] = '01012341234'

len(dataframe)
```

```python
# 컬럼 선택하기  
dataframe["이름"] # 컬럼이름아 하나만 있다면 Series 반환
dataframe[['이름', '주소', '나이']] # 리스트로 들어가 있다면 DataFrame
```

### df.isnull, df.notnull

```python
# 각 요소마다 불리언 값을 가진 DataFrame을 반환
dataframe.isnull()
dataframe.notnull()
```

### df.dropna, df.fillna

```python
# 비어있는 값이 있는 로우를 제거
datafame.dropna()

# 비어있는 값이 있으면 해당 값으로 채워줌
dataframe['전화번호'] = dataframe['전화번호'].fillna('전화번호 없음')
```

### options = fill_value

```python
# 연산시 비어있는 값들이 생길 경우 특정 값으로 채워줌
A = pd.DataFrame(np.random.randint(0, 10, (2, 2)), columns=list("AB"))
B = pd.DataFrame(np.random.randint(0, 10, (3, 3)), columns=list("BAC"))

A.add(B, fill_value=0) # add, sub, mul, div,
```

### 집계함수  

```python
# numpy array에서 사용했던 sum, mean 등을 활용 가능
data = {
    'A' : [i+5 for i in range(3)],
    'B' : [i**2 for i in range(3)]
}

df = pd.DataFrame(data)
df['A'].sum() # 18, A 시리즈 데이터만 뽑아서 연산
df.sum() # A : 18, B : 5 의 시리즈가 반환됨
df.mean()
```

### .sort_values

```python
df = pd.DataFrame({
    'col1' : [2, 1, 9, 8, 7, 4],
    'col2' : ['A', 'A', 'B', np.nan, 'D', 'C'],
    'col3' : [0, 1, 9, 4, 2, 3]
})

# col1 숫자 오름차순 정렬됨
df.sort_values('col1')   

# 내림차순 정렬
df.sort_values('col1', ascending=False)

# 오름차순, 내림차순 정렬
df.sort_Values(['col1', 'col2'], ascending=[False, True])

# col2를 먼저 정렬 후 col1을 정렬
df.sort_values(['col2', 'col1'])
```

### 조건으로 검색하기

```python
import numpy as np 
import pandas as pd  

df = pd.DataFrame(np.random.rand(5, 2), columns=['A', 'B'])

# 마스킹 연산
df[(df["A"] < 0.5) & (df["B"] > 0.3)]

# 쿼리 연산 (마스킹 연산 결과와 같음)
df.query("A < 0.5 and B > 0.3")

# 문자열 조건 연산  
df["Animal"].str.contains("Cat") 
df.Animal.str.match("Cat")
```

### 함수로 데이터 처리하기  

```python
df = pd.DataFrame(np.arange(5), columns=["Num"])

def square(x):
    return x**2

# .apply
df["Num"].apply(square) # 함수 자체를 넣음 => 시리즈 반환  
df["Square"] = df["Num"].apply(square) # 위를 이용해서 컬럼 추가

# lambda
df["Square"] = df.Num.apply(lambda x: x ** 2)

# replace 
	# apply로 함수 적용 대신 데이터 값만 바꿔주고 싶을 때
    # 0과 1로 바꿔줌
df.Sex.replace({"Male" : 0, "Female" : 1}) 
 
    # 시리즈 대신 데이터프레임 반환
df.Sex.replace({"Male" : 0, "Female" : 1}, inplace=True)
```

### 그룹으로 묶기  

```python
df = pd.DataFrame({'key' : ['A', 'B', 'C', 'A', 'B', 'C'],
                  'data1' : [1, 2, 3, 1, 2, 3],
                  'data2' : np.random.randint(0, 6, 6)})

df.groupby('key')
df.groupby('key').sum()
df.groupby(['key', 'data1']).sum()
```

![image-20210902170317061](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210902170317061.png)

```python
# groupby.aggregate

df.groupby('key').aggregate(['min', np.median, max])
df.groupby('key').aggregate({'data' : 'min', 'data2' : np.sum})
```

![image-20210902170636349](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210902170636349.png)

```python
# filter  
def filter_by_mean(x):
	return x['data2'].mean() > 3

df.groupby('key').mean()

	# 평균보다 큰 값을 추려낼 수 있음
df.groupby('key').filter(filter_by_mean)

# apply
df.groupby('key').apply(lambda x: x.max() - x.min())
```

![image-20210902172536288](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210902172536288.png)

```python
# get_group  

df = pd.read_csv("./univ.csv")
df.head()
df.groupby("시도").get_group("충남")
len(df.groupby("시도").get_group("충남")) # 94
```

![image-20210902172745573](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210902172745573.png)



###  MultiIndex  

```python
# 인덱스를 계층적으로 만들 수 있음
df = pd.DataFrame(
	np.random.randn(4, 2),
    index = [['A', 'A', 'B', 'B'], [1, 2, 1, 2]], # 인덱스가 2차원
    columns = ['data1', 'data2'] # 열 인덱스에도 적용 가능함
)

# 인덱스 탐색 시 다음과 같이 함
df["A"]
df["A"]["1"]
```

### pivot_table

```python
# 데이터에서 필요한 자료만 뽑아서 요약 가능

df.pivot_table(
	index='sex', columns='class', values='survived',
    aggfunc=np.mean # 평균값으로 채운다
)
```

![image-20210902174752245](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210902174752245.png)

## 데이터 샘플링

```python
# 30개의 표본을 뽑는다. (이것을 47번 반복한다.)

# 표본을 저장할 리스트
sample_list = []

for count in range(0, 47):
    """
    DataFrame.sample(
        n = 추출할 표본 개수
        replace = 복원추출 여부 (불리언 값)
        axis = 0: 인덱스 기준, 1: 칼럼 기준
    )
    """
    sample_list.append(main_df.sample(n = 30, replace = False, axis=0))

len(sample_list)
```



# ---

# matplotlib  

```python
import matplotlib.pyplot as plt  

x = [1, 2, 3, 4, 5]
y = [1, 2, 3, 4, 5]
plt.plot(x, y)

# title  
plt.title("First Plot")
plt.xlabel("x")
plt.ylabel("y")

# 객체지향 방식
x = [1, 2, 3, 4, 5]
y = [1, 2, 3, 4, 5]
fig, ax = plt.subplots() # 도화지, 그래프공간
ax.plot(x, y)
ax.set_title("First Plot")
ax.set_xlabel("x")
ax.set_ylabel("y")

fig.set_dpi(300) # 출력물에 대한 화질 표시
fig.savefig("first_plot.png") # 저장


# 여러 그래프 그리기  
x = np.linspace(0, np.pi*4, 100)
fig, axes = plt.subplots(2, 1) # 서브 플롯 나눔
axes[0].plot(x, np.sin(x))
axes[1].plot(x, np.cos(x))
```

## line style

```python
x = np.arange(10)
fig, ax = plt.subplots()

# solid
ax.plot(x, x, linestyle="-")

# dashed
ax.plot(x, x+2, linestyle="--")

# dashdot
ax.plot(x, x+4, linestyle="-.")

# dotted
ax.plot(x, x+6, linestyle=':')
```

## Color  

```python
x = np.arange(10)

flg, ax = plt.subplots()

ax.plot(x, x, color='r')
ax.plot(x, x+2, color="green")
ax.plot(x, x+4, color='0.8')
ax.plot(x, x+6, color="#524FA1")
```

## Marker  

```python
x = np.arange(10)

fig, ax = plt.subplots()

ax.plot(x, x, marker=".")
ax.plot(x, x+2, marker="o")
ax.plot(x, x+4, marker='v')
ax.plot(x, x+6, marker='s')
ax.plot(x, x+8, marker='*')
```

## 축 경계조정하기  

```python
x = np.linspace(0, 10, 1000)

flg, ax = plt.subplots()

ax.plot(x, np.sin(x))
ax.set_xlim(-2, 12) # x값 경계 설정
ax.set_ylim(-1.5, 1.5) # y값 경계 설정
```

## 범례

```python
flg, ax = plt.subplots()
ax.plot(x, x, label='y=x')
ax.plot(x, x**2, label='y=x*2')
ax.set_xlabel("x")
ax.set_ylabel("y")

ax.legend( # 범례
	loc='upper right', # 위치
    shadow=True, # 그림자
    fancybox=True, # 모서리 radius
    borderpad=2 # 범례 크기
)
```

## Scatter

```python
# ex 1
flg, ax = plt.subplots()

x = np.arange(10)

ax.plot(
	x, x**2, "o", # o 문자 넣었을 때 scatter plot 
    markersize=15,
    markerfacecolor='white',
    markeredgecolor='blue'
)

# ex 2
fig, ax = plt.subplots()
x = np.random.randn(50)
y = np.random.randn(50)
colors = np.random.randint(0, 100, 50)

sizes = 500 * np.pi * np.random.rand(50) ** 2

ax.scatter(x, y, c=colors, s=sizes, alpha=0.3)
# alpha = 투명도
```

## Bar plot  

```python
# 막대그래프
x = np.arange(10)
fig, ax = plt.subplots(figsize=(12, 4))
ax.bar(x, x**2)

# 누적 막대그래프
x = np.random.rand(3)
y = np.random.rand(3)
z = np.random.rand(3)
data = [x, y, z]

fig, ax = plt.subplots()
x_ax = np.arange(3)
for i in x_ax:
    ax.bar(x_ax, data[i],
          bottom=np.sum(data[:i], axis=0))
    
ax.set_xticks(x_ax)
ax.set_xticklabels(['A', 'B', 'C'])
```

## Histogram

```python
fig, ax = plt.subplots()
data = np.random.randn(1000)
ax.hist(data, bins=50)
```

## with pandas

```python
df = pd.read_csv("./president_heights.csv")

fig, ax = plt.subplots()
ax.plot(df["order"], 
       df["height(cm)"],
       label="height")

ax.set_xlabel("order")
ax.set_ylabel("height(cm)")
```

## subplot

```python
import numpy as np
import matplotlib

x = [1,3,5,7,9]
y = [2,4,6,8,10]

plt.subplot(131)
plt.plot(x, y)
plt.subplot(132)
plt.scatter(x, y)
plt.subplot(133)
plt.bar(x, y)
```
