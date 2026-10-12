<div align="center">

<h1>손병훈</h1>

<p>AI Developer</p>

<p><b>현상 뒤에 숨은 진짜 문제를 찾고, AI로 풀어냅니다.</b></p>

[![](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:freaks17489@gmail.com)
[![](https://img.shields.io/badge/Publications-1st--author%204%20%C2%B7%20Co--author%205-1a4d8f?style=for-the-badge&logo=googlescholar&logoColor=white)](#-publications)

</div>

---

## 🧑‍💻 About Me

**처음 받은 문제를 그대로 풀기보다, 왜 그런 문제가 생겼는지 파고드는 걸 좋아합니다.**

SQL을 몰라 데이터를 직접 조회하지 못하는 현장, 이미 고립된 뒤에는 서비스를 쓰지 않는 청년처럼, 문제를 다시 정의한 과정은 아래 프로젝트에 적었습니다.

**AI가 낸 결과는 그대로 믿지 않습니다.**

검증 장치를 먼저 붙이고, 그 장치를 얼마나 믿을 수 있는지까지 확인합니다. 학부 연구실에서 AI가 없는 논문을 지어내거나 저자명/제목을 틀리는 일을 자주 겪고 나서, 인용을 학술 DB 6곳에 대조해 검증하는 RealCite를 만들었습니다.

---

## 🚀 Projects

### Catus — AI 고양이와 쓰는 감성 그림일기
> 창업동아리 · 기획 · UI 디자인 · 개발 전담 · Spring Boot · React · Gemini · [Live](https://catus-app.vercel.app) · [Backend](https://github.com/freaks0/catus-backend) · [Frontend](https://github.com/freaks0/catus-frontend)

<!-- TODO: 상태 표기 추가 (예: 창업은 중단 · 데모 운영 중) -->

AI 고양이 달이와 대화하면 밤에 그림일기가 도착하는 청년 정서 지원 서비스입니다.

- 이미 고립된 청년은 찾기 어려워 대상을 **고립 전 청년**으로 재정의하고, 인터뷰로 찾은 "약점을 보이기 싫다"는 이유에서 익명 응원을 핵심 기능으로
- 프롬프트를 규칙 보존 압축(14,043자 → 3,666자)해 응답 속도 6.8s → 1.5s, 월 운영비 0원으로 배포
- 고립 위험군 조기 탐지 연구(논문 1저자): 통신 상대의 다양성을 엔트로피로 정량화한 HA-XGB로 F1 0.89, 고립이 점진적으로 심화된다는 결과로 "고립 전" 방향을 뒷받침

---

### RealCite — AI 논문 인용 검증 도구
> 개인 프로젝트 · TypeScript · Cloudflare Pages · [Live](https://citeguard-bzv.pages.dev) · [Repo](https://github.com/freaks0/realcite)

AI가 찾아준 참고문헌을 학술 DB 6곳에 실시간 대조해 실존 여부, 메타데이터, 철회 여부를 검증합니다.

- DOI가 해석돼도 제목·저자·연도를 교차 대조해 실제 DOI를 도용한 가짜 인용까지 탐지
- 소스 장애로 못 찾으면 조작 의심이 아닌 **판정 보류**로 표시해 검증기 자체의 오판 방지
- 백엔드 없이 정적 호스팅으로 운영비 0원, 참고문헌은 외부 서버에 저장되지 않음

---

### Text-to-SQL with a 4B SLM — 산업 시계열 데이터
> 연구 · 1저자 · AIDataSci @ KDD 2026 · Gemma-3 4B · LoRA · 코드 공개 준비 중

<!-- TODO: 위 메타 줄 끝에 논문 링크 추가 (예: · [Paper](URL)) -->

SQL을 모르는 현장 실무자가 자연어로 약 300만 건의 전력 데이터를 조회하도록, 4B 모델에 자동 검증 루프를 붙였습니다.

- 정답 SQL이 없고 실행은 타임아웃이 잦아, 실행 없이 오류를 잡는 **EXPLAIN을 검증기로** 선택
- 270M 학습형 검증기가 틀린 SQL의 80%를 통과시키는 걸 확인하고 결정론적 검증 유지
- 형식 준수율 38% → 90%, 학습에 없던 유형 34% → 77%, 재시도 호출 −20%(최종 정확도는 동일)

---

### Self-Correcting GraphRAG Agent — 자가수정 루프의 지식그래프 이식
> 개인 프로젝트 · LangGraph · NetworkX · ollama · [Repo](https://github.com/freaks0/graphrag-agent)

SQL 논문의 자가수정 루프를 지식그래프 질의로 옮겨, 파인튜닝하지 않은 SLM의 한계를 측정했습니다.

- 검증은 스키마만 보는 결정론적 단계, 교정은 LLM이 맡도록 분리하고 LLM judge 없이 채점
- 300런 중 **13.3%**는 답은 맞았지만 경로가 틀림 → 검증 통과가 의미적 정답을 보장하지 않음
- 자율 4-hop 계획은 35B 포함 3개 모델 모두 0/11 → 구조화된 계획에는 태스크 특화 파인튜닝이 필요

---

### Industrial Power Anomaly Detection — 업종 조건화 전략 비교
> 연구 · 1저자 · NBEATSx · FiLM · Hypernetwork

라벨 없는 산업 전력 데이터(2,469개 사이트, 5,706만 시간 레코드)에서 업종 정보를 넣는 방식 5가지를 비교했습니다.

- 라벨이 없어 이상 유형 4가지를 직접 정의·주입해 평가 기준을 만듦
- 모든 변형을 같은 백본·같은 손실로 학습해 공정하게 비교
- 구간형 이상에서만 차이(VUS-PR 격차 0.042)가 났고, 효과 크기가 작아 **잠정 신호로 보고**

---

### KOCO — 외국인 근로자 AI 동반자
> 새싹창업캠프 해커톤 최우수상 · 4인 팀 · 하루 만에 기획부터 시연까지

E-9 비자 근로자가 급여·비자·사업장 변경 정보를 이해하기 어렵다는 문제에서 출발한 서비스입니다.

- 제도와 정보가 없는 게 아니라 **언어 장벽 때문에 쓰지 못한다**는 점을 확인
- 문제 리서치와 서비스 기획, 하이코리아·외국인고용서비스 공공 API 조사 담당
- 다국어 상담·급여명세서 분석·비자 알림 프로토타입 구현 (시연은 AI 빌더 도구로 제작)

---

## 📄 Publications

<!-- TODO: 저널 논문 공식 제목 확인 후 레포 README와 통일 / 두 논문의 게재 상태(accepted·published) 확인 -->

**First author**

| Date | Title | Venue |
|---|---|---|
| 2026.08 | Structured EXPLAIN Feedback Improves SQL Generation with a 4B SLM on Industrial Time-Series Data | AIDataSci @ KDD |
| 2026.07 | Improving SQL Generation on Industrial Time-Series Data with Structured EXPLAIN Feedback using a 4B SLM | 한국정보기술학회논문지 |
| 2026.06 | 한국 산업 전력 이상 탐지를 위한 업종 조건화 전략의 예비 비교: 설계 및 예비 분석 | 한국통신학회 하계 |
| 2026.02 | 통신 메타데이터의 엔트로피 분석과 하이브리드 딥러닝 기반 청년 고립 탐지 | 한국통신학회 동계 |

**Co-author**

| Date | Title | Venue |
|---|---|---|
| 2026.08 | LLM Priors for Sample-Efficient Industrial Control in Digital-Twin Simulation | AIDataSci @ KDD |
| 2026.08 | Less Can Be Safer: Tail-Risk Reduction via Capacity-Constrained Policies in Industrial Reinforcement Learning | UDM @ KDD |
| 2026.08 | When Curriculum Becomes Critical: Automated Physics-Grounded Task Progressions for Open Quantum Control | GLOW @ IJCAI |
| 2026.06 | 금속·화학 산업 전력 데이터에서의 Regime 구조 분석과 이상탐지 활용성 평가 | 대한전자공학회 하계 |
| 2026.06 | 물리 제약 기반 Attention-LSTM 오토인코더와 SHAP을 활용한 ESS 배터리 이상탐지 및 원인 해석 | 대한전자공학회 하계 |

---

## 📌 Activities

- **2026.09** · 국제로봇올림피아드 한국대회 본선 · 경기 감독 · 심판 · 기록 총괄
- **2026.04 – 05** · 미래내일 일경험사업 ABC 프로젝트 멘토링 IT 캠퍼스 · 팀장
- **2025.06** · 새싹창업캠프 해커톤 · 최우수상
- **2024.06 – 12** · 엘리스 클라우드(자바/스프링) 기반 백엔드 엔지니어 트랙 수료
