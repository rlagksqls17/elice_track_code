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




