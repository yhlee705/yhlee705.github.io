---
layout: single
title: "Web Scraping, Web Crawling"
---

# Web Scraping, Web Crawling

* <b>웹스크래핑</b>
 1. 목적: 특정 웹사이트나 페이지에서 원하는 데이터를 추출하는 것이 주목적입니다.

 2. 작동 방식:
      - HTML 구조를 분석하여 필요한 데이터를 식별합니다.
      - CSS 선택자, XPath 등을 사용하여 특정 요소를 타겟팅합니다.
      - 정규표현식이나 파싱 라이브러리를 사용하여 데이터를 추출합니다.

 3. 사용 사례:
      - 가격 비교 웹사이트에서 상품 정보 수집
      - 뉴스 기사 콘텐츠 추출
      - 소셜 미디어 포스트 데이터 수집

 4. 도구: Beautiful Soup, Scrapy, Selenium 등


* <b>웹크롤링</b>

 1. 목적: 웹의 구조를 탐색하고 여러 페이지를 자동으로 방문하는 것이 주목적입니다.

 2. 작동 방식:
        - 시작 URL에서 출발하여 링크를 따라 다른 페이지로 이동합니다.
        - 방문한 페이지의 URL을 저장하고 새로운 링크를 발견하면 큐에 추가합니다.
        - 로봇 배제 표준(robots.txt)을 준수하며 웹사이트를 탐색합니다.

 3. 사용 사례:
        - 검색 엔진의 웹페이지 색인화
        - 웹 아카이빙
        - 대규모 데이터 수집 프로젝트

 4. 도구: Scrapy, Nutch, Heritrix 등

주요 차이점:

1. 범위: 스크래핑은 특정 페이지나 사이트에 집중하지만, 크롤링은 여러 사이트와 페이지를 광범위하게 탐색합니다.

2. 데이터 처리: 스크래핑은 데이터 추출과 구조화에 중점을 두는 반면, 크롤링은 페이지 발견과 링크 추적에 집중합니다.

3. 복잡성: 스크래핑은 상대적으로 간단할 수 있지만, 크롤링은 더 복잡한 로직과 자원 관리가 필요합니다.

4. 자원 사용: 크롤링은 일반적으로 더 많은 네트워크 대역폭과 저장 공간을 사용합니다.

실제 응용에서는 이 두 기술이 종종 결합됩니다. 예를 들어, 웹 크롤러로 여러 페이지를 탐색한 후 웹 스크래퍼로 각 페이지에서 필요한 데이터를 추출하는 방식으로 사용될 수 있습니다.

이 기술들을 사용할 때는 웹사이트의 이용 약관, 법적 제한 사항, 그리고 윤리적 고려사항을 항상 염두에 두어야 합니다.

<br>

## 동적 페이지 웹스크래핑

Selenium과 BeautifulSoup을 함께 사용하여 동적 웹 페이지를 스크래핑할 수 있음. <br>
Selenium은 웹 브라우저를 자동화할 수 있으며, BeautifulSoup은 웹 페이지의 HTML 코드를 파싱하여 원하는 데이터를 추출.


```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from bs4 import BeautifulSoup  # 정상적으로 import되지 않는 경우가 있는데 pip 업그레이드 후 vscode 재실행 해본다.
import time
```


```python
# webdriver.Chrome을 사용하여 Selenium 웹 드라이버를 설정
options = webdriver.ChromeOptions()
#options.add_argument('--headless')  # 브라우저를 보이지 않게 실행
options.add_argument('--no-sandbox')  # 샌드박스 모드 비활성화
options.add_argument('--disable-dev-shm-usage')  # /dev/shm 사용 비활성화 (메모리 문제 해결용)

driver = webdriver.Chrome(options = options)
```

* '--no-sandbox' 옵션
  * 의미: "sandbox" 기능을 비활성화
  * 설명
    * 크롬 브라우저에서 프로세스를 격리하여 보안을 강화하는 기능(브라우저가 실행되는 동안 서로 다른 탭이나 플러그인이 서로 간섭하지 않도록 함)
    * 특정 서버 환경이나 컨테이너화된 환경에서는 샌드박스 기능이 문제를 일으킬 수 있음
  * 용도: 주로 리소스가 제한된 환경, 예를 들어 Docker 컨테이너나 CI/CD 파이프라인에서 Selenium을 실행할 때 사용
  * 샌드박스를 비활성화하면 브라우저 프로세스 간의 격리가 사라져 보안에 취약해질 수 있음<br>
* '--disable-dev-shm-usage' 옵션
  * 의미: /dev/shm 사용을 비활성화
  * 설명
    * 기본적으로 Chrome은 /dev/shm (공유 메모리 디렉토리)을 사용하여 브라우저의 메모리 맵 파일을 저장
    * 그러나 이 디렉토리의 크기가 제한적일 수 있어, 특히 Docker 컨테이너와 같은 환경에서는 기본 설정 크기(64MB)로 인해 메모리 부족 문제가 발생할 수 있음
    * 이러한 경우 이 옵션을 사용하여 Chrome이 /dev/shm 대신 디스크를 사용하도록 할 수 있음
  * 용도: 리소스가 제한된 환경, 특히 Docker 컨테이너와 같은 환경에서 메모리 부족 문제를 방지하기 위해 사용



```python
# driver.get(url)을 통해 지정한 URL로 브라우저를 열고 웹 페이지에 접근
url = "https://www.iea.org/energy-system/carbon-capture-utilisation-and-storage/direct-air-capture"  # 스크래핑할 웹 페이지 URL
driver.get(url)
```


```python
# time.sleep(3)을 사용하여 동적 콘텐츠 로드를 기다림 (필요한 경우 조정 가능)
time.sleep(3)

# driver.page_source를 통해 현재 웹 페이지의 HTML 소스 가져오기
page_source = driver.page_source
```


```python
# BeautifulSoup을 사용하여 페이지 소스 파싱하고 원하는 데이터를 추출
soup = BeautifulSoup(page_source, 'html.parser')
```


```python
# 필요한 데이터를 추출
# 예시: h1 태그의 텍스트를 추출
heading = soup.find('h1').get_text()
print(f"Heading: {heading}")
```

    Heading: Direct Air Capture
    


```python
# 드라이버 종료
driver.quit()
```


```python

```
