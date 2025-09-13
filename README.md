# Crypto Auto-Trading Backtest Project

<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=Python&logoColor=white"> <img src="https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=Amazon-AWS&logoColor=white"> <img src="https://img.shields.io/badge/Telegram-26A5E4?style=for-the-badge&logo=Telegram&logoColor=white">

---

## 프로젝트 개요

### 투자 목표

코인 투자는 **변동성이 심해 장기적인 하락 방어와 상승 시 수익 극대화**가 동시에 요구된다. 본 프로젝트는 **자동화된 매매 전략**을 설계·백테스트하여, 하락기에도 스트레스 받지 않으면서 상승장에는 수익을 공유할 수 있는 전략을 검증한다.

**즉, MDD를 줄이면서 CAGR 극대화하는 것이 목표이다.**

<img width="1200" height="800" alt="Figure_1" src="https://github.com/user-attachments/assets/7b855997-51de-4b49-b37b-d57fb041de69" />



### 주요 기능

* **백테스트 환경 구축**: 다양한 시기(침체기, 급등기, 임의 기간)를 구분하여 전략 검증
* **포트폴리오 전략**: 다수의 코인에 비중을 배분하여 분산 투자
* **자동화 실행**: AWS 서버에서 매일 오전 9시에 매매 신호 계산 및 실행
* **알림 시스템**: 텔레그램을 통해 매수/매도 이벤트 및 대상 코인 실시간 알림

---

## 투자 전략

* **이동평균선 기반 매매**

  * 각 코인별 **단기, 장기 이동평균선(MA)** 계산
  * 종일 종가와 단기, 장기 이동평균선을 비교해 조건에 부합하면 매수/매도
* **포트폴리오 구성 (backtest\_portfolio.py)**

  ```python
  InvestCoinList = [
      {"coin_ticker":"KRW-BTC", "invest_rate":0.25},
      {"coin_ticker":"KRW-ETH", "invest_rate":0.20},
      {"coin_ticker":"KRW-SOL", "invest_rate":0.15},
      {"coin_ticker":"KRW-SUI", "invest_rate":0.15},
      {"coin_ticker":"KRW-XRP", "invest_rate":0.10},
      {"coin_ticker":"KRW-POL", "invest_rate":0.05},
      {"coin_ticker":"KRW-DOT", "invest_rate":0.03},
      {"coin_ticker":"KRW-ADA", "invest_rate":0.02},
  ]
  ```
* **포트폴리오 목표**: 개별 코인 변동성을 분산시키고, 시장 상승 시 수익을 공유하면서 하락 방어

---

## 백테스트 시나리오

* `recession_backtest.py`: 코인 **침체기**에 개별 코인 전략 검증
* `upturn_backtest.py`: 코인 **급등기**에 개별 코인 전략 검증
* `backtest_portfolio.py`: 임의의 기간을 설정해 **포트폴리오 전략** 검증

---

## 자동화 및 운영 환경

* **AWS 서버**: crontab을 활용해 매일 오전 9시 자동 매매 신호 계산
* **텔레그램 봇 연동**: 매수/매도 조건 충족 시 알림 전송

<img width="703" height="643" alt="image" src="https://github.com/user-attachments/assets/fc746a33-7b98-4937-a0bd-16914970f763" />

---

## Directory Structure

```bash
├── README.md                      <- 프로젝트 요약 설명
├── recession_backtest.py          <- 침체기 개별 코인 백테스트 코드
├── upturn_backtest.py             <- 급등기 개별 코인 백테스트 코드
├── backtest_portfolio.py          <- 포트폴리오 백테스트 코드
├── reports                        <- 분석 결과 및 시각화 저장
│   ├── portfolio_results.png
│   ├── individual_recession.png
│   └── individual_upturn.png
```

---

## 사용 기술 스택

* **언어/라이브러리**: Python (pyupbit, pandas, numpy, matplotlib)
* **환경**: AWS 서버 (자동 매매 실행)
* **알림 시스템**: Telegram Bot
* **분석 기법**: 이동평균선(MA) 기반 트레이딩 전략, 포트폴리오 분산 투자, 백테스팅

---

## 참고

* Upbit API (pyupbit)
* AWS EC2 / crontab 자동화
* Telegram Bot API

