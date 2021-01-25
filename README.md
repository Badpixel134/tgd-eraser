# tgd-eraser
tgd.kr eraser.
트게더 지우개

파이썬으로 만듬. 조잡함.

https://greeksharifa.github.io/references/2020/10/30/python-selenium-usage/ 여기서 본 예제를 토대로 함.

해당 게시글의 selenium 설치까지 진행하고 해당 코드들을 사용하면 될것.

파이썬 만진지 5분밖에 안된 사람이 만들었다보니 제대로 쓰는 방법도 잘 모르겠음.
IDLE 로 실행했을 경우 잘 작동함.

여기서부터
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from time import sleep

options = webdriver.ChromeOptions()
options.add_argument('window-size=1920,1080')

driver = webdriver.Chrome('chromedriver', options=options)
driver.implicitly_wait(5)

여기까지 한 다음 크롬 창이 뜨면 거기서 직접 트게더 로그인.


for i in range(1, 1000):
	driver.get(url='https://tgd.kr/member/mylist')
	search_box = driver.find_element_by_xpath('//*[@id="main-content"]/div/div[1]/table/tbody/tr[1]/td[1]/a')
	search_box.click()
	sleep(3)
	delete = driver.find_element_by_xpath('//*[@id="article-content-wrapper"]/div[4]/a[2]')
	delete.click()
	sleep(3)
	confirm = driver.find_element_by_xpath(' //*[@id="main-content"]/div/form/div/button')
	confirm.click()
	sleep(3)
  
  그다음은 이걸 진행해서 기다리면 알아서 해결된다. recaptcha 뜨면 창 모두 닫고 처음부터 다시 시작하면됨.
