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


