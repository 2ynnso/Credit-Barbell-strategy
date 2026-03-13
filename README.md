# Credit Barbell Strategy

크레딧 바벨 전략 백테스트와 VIX 필터 확장 버전을 정리한 저장소입니다. 이 저장소는 `regime-detection`과 분리된 별도 공유용 저장소이며, GitHub에는 최종 노트북과 핵심 결과물만 깔끔하게 올리는 것을 기준으로 구성했습니다.

## Repository Structure

```text
.
├── credit-barbell-strategy.ipynb
├── data/
├── results/
│   ├── figures/
│   └── reports/
├── README.md
└── .gitignore
```

- `credit-barbell-strategy.ipynb`
  최종 분석 노트북
- `data/`
  원천 데이터 또는 중간 가공 데이터를 두는 위치
- `results/figures/`
  전략 성과와 레짐 변화 시각화
- `results/reports/`
  백테스트 요약, 월별 상세 성과표, 레짐별 성과표

## Strategy Summary

이 전략은 크레딧 자산과 안전자산을 함께 운용하는 바벨 구조를 기본으로 합니다. 매크로 및 신용 스프레드 신호를 바탕으로 시장 국면을 나누고, VIX를 추가 필터로 활용해 급격한 위험 확대 구간에서 방어적으로 대응하는 것이 핵심입니다.

주요 구성 요소:

- 크레딧 노출과 안전자산 노출의 바벨 구조
- 신용 및 매크로 기반 레짐 분류
- VIX 기반 추가 위험 제어
- 월별 성과, 누적 성과, 레짐별 비중 변화 검증

## Main Outputs

### Backtest Performance

![Backtest Performance](results/figures/backtest_performance.png)

### Regime Timeline

![Regime Timeline](results/figures/regime_timeline.png)

### VIX Signal Comparison

![VIX Signal Comparison](results/figures/signal_comparison_vix.png)

## Result Files

- `results/reports/strategy_VIX_TLT_mix_report.xlsx`
  전략 성과 요약 리포트
- `results/reports/strategy_monthly_details.xlsx`
  월별 수익률 및 상세 결과
- `results/reports/barbell전략_레짐별 비중과 성과_SAA.xlsx`
  레짐별 자산 비중과 성과 정리

## Data And Dependencies

노트북 실행 시 사용하는 주요 패키지:

- `pandas`
- `numpy`
- `matplotlib`
- `yfinance`
- `fredapi`
- `openpyxl`

예시 설치:

```bash
pip install pandas numpy matplotlib yfinance fredapi openpyxl jupyter
```

## How To Run

1. 가상환경을 생성합니다.
2. 필요한 패키지를 설치합니다.
3. FRED API Key가 필요하면 환경변수 또는 노트북 설정 셀에 입력합니다.
4. `credit-barbell-strategy.ipynb`를 열어 순서대로 실행합니다.
5. 산출물은 `results/` 폴더 기준으로 관리합니다.

## Upload Policy

GitHub 업로드 시 원칙은 아래와 같습니다.

- 루트에는 최종 노트북과 설명 문서만 유지
- 결과 이미지는 `results/figures/`로 분리
- 결과 엑셀은 `results/reports/`로 분리
- 초안 노트북, 참고 PDF, 중간 실험 파일은 업로드 대상에서 제외

즉, 이 저장소는 발표 및 공유용 최종 결과물 저장소로 유지합니다.
