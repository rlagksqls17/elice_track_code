# mySQL  

## 데이터베이스

```mysql
#  사용 중인 데이터베이스 조회
SELECT DATABASE();

# alembic_version 삭제 
DELETE FROM alembic_version;
```

## 테이블

```mysql
# 해당 테이블의 개요를 보여준다.
DESC 테이블 명;

# 사용중인 테이블 목록들 조회
SHOW TABLES;

# 해당 테이블의 모든 row를 보여준다.
SHOW * FROM 테이블 명;

# 해당 테이블의 모든 row를 삭제한다.  
DELETE FROM 테이블 명;

CREATE TABLE 테이블이름

# FK를 포함시켜 테이블을 만든다.
ALTER TABLE TABLE2 ADD FOREIGN KEY(id) REFERENCES table1(id);

mysql> CREATE TABLE user_info
    -> (_id INT PRIMARY KEY AUTO_INCREMENT,
    -> userId VARCHAR(32) NOT NULL,
    -> name VARCHAR(32) NOT NULL,
    -> image MEDIUMBLOB,
    -> FOREIGN KEY (userId)
    -> REFERENCES users(userId));
    
 mysql> CREATE TABLE education
    -> (userId VARCHAR(32) NOT NULL,
    -> school_name VARCHAR(32),
    -> major VARCHAR(32),
    -> degree VARCHAR(32),
    -> FOREIGN KEY (userId)
    -> REFERENCES users(userId));
 
# 테이블 삭제
DROP TABLE 테이블명;

```

## 컬럼  

```mysql
# 컬럼명 변경 
ALTER TABLE 테이블명 CHANGE 기존컬럼명 변경할컬럼명 컬럼타입
```

```python

```

주어진 길이가지고 어떻게 컴포넌트를 복제하지??

주어진 길이 만큼 컴포넌트를 복제해야 함  

길이 만큼 요소를 만들어 리스트에 저장 [1, 2, 3]



```jsx
const [mappingElement, setMappingElement] = useState([])

useEffect(
    list = []
for {i = 0; i < length; i++}(
	list.push(i)
))

setMappingElement(list)

map(elements => <userInfo index={elements}/>)
```



초기 네트워크에 들어갔을 때, 사용자 프로필을 모두 보여줘야 한다.  

useRef와 useEffect를 혼용하자.  

먼저 입력창 state를 useRef로 저장해서 렌더링 되어도 이 state가 초기회되지 않도록 한다.  



입력창에 입력값을 입력하고, 검색버튼을 누르면, state를 일단 검사한다음에 검사가 통과되면 form을 통해 제출되고 

state가 바뀐다.



useEffect를 사용해서, useRef로 지정한 state값이 변경될 때마다 컴포넌트를 리렌더링한다.

물론 useRef로 인해서 검색값 state는 변하지 않는다.



useEffect에서는 입력값을 flask로 넘겨준다. flask에서는 입력된 값을 바탕으로 mysql에서 이름들을 모두 검색하고, 

해당되는 ID들을 싹 다 리스트로 넘겨준다. 그 ID를 렌더링 시 초기화되는 state에다가 저장한다.



이후 리스트를 매핑하는데, 매핑되는 각 요소에는 사용자요약프로필 컴포넌트가 담겨있다. 

그 각각의 컴포넌트는 useEffect를 시전하여 해당 ID에 맞는 user_info를 불러와서 정보를 리턴한다.

추가적으로 접속 버튼까지 생성되는데, 이 버튼을 클릭하면 새로운 페이지로 이동, 해당 ID의 상세컴포넌트를 불러온다.  



```jsx
    // Serve Component 1
    function UserInfo(){
    /*
    사용자 프로필 컴포넌트
        사진 (user_ImageComponent) : 클릭하면 수정 가능
        username : 이름 
        onlineMyself : 한 줄 소개 
            - isClick : state, 값에 따라 입력창 or 정보조회 렌더링 
            - UpdateInput : support Component
    */
        
        const [username, setUsername] = useState('이름')
        const [onelineMyself, setOnelineMyself] = useState('안녕하세요')
        const [isClick, setIsClick] = useState(false)

        useEffect(() => {
            fetch('/api/show_user_info', {
                method: 'post',
                headers: {
                    'Content-Type' : 'application/json'
                },
                body: JSON.stringify(props.researchid)
            })
            .then(r => r.json())
            .then(res => {
                if(res['status'] == 200){
                    setUsername(res['name'])
                    setOnelineMyself(res['onelineMyself'])
                }
                else{
                    return console.log("Not Found!")
                }
            }, [username, onelineMyself, isClick])
        })
        
    
        return (
            <div>
                <div>
                    <img src='' alt='프로필사진'/>
                </div>
                <div>{username}</div>
                <div>
                    한 줄 소개 :
                    {isClick ? 
                        <UpdateInput 
                            updateCase='onelineMyself' 
                            initState={onelineMyself}
                        /> 
                        : `${onelineMyself}`
                    }
                    {((props.researchid === ID) && !isClick) ? 
                        <button onClick={() => 
                            setIsClick(true)
                        }>
                        수정하기
                        </button>
                        : ""
                    }
                </div>
            </div>
        )
    }
```

## 유저  

```js
// 사용 중인 유저 보기
select user, host from user;

// 사용 중인 유저 삭제
drop user rlagksqls17@localhost;
```



## 포트  

```js
SHOW GLOBAL VARIABLES LIKE 'PORT'
```

## 접속

```mysql
mysql -u rlagksqls17 -p project;

http://elice@kdt-1st-project-60.koreacentral.cloudapp.azure.com
```

