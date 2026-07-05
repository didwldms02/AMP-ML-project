# AMP-ML-project

머신러닝을 이용한 항균 펩타이드(Antimicrobial Peptide, AMP) 후보 서열 분류 프로젝트

## 프로젝트 개요

항생제 내성 문제가 심각해지면서 새로운 항균 물질 발굴이 중요해지고 있다. 항균 펩타이드(AMP)는 세균 세포막을 직접 파괴하는 기전으로 작용해 내성이 잘 생기지 않아 차세대 항균제 후보로 주목받는다.

본 프로젝트는 AMP와 비AMP 서열의 물리화학적 특성을 추출하고, 머신러닝 모델을 학습시켜 신규 AMP 후보를 분류·우선순위화하는 파이프라인을 구현한다.

## 데이터

| 용도 | 출처 | 개수 |
|------|------|------|
| 학습 (AMP) | AMPlify dataset | 3,338 |
| 학습 (non-AMP) | AMPlify dataset | 3,338 |
| 예측 대상 | APD (Antimicrobial Peptide Database) | 1,495 |

## 방법

1. FASTA 서열 파싱
2. 물리화학적 특성 28개 추출 (순전하, 소수성, 아미노산 조성 등)
3. PCA 기반 데이터 분포 탐색
4. 분류 모델 학습 및 비교 (SVM, Random Forest, Gradient Boosting, Logistic Regression)
5. 최종 모델(SVM)로 후보 서열 예측 및 우선순위화

## 결과

- 학습/평가 데이터를 8:2로 분할하여 평가
- SVM 모델이 평가 데이터 정확도 89.9%로 가장 우수
- 순전하(net charge)가 가장 중요한 판별 인자로 확인됨

| 모델 | 정확도 |
|------|--------|
| SVM | 89.9% |
| Random Forest | 89.4% |
| Gradient Boosting | 87.0% |
| Logistic Regression | 77.8% |

## 실행 방법

```bash
pip install -r requirements.txt
jupyter notebook amp_classification.ipynb
```

## 참고문헌

- Jeon et al. (2023). A peptide encoded by a highly conserved gene belonging to the genus *Streptomyces* shows antimicrobial activity against plant pathogens. *Frontiers in Plant Science*, 14, 1250906.
- Li et al. (2022). AMPlify: attentive deep learning model for discovery of novel antimicrobial peptides. *BMC Genomics*, 23, 77.
