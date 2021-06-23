# Gitlab_CI  

CI-continuous Integration  
: 새로운 코드에 대한 변경사항이 꾸준히 자동으로 빌드 및 테스트 되어 여러 개발자가 동시에 작업할 때 인터럽트가 발생하는 것을 방지 가능  
: 자동으로 (빌드 - 테스트 - 머지)를 해줌  

CI가 없으면 개발자가 코드 작성 - 빌드 - 테스트 - 배포까지 다 해주어야 함  
**CI를 한번만 잘 작성해놓으면 개발자는 코드만 작성하면 됨**  
```  
## CI하지 않고 빌드하기  
npm install express  # express로 어플을 하나 만듬  
npm install --save-dev mocha should supertest  
```  
Heroku : CI 없이 배포를 위한 사이트   

## CI로 자동화 시키기  

1. .gitlab-ci.yml 파일을 다음과 같이 저장한다.   
![image](https://user-images.githubusercontent.com/74280650/123088605-e8a4de80-d460-11eb-9acf-7187bf22ec56.png)  

2. 이를 Git lab에 push하면 자동으로 Git lab이 test 코드를 돌려줌  

3. 실제 프로젝트에 CI적용 시 다음과 같이 진행함  
  - Unprotected branch 에 Push 할 때  
  : test 및 lint 진행  
  - Protected branch에 MR 할 때  
  : test 및 lint 진행, 실패 시 Merge 불가  
  - PRotected branch에 Push / Merge 할 때  
  : test 및 lint 진행, 성공시 deploy  
  
4. Git lab - Settings - General로 이동
  : Merge checks -> pipelines must succeed 체크   
  : **이를 통해 CI를 Pass하지 못한 경우 Merge 할 수 없도록 설정 가능**  
  


