# 중고차 예측 프로젝트

!크롬드라이버가 필요합니다!

사이킷런과 셀레니움을 이용해서 중고차 가격을 예측하는 프로그램입니다.


차량정보크롤링.py : 중고차 사이트에 들어가서 필요한 데이터를 수집후 엑셀에 자동저장

중고차가격예측.py : 엑셀에 저장한 데이터를 숫자형으로 전처리하고 앙상블학습 진행, 결과 출력



데이터 전처리 방식
![image](https://user-images.githubusercontent.com/83406220/121778005-d066d100-cbcf-11eb-845f-5637eadebac5.png)

차량번호와 제시번호는 drop하고
연식은 연도만 뽑아냅니다
숫자데이터에 있는 불필요한 , 만원 등은 날려버립니다.
labelencoder를 이용하여 문자형데이터를 숫자형으로 바꿉니다
연비 같은 데이터는 결측값을 평균으로 넣습니다

성능이 제일 잘나온 Xgboost기준 입니다.

![y_test](https://user-images.githubusercontent.com/83406220/121778106-61d64300-cbd0-11eb-836e-2976d9645b80.png) y_test
![예측](https://user-images.githubusercontent.com/83406220/121778107-63077000-cbd0-11eb-9210-c7e89ea2946e.png) y_pred


![오차](https://user-images.githubusercontent.com/83406220/121778111-6569ca00-cbd0-11eb-9000-2637c1776f34.png) 
제대로 예측한 것이 70%정도 나머지 25%정도는 500만원가량 오차가 발생합니다.

오차가 심하게 발생하는게 있는데

가격은 비싼데 연비나 배기량이 누락되서 평균치를 넣어도 소용이 없는 점
애초에 데이터량이 적은 점(이건 늘리는 게 가능)
분명 같은 데이터인데 이름이 다른 것 (검정, 검정색, 검은색 등)

제일 문제인건 생각보다 결측값이 많은게 문제인것 
