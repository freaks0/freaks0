<div align="center">

<h1>손병훈</h1>

<p>AI Developer · SLM · Text-to-SQL · Time-Series</p>

<p><b>현상 뒤에 숨은 진짜 문제를 찾고, AI로 풀어냅니다.</b></p>

[![](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:freaks17489@gmail.com)
[![](https://img.shields.io/badge/Publications-1st%204%20%C2%B7%20Co%205-1a4d8f?style=for-the-badge&logo=googlescholar&logoColor=white)](#-publications)

</div>

---

## 🧑‍💻 About Me

**눈에 보이는 현상보다, 그 뒤의 진짜 문제를 찾는 걸 좋아합니다.** 청년 고립 서비스를 기획할 때 기사·통계·인터뷰를 파고들어 보니, 이미 고립된 청년은 찾기도 돕기도 어렵고 서비스를 쓰지도 않았습니다. 그래서 대상을 **"고립 전 청년"** 으로 바꿨습니다. 외국인 근로자는 권리가 없는 게 아니라 언어와 정보 장벽 때문에 **권리를 쓰지 못하고** 있었고, 산업 현장의 데이터는 탐지 모델이 부족한 게 아니라 **실무자가 SQL을 몰라 직접 조회하지 못하는** 게 먼저였습니다. 문제를 다시 정의한 뒤에는, AI의 결과를 그대로 믿지 않고 검증할 수 있는 장치부터 붙여서 풉니다.

- 📄 **1저자 논문 4편** — KDD 2026 Workshop(AIDataSci), 한국정보기술학회논문지 등 · 공저 5편
- 🎯 4B 모델 SQL 형식 준수율 **38% → 90%** — LoRA 파인튜닝 + EXPLAIN 자기수정 루프
- 🧭 **라벨도 주제도 없는** 산업 전력 데이터에서 연구 방향과 평가 기준을 직접 설계
- 🏆 새싹창업캠프 해커톤 **최우수상** · 미래내일 일경험 프로젝트 **팀장**
- 🌱 관심 분야: **소형 언어모델 · LLM 결과 검증 · 산업 데이터 AI**

---

## 🛠️ Tech Stack

| **LLM · 학습** | ![](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![](https://img.shields.io/badge/Gemma--3-4285F4?style=flat-square&logo=google&logoColor=white) ![](https://img.shields.io/badge/Qwen--2.5-615CED?style=flat-square&logoColor=white) ![](https://img.shields.io/badge/LoRA-FF6F00?style=flat-square&logoColor=white) |
|---|---|
| **에이전트 · RAG** | ![](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white) ![](https://img.shields.io/badge/LangSmith-1C3C3C?style=flat-square&logo=langchain&logoColor=white) ![](https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama&logoColor=white) ![](https://img.shields.io/badge/NetworkX-2C5BB4?style=flat-square&logoColor=white) |
| **시계열 · ML** | ![](https://img.shields.io/badge/NBEATSx-1a4d8f?style=flat-square&logoColor=white) ![](https://img.shields.io/badge/LSTM--AE-555555?style=flat-square&logoColor=white) ![](https://img.shields.io/badge/XGBoost-189AB4?style=flat-square&logoColor=white) |
| **데이터 · 평가** | ![](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white) ![](https://img.shields.io/badge/McNemar_·_Wilson_CI-6A5ACD?style=flat-square&logoColor=white) |
| **백엔드 · 도구** | ![](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white) ![](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white) ![](https://img.shields.io/badge/Figma-F24E1E?style=flat-square&logo=figma&logoColor=white) |

---

## 🚀 Projects

### 🧠 Text-to-SQL with a 4B SLM — 산업 시계열 데이터
> 연구 · 1저자 · Gemma-3 4B · LoRA · SQLite · 단일 GPU(RTX 5090) · 국가과제 데이터라 코드는 공개 준비 중

보안 때문에 클라우드 AI를 쓸 수 없는 산업 현장에서, SQL을 모르는 실무자가 **자연어로 약 300만 건의 전력 데이터를 조회**하도록 4B 모델에 자동 검증 루프를 붙였습니다.

**핵심 판단**: 정답 SQL이 없고 300만 건 실행은 타임아웃이 잦아, 실행 없이 오류를 잡는 **EXPLAIN을 검증기로** 선택 / 피드백을 "실패만 / 오류 메시지 / 오류+컬럼 목록" 3단계로 나눠 같은 조건에서 비교 / 270M 학습형 검증기가 잘못된 SQL의 80%를 통과시키는 것을 확인하고 **결정론적 검증 유지** / 재시도가 쌓일수록 컨텍스트가 길어져 SQL이 잘리는 실패(잔여 실패의 43%)를 찾아 한계로 보고

**검증**: 형식 준수율 ID **38% → 80% → 90%**, 학습에 없던 유형(OOT) **34% → 77%** / 피드백을 정교하게 줘도 최종 정확도는 86~88%로 같았지만(McNemar p ≥ 0.75) 재시도 호출은 **89 → 71회(−20%)** / Qwen-2.5 3B로 교차 검증

---

### 🕸️ Self-Correcting GraphRAG Agent — 자가수정 루프의 지식그래프 이식
> 개인 프로젝트 · LangGraph · NetworkX · ollama(qwen2.5-coder:7b) · LangSmith · [Repo](https://github.com/freaks0/graphrag-agent)

SQL 논문의 EXPLAIN 자가수정 루프를 지식그래프 질의로 옮겨, 파인튜닝하지 않은 SLM이 어디까지 되고 어디서 무너지는지 측정했습니다.

**핵심 판단**: 멀티홉 질문이 실제로 성립하도록 내 논문 3편의 교차관계(공유 저자·데이터·개념)로 그래프 구성 / 검증은 스키마만 보는 결정론적 단계(5종 에러 + 유효한 대안 피드백), 교정은 LLM이 맡도록 분리 / LLM judge 없이 그래프에서 정답 집합을 뽑아 채점

**결과**: 20문항 × 20회 반복에서 답은 맞았지만 경로가 틀린 경우 **13.3%(40/300)**, 검증 통과가 의미적 정답을 보장하지 않음을 정량화 / base 모델의 자율 4-hop 계획 **0/11**, 피드백 구조는 모델이 태스크를 해낼 능력이 있을 때만 효과가 있고 그 경계가 파인튜닝

---

### 📈 Industrial Power Anomaly Detection — 업종 조건화 전략 비교
> 연구 · 1저자 · NBEATSx · FiLM · Hypernetwork · VUS-PR

라벨이 없는 산업 전력 데이터에서, 업종 정보를 모델에 넣는 방식 5가지가 이상탐지 성능을 어떻게 바꾸는지 비교했습니다.

**핵심 판단**: 라벨이 없어 순간 급증·패턴 이탈·점진적 변화·구간형 이상 **4가지를 직접 정의해 주입**하고 평가 기준을 만듦 / 4,116개 사이트 중 관측률 80% 이상인 **2,469개 사이트, 5,706만 시간 레코드**만 남겨 분석 / 모든 변형을 같은 백본·같은 손실로 학습해 공정하게 비교

**결과**: 구간형 이상에서만 차이(VUS-PR 격차 0.042)가 났고 효과 크기가 작아 **잠정 신호로 보고**

---

### 🌵 Catus — 청년 정서 지원 앱
> 창업동아리 · 기획 · UI 디자인 · 개발 전담 · 배포 전 프로젝트 중단

AI 고양이와의 대화로 그림일기를 만들고, 익명 응원 편지로 선인장을 키우는 청년 정서 지원 앱입니다.

**핵심 판단**: 이미 고립된 청년은 외부에서 찾기 어렵고 서비스도 쓰지 않는다는 점을 기사·통계로 확인 → 대상을 **고립 전 청년**으로 재정의 / 멘토의 "타깃에 기능을 끼워 맞춘 느낌"이라는 피드백 뒤 청년 10명 내외 인터뷰로 "약점을 보이기 싫어 말하지 못한다"는 진짜 이유를 찾아 **익명 응원**을 핵심 기능으로 / 바뀐 방향을 팀이 같이 보도록 기획·기술·개발 명세서를 나눠 작성

---

### 🤝 KOCO — 외국인 근로자 AI 동반자
> 새싹창업캠프 해커톤 **최우수상** · 4인 팀 · 하루 안에 기획부터 시연까지 · 시연은 AI 빌더 도구로 제작

E-9 비자 근로자가 급여·비자·사업장 변경 정보를 이해하기 어렵다는 문제에서 출발한 서비스입니다.

**본인 담당**: 문제 리서치와 서비스 기획 / 하이코리아·외국인고용서비스 공공 API 조사 / 다국어 상담·급여명세서 분석·비자 알림 기능의 프로토타입 구현

---

## 📄 Publications

| Date | Title | Venue | Role |
|---|---|---|---|
| 2026.08 | Structured EXPLAIN Feedback Improves SQL Generation with a 4B SLM on Industrial Time-Series Data | AIDataSci @ KDD | **1st** |
| 2026.07 | Improving SQL Generation on Industrial Time-Series Data with Structured EXPLAIN Feedback using a 4B SLM ([DOI](http://dx.doi.org/10.14801/jkiit.2026.24.7.81)) | 한국정보기술학회논문지 | **1st** |
| 2026.06 | 한국 산업 전력 이상 탐지를 위한 업종 조건화 전략의 예비 비교: 설계 및 예비 분석 | 한국통신학회 하계 | **1st** |
| 2026.02 | 통신 메타데이터의 엔트로피 분석과 하이브리드 딥러닝 기반 청년 고립 탐지 | 한국통신학회 동계 | **1st** |
| 2026.08 | LLM Priors for Sample-Efficient Industrial Control in Digital-Twin Simulation | AIDataSci @ KDD | Co |
| 2026.08 | Less Can Be Safer: Tail-Risk Reduction via Capacity-Constrained Policies in Industrial Reinforcement Learning | UDM @ KDD | Co |
| 2026.08 | When Curriculum Becomes Critical: Automated Physics-Grounded Task Progressions for Open Quantum Control | GLOW @ IJCAI | Co |
| 2026.06 | 금속·화학 산업 전력 데이터에서의 Regime 구조 분석과 이상탐지 활용성 평가 | 대한전자공학회 하계 | Co |
| 2026.06 | 물리 제약 기반 Attention-LSTM 오토인코더와 SHAP을 활용한 ESS 배터리 이상탐지 및 원인 해석 | 대한전자공학회 하계 | Co |

---

## 📌 Activities

- **2026.04 – 05** · 미래내일 일경험사업 ABC 프로젝트 멘토링 IT 캠퍼스 · 팀장
- **2026.09** · 국제로봇올림피아드 한국대회 본선 · 경기 감독 · 심판 · 기록 총괄
- **2025.06** · 새싹창업캠프 해커톤 · 최우수상
- **2024<div align="center">

<h1>손병훈</h1>

<p>AI Developer · SLM · Text-to-SQL · Time-Series</p>

<p><b>현상 뒤에 숨은 진짜 문제를 찾고, AI로 풀어냅니다.</b></p>

[![](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:freaks17489@gmail.com)
[![](https://img.shields.io/badge/Publications-1st%204%20%C2%B7%20Co%205-1a4d8f?style=for-the-badge&logo=googlescholar&logoColor=white)](#-publications)

</div>

---

## 🧑‍💻 About Me

**눈에 보이는 현상보다, 그 뒤의 진짜 문제를 찾는 걸 좋아합니다.** 청년 고립 서비스를 기획할 때 기사·통계·인터뷰를 파고들어 보니, 이미 고립된 청년은 찾기도 돕기도 어렵고 서비스를 쓰지도 않았습니다. 그래서 대상을 **"고립 전 청년"** 으로 바꿨습니다. 외국인 근로자는 권리가 없는 게 아니라 언어와 정보 장벽 때문에 **권리를 쓰지 못하고** 있었고, 산업 현장의 데이터는 탐지 모델이 부족한 게 아니라 **실무자가 SQL을 몰라 직접 조회하지 못하는** 게 먼저였습니다. 문제를 다시 정의한 뒤에는, AI의 결과를 그대로 믿지 않고 검증할 수 있는 장치부터 붙여서 풉니다.

- 📄 **1저자 논문 4편** — KDD 2026 Workshop(AIDataSci), 한국정보기술학회논문지 등 · 공저 5편
- 🎯 4B 모델 SQL 형식 준수율 **38% → 90%** — LoRA 파인튜닝 + EXPLAIN 자기수정 루프
- 🧭 **라벨도 주제도 없는** 산업 전력 데이터에서 연구 방향과 평가 기준을 직접 설계
- 🏆 새싹창업캠프 해커톤 **최우수상** · 미래내일 일경험 프로젝트 **팀장**
- 🌱 관심 분야: **소형 언어모델 · LLM 결과 검증 · 산업 데이터 AI**

---

## 🛠️ Tech Stack

| **LLM · 학습** | ![](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![](https://img.shields.io/badge/Gemma--3-4285F4?style=flat-square&logo=google&logoColor=white) ![](https://img.shields.io/badge/Qwen--2.5-615CED?style=flat-square&logoColor=white) ![](https://img.shields.io/badge/LoRA-FF6F00?style=flat-square&logoColor=white) |
|---|---|
| **에이전트 · RAG** | ![](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white) ![](https://img.shields.io/badge/LangSmith-1C3C3C?style=flat-square&logo=langchain&logoColor=white) ![](https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama&logoColor=white) ![](https://img.shields.io/badge/NetworkX-2C5BB4?style=flat-square&logoColor=white) |
| **시계열 · ML** | ![](https://img.shields.io/badge/NBEATSx-1a4d8f?style=flat-square&logoColor=white) ![](https://img.shields.io/badge/LSTM--AE-555555?style=flat-square&logoColor=white) ![](https://img.shields.io/badge/XGBoost-189AB4?style=flat-square&logoColor=white) |
| **데이터 · 평가** | ![](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white) ![](https://img.shields.io/badge/McNemar_·_Wilson_CI-6A5ACD?style=flat-square&logoColor=white) |
| **백엔드 · 도구** | ![](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white) ![](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white) ![](https://img.shields.io/badge/Figma-F24E1E?style=flat-square&logo=figma&logoColor=white) |

---

## 🚀 Projects

### 🧠 Text-to-SQL with a 4B SLM — 산업 시계열 데이터
> 연구 · 1저자 · Gemma-3 4B · LoRA · SQLite · 단일 GPU(RTX 5090) · 국가과제 데이터라 코드는 공개 준비 중

보안 때문에 클라우드 AI를 쓸 수 없는 산업 현장에서, SQL을 모르는 실무자가 **자연어로 약 300만 건의 전력 데이터를 조회**하도록 4B 모델에 자동 검증 루프를 붙였습니다.

**핵심 판단**: 정답 SQL이 없고 300만 건 실행은 타임아웃이 잦아, 실행 없이 오류를 잡는 **EXPLAIN을 검증기로** 선택 / 피드백을 "실패만 / 오류 메시지 / 오류+컬럼 목록" 3단계로 나눠 같은 조건에서 비교 / 270M 학습형 검증기가 잘못된 SQL의 80%를 통과시키는 것을 확인하고 **결정론적 검증 유지** / 재시도가 쌓일수록 컨텍스트가 길어져 SQL이 잘리는 실패(잔여 실패의 43%)를 찾아 한계로 보고

**검증**: 형식 준수율 ID **38% → 80% → 90%**, 학습에 없던 유형(OOT) **34% → 77%** / 피드백을 정교하게 줘도 최종 정확도는 86~88%로 같았지만(McNemar p ≥ 0.75) 재시도 호출은 **89 → 71회(−20%)** / Qwen-2.5 3B로 교차 검증

---

### 🕸️ Self-Correcting GraphRAG Agent — 자가수정 루프의 지식그래프 이식
> 개인 프로젝트 · LangGraph · NetworkX · ollama(qwen2.5-coder:7b) · LangSmith · [Repo](https://github.com/freaks0/graphrag-agent)

SQL 논문의 EXPLAIN 자가수정 루프를 지식그래프 질의로 옮겨, 파인튜닝하지 않은 SLM이 어디까지 되고 어디서 무너지는지 측정했습니다.

**핵심 판단**: 멀티홉 질문이 실제로 성립하도록 내 논문 3편의 교차관계(공유 저자·데이터·개념)로 그래프 구성 / 검증은 스키마만 보는 결정론적 단계(5종 에러 + 유효한 대안 피드백), 교정은 LLM이 맡도록 분리 / LLM judge 없이 그래프에서 정답 집합을 뽑아 채점

**결과**: 20문항 × 20회 반복에서 답은 맞았지만 경로가 틀린 경우 **13.3%(40/300)**, 검증 통과가 의미적 정답을 보장하지 않음을 정량화 / base 모델의 자율 4-hop 계획 **0/11**, 피드백 구조는 모델이 태스크를 해낼 능력이 있을 때만 효과가 있고 그 경계가 파인튜닝

---

### 📈 Industrial Power Anomaly Detection — 업종 조건화 전략 비교
> 연구 · 1저자 · NBEATSx · FiLM · Hypernetwork · VUS-PR

라벨이 없는 산업 전력 데이터에서, 업종 정보를 모델에 넣는 방식 5가지가 이상탐지 성능을 어떻게 바꾸는지 비교했습니다.

**핵심 판단**: 라벨이 없어 순간 급증·패턴 이탈·점진적 변화·구간형 이상 **4가지를 직접 정의해 주입**하고 평가 기준을 만듦 / 4,116개 사이트 중 관측률 80% 이상인 **2,469개 사이트, 5,706만 시간 레코드**만 남겨 분석 / 모든 변형을 같은 백본·같은 손실로 학습해 공정하게 비교

**결과**: 구간형 이상에서만 차이(VUS-PR 격차 0.042)가 났고 효과 크기가 작아 **잠정 신호로 보고**

---

### 🌵 Catus — 청년 정서 지원 앱
> 창업동아리 · 기획 · UI 디자인 · 개발 전담 · 배포 전 프로젝트 중단

AI 고양이와의 대화로 그림일기를 만들고, 익명 응원 편지로 선인장을 키우는 청년 정서 지원 앱입니다.

**핵심 판단**: 이미 고립된 청년은 외부에서 찾기 어렵고 서비스도 쓰지 않는다는 점을 기사·통계로 확인 → 대상을 **고립 전 청년**으로 재정의 / 멘토의 "타깃에 기능을 끼워 맞춘 느낌"이라는 피드백 뒤 청년 10명 내외 인터뷰로 "약점을 보이기 싫어 말하지 못한다"는 진짜 이유를 찾아 **익명 응원**을 핵심 기능으로 / 바뀐 방향을 팀이 같이 보도록 기획·기술·개발 명세서를 나눠 작성

---

### 🤝 KOCO — 외국인 근로자 AI 동반자
> 새싹창업캠프 해커톤 **최우수상** · 4인 팀 · 하루 안에 기획부터 시연까지 · 시연은 AI 빌더 도구로 제작

E-9 비자 근로자가 급여·비자·사업장 변경 정보를 이해하기 어렵다는 문제에서 출발한 서비스입니다.

**본인 담당**: 문제 리서치와 서비스 기획 / 하이코리아·외국인고용서비스 공공 API 조사 / 다국어 상담·급여명세서 분석·비자 알림 기능의 프로토타입 구현

---

## 📄 Publications

| Date | Title | Venue | Role |
|---|---|---|---|
| 2026.08 | Structured EXPLAIN Feedback Improves SQL Generation with a 4B SLM on Industrial Time-Series Data | AIDataSci @ KDD | **1st** |
| 2026.07 | Improving SQL Generation on Industrial Time-Series Data with Structured EXPLAIN Feedback using a 4B SLM | 한국정보기술학회논문지 | **1st** |
| 2026.06 | 한국 산업 전력 이상 탐지를 위한 업종 조건화 전략의 예비 비교: 설계 및 예비 분석 | 한국통신학회 하계 | **1st** |
| 2026.02 | 통신 메타데이터의 엔트로피 분석과 하이브리드 딥러닝 기반 청년 고립 탐지 | 한국통신학회 동계 | **1st** |
| 2026.08 | LLM Priors for Sample-Efficient Industrial Control in Digital-Twin Simulation | AIDataSci @ KDD | Co |
| 2026.08 | Less Can Be Safer: Tail-Risk Reduction via Capacity-Constrained Policies in Industrial Reinforcement Learning | UDM @ KDD | Co |
| 2026.08 | When Curriculum Becomes Critical: Automated Physics-Grounded Task Progressions for Open Quantum Control | GLOW @ IJCAI | Co |
| 2026.06 | 금속·화학 산업 전력 데이터에서의 Regime 구조 분석과 이상탐지 활용성 평가 | 대한전자공학회 하계 | Co |
| 2026.06 | 물리 제약 기반 Attention-LSTM 오토인코더와 SHAP을 활용한 ESS 배터리 이상탐지 및 원인 해석 | 대한전자공학회 하계 | Co |

---

## 📌 Activities

- **2026.09** · 국제로봇올림피아드 한국대회 본선 · 경기 감독 · 심판 · 기록 총괄
- **2026.04 – 05** · 미래내일 일경험사업 ABC 프로젝트 멘토링 IT 캠퍼스 · 팀장
- **2025.06** · 새싹창업캠프 해커톤 · 최우수상
- **2024.06 - 12** · 엘리스 클라우드(자바/스프링) 기반 백엔드 엔지니어 트랙 수료
