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









