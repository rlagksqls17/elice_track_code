## **CLI**    

CLI : Command Line Interface  

운영체제를 다루는 방법은 GUI 방식, CLI 방식이 있음   
CLI : bash, sh, zsh, powershell 등 다양함, 명령어 입력하면 운영체제에 전달해주는 역할  
> 이 Shell들을 실행하는 프로그램들을 콘솔 or 터미널이라고 함  

bash의 경우 리눅스나 맥에서 사용하는 Shell임  
윈도우는 bash가 안 깔려있기 때문에 Git-bash를 사용 (윈도우에서 사용가능한 bash)  

**리눅스에서 파일이나 디렉토리 앞에 '.'이 있으면 히든파일이다.**  

## **Git 원리**  
파일 수정후 저장시 (untracked) 상태가 되고,  
git add [파일 이름, 복수 개 가능] 시 (tracked) 상태가 된다.    
git commit -m "수정할 사항" 입력 시 master에 고유한 아이디가 올라가고, 이전에 올린 버전이 있으면 그 버전의 고유 아이디는 parent에 올라간다.  

parent 고유아이디가 버전마다 저장되어 있기 때문에 언제든지 Roll-Back 가능하다.    
*파일이 숨겨져 있기 때문에 git ls -a를 통해 전체파일을 살펴보며 공부하면 좋다.*   

레거시 : 프로젝트가 진행되며 계속해서 유전되는 버그    

##  **버전 관리의 중요성**  
**버전 관리를 해서 디버그를 훨씬 더 쉽게 할 수 있다.**    
**단일 기능 버전 관리도 필요**    


## Git log 간단히 보는 방법과 롤백 방법  
HEAD를 원하는 버전의 ID에 올려놓게 해야 한다.  
```  
 git log --oneline
91875fd (HEAD -> master) work 5
f9b6352 work 4
c968d88 work 3
8ad2762 work 2
326a7a5 work 1
```    
```  
$ git log --oneline
91875fd (HEAD -> master) work 5
f9b6352 work 4
c968d88 work 3
8ad2762 work 2
326a7a5 work 1

joo@pc MINGW64 ~/Desktop/work (master)
$ git checkout c968d88
Note: switching to 'c968d88'.
```  

**checkout 하게 되면, Git은 Head가 가리키는 버전을 출력함, 즉 checkout은 Head를 바꿈**  
**따라서 롤백하게 되면 우리가 작업한 애들이 안 보임**    

헤드도 표시  
```  
$ git log --oneline --all
91875fd (master) work 5
f9b6352 work 4
c968d88 (HEAD) work 3
8ad2762 work 2
326a7a5 work 1
```   


아래처럼 입력하면 화살표가 아닌 콤마로 가리켜짐  
  
  
  
**dettached**  
```
joo@pc MINGW64 ~/Desktop/work ((c968d88...))
$ git checkout 91875fd
Previous HEAD position was c968d88 work 3
HEAD is now at 91875fd work 5

joo@pc MINGW64 ~/Desktop/work ((91875fd...))
$ git log --oneline --all
91875fd (HEAD, master) work 5
f9b6352 work 4
c968d88 work 3
8ad2762 work 2
326a7a5 work 1
```  

이렇게 해도 나중에 새로운 커밋을 할때 master는 c(원래 버전)를 가리키고,  HEAD는 D(신 버전)를 가리키게 됨  
  
  
  
**attached**  
```  
joo@pc MINGW64 ~/Desktop/work (master)
$ git log --oneline --all
91875fd (HEAD -> master) work 5
f9b6352 work 4
c968d88 work 3
8ad2762 work 2
326a7a5 work 1
```    
  
   

**즉 롤백 후 돌아가고 싶을 때는 master가 현재를 가리키기 때문에 HEAD를 그냥 master로 체크아웃 하면 됨**  

: git은 어떤 경우에도 삭제나 수정하지 않는다.  (불변성)  
: 따라서 삭제된 워크의 커밋 아이디를 알고 다시 체크아웃하면 복구 가능  













