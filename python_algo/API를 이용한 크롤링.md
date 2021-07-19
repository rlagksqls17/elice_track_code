## API?  
: 어떤 프로그램과 또 다른 프로그램을 연결해주는 매개체  
: 원본 데이터는 호환성 문제로 쉽게 사용할 수 없음 >> 따라서 API를 이용하여 사용자들이 원본 데이터를 사용함  
: 보통 API를 이용하여 데이터를 불러오는 경우는 데이터가 동적으로 변화하는 일이 많아 실시간으로 값을 불러와야 하는 경우임  

### requests.get(heders : )
: **API의 URL**에 GET 요청을 보내면 JSON 데이터를 얻을 수 있음  
: 몇몇 웹 사이트들은 크롤러 등을 통한 기계적인 접근을 막고 있기 때문에, 위 매개변수를 지정해줘야 함  

<특정 검색어를 입력하면, 해당 검색어에 관련된 음식점들의 리뷰 상위 5개를 각각 찾아 출력하는 코드>
```  
from bs4 import BeautifulSoup
import requests
import json            #json import하기

custom_header = {
    'referer' : 'https://www.mangoplate.com/',
    'user-agent' : 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/73.0.3683.103 Safari/537.36' }

def get_reviews(code) :
    comments = []
    
    #입력된 {code} 변수에 따라 아래 url (api의 url)이 달라짐
    url = f"https://stage.mangoplate.com/api/v5{code}/reviews.json?language=kor&device_uuid=V3QHS15862342340433605ldDed&device_type=web&start_index=0&request_count=5&sort_by=2"
    req = requests.get(url, headers = custom_header)
    
    # req에 데이터를 불러온 결과가 저장되어 있음
    if req.status_code == requests.codes.ok:
        print("접속 성공")
        reviews = json.loads(req.text) 
        for review in reviews:
            comment = review["comment"]
            comments.append(comment["comment"][0:40].replace("\n", "")) # 해당 리뷰의 40글자 만큼만 읽어옴
        return comments
    else:
        print("Error code")
    
    
def get_restaurants(name) :
    url = f"https://www.mangoplate.com/search/{name}"
    req = requests.get(url, headers = custom_header)
    soup = BeautifulSoup(req.text, "html.parser")
    
    # soup에는 특정 키워드로 검색한 결과의 HTML이 담겨 있음.
    # 특정 키워드와 관련된 음식점의 이름과 href를 튜플로 저장함,
    # 이름과 href를 담은 튜플들이 담긴 리스트가 반환됨.
    tag_a = soup.find('ul', class_="list-restaurants").find_all('a', class_ = "only-desktop_not")
    names = soup.find('ul', class_ = "list-restaurants").find_all('h2', class_= 'title')
    search_count = 0  
    result = []
    while(True):
        try: 
            name = names[search_count].get_text('h2',strip = True).replace("\n", "").replace("h2", " ")
            a_href = tag_a[search_count]['href']
            result.append((name, a_href))
            search_count += 1
        except IndexError:
            return result
        
def main() :
    name = '초밥'
    
    restuarant_list = get_restaurants(name)
    print(restuarant_list)
    
    for r in restuarant_list :
        print(r[0]) # 이름이 출력됨
        print(get_reviews(r[1])) # 그 이름을 검색했을 때 나오는 하이퍼링크를 참조한, 리뷰가 출력됨
        print("="*30)
        print("\n"*2)
        
if __name__ == "__main__" :
    main()
```
