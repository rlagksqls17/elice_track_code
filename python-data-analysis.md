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
json.loads(dict_string) : 딕셔너리를 JSON 형태의 문자열로 반환
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
```



# ---

# 데이터 시각화

## matplotlib  

```python
```

