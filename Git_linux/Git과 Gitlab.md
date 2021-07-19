## Git 특징
1. 효율적인 협업을 위해 사용한다.  (수정사항이 겹칠경우 이를 처리해야하는 문제점을 해결)
2. 쉬운 버전관리 (각각의 파일을 스냅샷 형태로 저장한다)  
3. 가지 치기와 병합 (여러 가지 작업이 겹치는 경우를 방지)  
4. 가볍고 빠르다. (서버와의 통신 없이 로컬에서 진행됨. 즉 분산 작업에 매우 효율적임)  
**여기서 개발자들은 코드를 개발하는데 집중하고, 통합 관리자들은 개발된 코드를 테스트하고 병합하는 데 집중함**   
5. 데이터 무결성 보장 (16진수 문자열로 이루어진 commit id로 개발자 기록이 남겨짐)  
6. 준비 영역 (Staging area를 통해 commit 을 위한 준비 공간이 존재)  
7. 오픈 소스 (소스 코드 공개 상태에서 누구나 프로젝트에 기여 가능)  
8. Git 호스팅 서비스  

## Git 실습  

```  
$ git version
git version 2.30.0.windows.2

$ git config --global user.name "KimHanBin" 
# 이름 설정  

$ git config --global user.email "rlagksqls17@naver.com"
# 이메일 설정  

$ git config --list
user.email=rlagksqls17@naver.com
user.name=KimHanBin  
# 저장소가 시작되지 않은 상태에서는 유저 설정 시에 반드시 --global을 입력해야 함.   
```  

## Git 저장소 생성  
```  
Git init # 기존의 디렉토리를 git repository로 설정  
joo@pc MINGW64 /c/users/joo/Desktop/Python_study/git_study
$ git init
Initialized empty Git repository in C:/Users/joo/Desktop/Python_study/git_study/.git/  


```  

## 정해진 저장소에 새로운 파일을 반영시키려면?  
![image](https://user-images.githubusercontent.com/74280650/122907730-66e48080-d38e-11eb-8d4a-56dcf932eb44.png)  
```  
git add comment.js  
# comment.js 파일을 준비영역으로 보냄  

git add . # 한꺼번에 파일을 보낼 때  
git status # Staging area의 어떤 파일이 변경되었는지 확인 가능  
```  

## Git 저장소 반영  
comment.js **파일을 staging 하였을 때**, commit을 추가  
```  
git commit -m "문자" #.git 저장소 내에 staging 파일을 저장  
git commit --amend # 앞에서 적은 메세지에 오타가 있거나 누락된 파일이 있을 경우 내용 변경  
git log # 저장소 반영 내용이 궁금할 경우 사용  
```  
## Git 관리 상태 확인  
git status : staging file 들의 상태 확인    
git log : .git repositroy에 존재하는 history 확인  
  -p : 각 commit의 수정 결과를 보여주는 diff와 같은 역할을 수행  
  -n : 상위 n개의 commit 만 보여줌  
  --stat : 어떤 파일이 commit 에서 수정되고 변경되었는지, 파일 내 라인이 추가되거나 삭제되었는지 확인  
  --pretty=oneline : 각 commit을 한 줄로 출력
  **--graph** : commit 간의 연결된 관계를 아스키 그래프로 출력  
  -S function_name : 코드에서 추가하거나 제거된 내용 중 특정 텍스트가 포함되어 있는지 검사  
git diff : commit 된 파일 중 변경된 사항을 비교할 때  

## Git Branch  
: 독립적으로 어떤 작업을 진행하기 위한 개념  
: 각각의 Branch는 다른 Branch의 영향을 받지 않음  

메인 Branch : 배포할 수 있는 수준의 안정적인 Branch  
토픽 Branch : 기능 추가나 버그 수정과 같은 단위 작업을 위한 Branch  

```  
git branch like_feature  # Git Branch 생성 
git branch # git Branch 현재 상황 확인  
git checkout like_feature # 현재 작업 branch 전환  
# snapshot을 넘나들 때도 사용 가능  
```  

![image](https://user-images.githubusercontent.com/74280650/122944507-d9675780-d3b2-11eb-9564-1e984ed7b34a.png)
  
## 병합  
fast-foward   
```  
git checkout like_feature  # 브랜치 이동  
```  
![image](https://user-images.githubusercontent.com/74280650/122947573-395efd80-d3b5-11eb-84d5-891354534173.png)
  

```  
git checkout master # 브랜치 이동  
git merge like_feature # master브랜치에서 like_feature Branch를 병합  
# like_feature Branch의 내용이 master Branch에서 업데이트 된 내용이기 때문에 곧바로 merge 되는 것을 확인 가능  
# 추가된 내용이 겹쳐지는 거임 (fast-foward)  
```  

갈라지는 branch 병합  
![image](https://user-images.githubusercontent.com/74280650/122947672-4bd93700-d3b5-11eb-8139-05cf7fb9459a.png)
  
```  
git log --graph --all  # 커밋 그래프 확인  
git merge like_feature  
```  

![image](https://user-images.githubusercontent.com/74280650/122948155-a8d4ed00-d3b5-11eb-8ec9-d69687c5028c.png)
  
```  
git branch --merged # Merge된 Branch를 확인  
```  
**사용을 마친 branch는 다음 코드와 같이 삭제해주어야 함**  
```  
git branch -d <branch name>  
```  

## Merge conflict  
**: Merge 한 두 Branch에서 같은 파일을 변경했을 때 충돌이 발생함**  
```  
각각 다른 브랜치에서 같은 파일을 서로 다른 내용으로 작업시 충돌이 발생함  
git merge like_features # 수행시 충돌  
```  

![image](https://user-images.githubusercontent.com/74280650/122954727-a759f380-d3ba-11eb-832d-89acc4a6597d.png)
  
먼저 git stauts 명령어로 어느 파일에서 충돌이 발생했는지 확인하고,  
충돌이 일어난 comment.js 파일을 열어본다.  
수정 완료 후, git add, git commit, 다시 merge  

**충돌 방지하는 것도 중요함**  

**master branch의 경우 배포가 가능한 안정적인 수준으로 제작되어야 하기 때문에 잦은 변화는 안 됨**  

## 원격 저장소  

1. 원격저장소 받아오기  
: 인터넷이나 네트워크 어딘가에 있는 저장소  

1-1 ```Git clone``` 기존의 git repository를 복사  (현재 폴더 내에 새로운 폴더를 생성)
**만약 현재 폴더를 저장소로 쓰고 싶을 경우 git clone 명령의 마지막에 '.' 을 찍어줌**  
```git clone [주소]```
1-2 gitlab또는 Github에서 원하는 프로젝트에서 Clone 누름  
1-3 여기서 clone with HTTPs 옵션으로 선택함  
1-4 Git clone 뒤에 clone 버튼으로 확인한 원격저장소의 주소를 넣어줌  
1-5 ```git remote add origin [저장소 주소]```  # 명령어로 연결  
1-6 ```git remote``` # 연결 확인  
1-7 ```git remote show origin``` # 원격 저장소 확인  
1-8 ```git remote rename origin git_test``` : 원격 저장소 단축 이름 변경  
1-9 ```git remote rm git_test``` : 저장소 삭제  

2. 원격 저장소 동기화  
2-1 pull : 원격 저장소에서 데이터 가져오기  + 병합  
2-2 Fetch : 원격 저장소에서 데이터 가져오기만 함  
2-3 Push : 로컬 저장소에서 작업한 내용을 원격저장소에 반영함  
**다른 사람이 먼저 Push 한 상태에서는 Push할 수 없음, 따라서 Merge 먼저 해야 함**  

> 예를 들어, 계산기 프로젝트를 한다고 쳐보자.  
> 1. Calculator라는 원격저장소를 github에 저장했다. (파일 아무것도 없음)  
> 2. 네 사람 각자 더하기, 빼기, 곱하기, 나누기 기능을 가진 코드를 짜야한다.  
> 3. 먼저 네 사람은 모두 Calculator 원격저장소를 다운 받아 연결해야한다.  
> 4. 각자 기능을 만든다. Branch를 만들어 기능을 세분화하는 것 가능하나, 반드시 병합해주어야한다.  
> 5. 병합하고나면, 해당 원격저장소에 push 한다. (이때 다른사람이 작업한 것을 Merge 먼저 해주어야 한다.)  

## Origin/master  
```
git remote add origin [주소]  
# 이는 원격저장소의 이름을 origin으로 지정한다는 의미임  
보통 기본적으로 만들어진 원격저장소의 이름은 origin이 default 값임  
```  






