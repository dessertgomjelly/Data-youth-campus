# 🫥 데이터 청년 캠퍼스 : 빅데이터 분석 및 비즈니스 인사이트 역량 제고 과정
[서울시 소상공인 상권 군집화와 폐업 예측을 통한 창업비서 모델](https://github.com/dessertgomjelly/Data-youth-campus/blob/main/%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%8E%E1%85%A5%E1%86%BC%E1%84%82%E1%85%A7%E1%86%AB%20%E1%84%8F%E1%85%A2%E1%86%B7%E1%84%91%E1%85%A5%E1%84%89%E1%85%B3%20%E1%84%8E%E1%85%AC%E1%84%8C%E1%85%A9%E1%86%BC.pdf) 
<br>
<br>

## [팀원 역할]
- 이윤지 : EDA, 모델링
- 권민서 : PPT(UI&UX)
- 권채영 : Research 
- 문성준 : EDA, 모델링
- 엄서윤 : Research, EDA
- 오현석 : Research 
- 조한결 : 어도비(UI&UX)
<br>


## [프로젝트 진행 기간]
2023.07.03 ~ 2023.08.29 (8주간 진행)

<br>


## [수상 내역]
- [🏆 상명대학교 프로젝트 평가 우수상](https://github.com/dessertgomjelly/Data-youth-campus/blob/main/Awards/awards1.jpeg)
- [🏆 한국정책학회 빅데이터 분석 분야 프로젝트 평가 우수상](https://github.com/dessertgomjelly/Data-youth-campus/blob/main/Awards/awards2.jpeg)
<br>


## [주요 기능]
- ### 단계별 기능
  - 1단계 : 군집화를 통한 상권 특성에 따른 입지 선정
  - 2단계 : 폐업률 예측 모델을 통한 생존전략 컨설팅
  - 3단계 : 매출 예측 모델을 통한 마케팅 타겟 컨설팅
    
<img width="700" alt="창업 비스" src="https://github.com/dessertgomjelly/Data-youth-campus/assets/127851446/7162f8ac-5ce6-4557-9396-f0ccade13518">

<br>



- ### 어도비 xd를 통한 컨설팅 시나리오 구성

<img width="800" alt="어도비xd" src="https://github.com/dessertgomjelly/Data-youth-campus/assets/127851446/20fdaaa5-39fb-45b9-a482-b98ee142a660">


  - [해당 링크를 클릭하면 창업 비서 홈페이지로 연결 됩니다.](https://xd.adobe.com/view/5738df5a-27a5-4ef2-8b12-f71b1987e799-026b/?fullscreen)


<br>


## [배경]
- ### 개발 목적 및 필요성
    - 기존 상권 분석 서비스는 단순 상권 정보 제공에서 그치는 한계
    - 상권 선택에서 끝나는 것이 아닌 구체적인 '생존 전략 컨설팅'을 제공하여 소상공인이 창업 후 가지는 경영적 어려움을 지원한다.

<br>



## [데이터 수집]
- ### 공공 데이터 포털
    -  ‘우리마을가게 상권분석 서비스’ 데이터: 2018-2021년도 서울시 생활인구, 직장인구, 상권별 추정매출, 상권변화지표, 점포, 집객시설에 대한 공공 데이터
- ### 서울시 상권분석 서비스
    - 2018-2021년도 서울시 점포 생존율, 가구 소득분위, 지역 임대시세에 대한 공공 데이터

<br>


## [데이터 전처리]
- #### 1-1 상주, 생활, 직장인구 통합.ipynb
  - 서울시 상주인구, 생활인구, 직장인구 데이터 통합
  - ‘stay_live_work_multiindex_drop_data.csv’ 데이터 프레임 생성
 
- #### 1-2 상권변화지표, 소득소비 통합.ipynb
    - 상권변화지표, 소득소비 데이터 통합
    - ‘money.csv’ 데이터 프레임 생성

- #### 1-3 업종별 매출액 변수 추가+top10 분류.ipynb
    - 업종별 매출 금액(amount), 업종별 매출 비율(prob) 변수 추가, 업종 카테고리 분류
    - 'category10_amount_prob.csv' 데이터 프레임 생성
 
- #### 1-4 서울시 상권분석 서비스 변수 추가.ipynb
    -  위의 세 가지 데이터 파일을 통합
    -  서울시 상권분석 서비스에서 가져온 점포 생존율, 가구 소득분위, 지역 임대시세 데이터를 ‘행정동 기준’으로 통합
<br>


|               EDA : 업종 재분류                |            EDA : 독립 변수              |             EDA : 종속 변수              |
| :--------------------------------------------: | :------------------------------------: | :--------------------------------------: |
| 업종 카테고리 81개 -> 20개로 분류                | 교통 시설 수 : 공항, 철도, 버스터미널, 지하철, 버스 정거장 | (폐업률)을 평균보다 큰 경우 1, 작은 경우 0으로 범주화 |
| 상위 10개의 업종을 최종 사용 변수로 선정        | 교육 시설 수 : 유치원수, 초등학교수, 중학교수, 고등학교 수, 대학교수 | (주중/주말 매출) 분기별 매출 금액 군집별 이상치 제거 |
| 새로운 변수 설정 : 상권별 업종/매출 비율(prob)  | 편의 시설 수 : 은행수, 종합병원수, 일반병원수, 약국수, 백화점수, 슈퍼마켓수, 극장수 | (주중/주말 매출) 매출 금액을 0.33과 0.66을 기준으로 3구간으로 범주화 |

<br>




## [모델 선정]
- #### 클러스터링
    - 2-1 클러스터링(업종).ipynb
    - 업종 10개를 선정하여, 주성분 분석과 Elbow Method를 통해 업종에 따른 군집화
 <img width="700" alt="테블로 시각화" src="https://github.com/dessertgomjelly/Data-youth-campus/assets/127851446/c879d81b-7082-4ecb-96e2-5d7af943015f">
<br>
<br>

- #### 예측 모델 (폐업률)
  - 로지스틱, 랜덤포레스트, XG Boost, 의사결정 나무 4개의 모델 
  -  각 모델마다 기본모델, 그리드 서치, 컷오프 방법 등을 이용해 하이퍼파라미터 조정
  -  군집별 평가지표를 통해 최적의 모델 선정
  -  XGBoost의 성능 지표가 높지만, 다른 데이터에 대해 일부 변수의 중요도가 0이 되는 과적합의 가능성을 고려하여 랜덤 포레스트 모델로 최종 선정
<img width="700" alt="폐업률 모델" src="https://github.com/dessertgomjelly/Data-youth-campus/assets/127851446/98803969-37d6-4b50-ab8e-9c20f9216fc1">

<br>
<br>


- #### 예측 모델 (주중매출, 주말매출)
    - 로지스틱, 랜덤포레스트, XG Boost, 의사결정 나무 4개의 모델 
    - 그리드 서치를 통한 모델링 진행 후 4개의 모델 중 평가 지표를 통한 최적의 모델 선정
<img width="700" alt="주중 매출 모델" src="https://github.com/dessertgomjelly/Data-youth-campus/assets/127851446/138b1264-ccee-46a8-9069-10da7f87fc77">
<img width="700" alt="주말 매출 모델" src="https://github.com/dessertgomjelly/Data-youth-campus/assets/127851446/66d6b21d-9815-4b1d-b388-135c44837d9d">

<br>

 ## [한계점 및 차별점]
- #### 차별점
    - 서울시 '생활 밀접 업종별' 특화 모형 구축
    - 업종별로 군집화하여 상권 특징별로 경영 솔루션을 제안
    - 폐업과 매출 모델 결과를 연관 시켜 다양한 마케팅 제안

- #### 한계점
    - 변수 카테고리 부족
        - 공공 데이터 이외 데이터를 사용한다면 여러 변수 추가 가능
    - 서울시 한정
        - 시군구/상권코드를 활용하여 추후 전국 단위로 확장 가능
    - 과적합 문제
        - 더 많은 데이터 수집을 통해 성능 개선
