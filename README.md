# API로 JSON/XML문서 읽어오기 연습

# API_KEY와 BASE_URL + END_POINT 합쳐서 URL을 만들어준다 
API_KEY = {내가 받은 키값}
URL = BASE_URL + END_POINT

# 파라미터를 채워준다
params = {
    'serviceKey' : API_KEY,
    'pageNo' : '1',
    'numOfRows': '10'
}

# response = request.get으로 불러와준다

import requests
response = requests.get(URL, params = params)

# URL을 생성해준다
from requests import Request,Session
s = Session()
req = Request('GET', URL, params=params)
prepped = s.prepare_request(req)
print(prepped.url)  # 준비된 요청의 URL 확인

# 생성된 URL에서 경로를 확인하여 데이터프레임 형태로 출력한다
import pandas as pd
pd.read_xml(response.content, xpath =  '/ForeignLocalGovernmentsYear/row')
