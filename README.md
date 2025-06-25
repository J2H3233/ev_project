# 보고서
https://www.canva.com/design/DAGkVM7qDQw/P3Zg1elwo83iBKe83ARdtQ/edit

# 1. charging_station_count.ipynb
## 파일 목적
* 전국 충전소 수 파일을 기반으로 지역별/전국 충전소 월별 증가/누적수 전처리
### input
* ../data/raw/ev_charging_station.csv
### output
* ../data/processed/region_year_counts_matrix.csv

-----------------------------
# 2. ev_range.ipynb
## 파일 목적
* 조사한 전기차 주행거리를 기반으로 적절하게 주행거리를 반영할 수 있는 지표를 테스트
* 최종적으로 누적 최대 이동평균으로 전처리
### input
../data/raw/ev_range.csv
### output
../data/processed/final_ev_range.csv

-----------------------------
# 3. train_xgb_rf_prophet.ipynb
## 파일 목적
* 최종 전처리 파일을 기반으로 모델에 시간변수, 시차 변수, 이동 평균 변수, 출시 이벤트 플래그 조작등 모델입력 데이터 처리 및 저장(X_input)
* r2기반 grid_search로 xgb, rf의 모델 튜닝
* 튜닝된 모델로 전진 교차 검증방식으로 평가
* 전체 데이터 학습 모델 저장
* prophet 모델용 data_pp 데이터 처리
* prophet 모델 파라미터 설정, 전진 교차 검증 방식으로 평가
* 전체 데이터를 학습한 prophet 모델로 변수 영향력 시각화
### input
* ../data/processed/final_preprocessed_data.csv
### output
* ../data/processed/X_input.csv
* ../output/models/best_rf_model.pkl
* ../output/models/best_xgb_model.pkl

-----------------------------
# 4. clustering.ipynb
## 파일 목적
* 수집된 데이터 기반으로 군집화
* k값 결정을 위한 Elbow Method와 실루엣 점수 계산
* 클러스터 별 데이터 평균 시각화
* 군집화 결과 html로 시각화
### input
* ../data/raw/ev_subsidy.csv
* ../data/raw/Region.csv
* ../data/raw/Region_population.csv
* ../data/processed/ev_charging_count.csv
* ../data/raw/avg_latlng_by_region.csv
### output
* ../output/clustering.html

-----------------------------
# 5. visualize_feature.ipynb
## 파일 목적
* xgb, rf 모델의 shap 값 계산
* shap 시각화
* 설명 변수간 shap 의존성 시각화
* 설명 변수간 상관 계수 계산
* 설명 변수간 상관 관계 시각화
### input
* ../data/processed/X_input.csv
* ../output/models/best_rf_model.pkl
* ../output/models/best_xgb_model.pkl
### output
* 없음
