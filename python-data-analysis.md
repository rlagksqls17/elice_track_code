# 데이터 분석  

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

## matplotlib  

```python
```

