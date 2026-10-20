<div align="center">

<h1>손병훈</h1>

<p>AI Developer</p>

<p><b>현상 뒤에 숨은 진짜 문제를 찾고, AI로 풀어냅니다.</b></p>

[![](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:freaks17489@gmail.com)
[![](https://img.shields.io/badge/Publications-1st--author%204%20%C2%B7%20Co--author%205-1a4d8f?style=for-the-badge&logo=googlescholar&logoColor=white)](#-publications)

</div>

---

## 🧑‍💻 About Me

**처음 받은 문제를 그대로 풀기보다, 왜 그런 문제가 생겼는지 파고듭니다.**

SQL을 몰라 데이터를 직접 조회하지 못하는 현장, 이미 고립된 뒤에는 서비스를 쓰지 않는 청년. 문제를 다시 정의한 과정은 아래 프로젝트와 연구에 적었습니다.

**AI가 낸 결과는 그대로 믿지 않습니다.**

검증 장치를 먼저 붙이고, 그 장치를 얼마나 믿을 수 있는지까지 확인합니다. 연구실에서 AI가 없는 논문을 지어내는 일을 자주 겪은 뒤 인용을 학술 DB 6곳에 대조하는 RealCite를 만들었고, 연구에서는 검증기 자체의 한계를 수치로 쟀습니다.

---

## 🚀 Projects

### Catus: 고립 전 청년을 위한 대화형 감정 기록 서비스
[Live Demo](https://catus-app.vercel.app) · [기획·설계 문서](https://freaks0.github.io/catus/)

마음돌봄 서비스는 힘들어진 사람이 찾아와야 시작되지만, 이미 고립된 청년은 찾아오지 않습니다. 그래서 고립되기 전의 일상에 미리 들어가 있도록 문제를 다시 정의했고, 이 재정의는 통신 메타데이터로 고립 위험을 조기 탐지하는 연구(1저자, 한국통신학회 2026 동계)로 뒷받침했습니다.

- 고양이 "달이"와의 짧은 대화가 그림일기가 되고, 주간 편지와 익명 응원으로 이어지는 가장 가벼운 접점
- AI가 대화에 없던 감정을 일기에 지어내지 못하게 하는 사실 충실성 장치
- 기획, 개발, 배포, 운영 1인 수행. 무료 티어 인프라에서 사용자 테스트 중
- Spring Boot 3 · PostgreSQL · Gemini · React 19

### RealCite: AI 논문 인용 검증 도구
[Live](https://realcite.pages.dev) · [Repo](https://github.com/freaks0/realcite)

AI가 찾아 준 논문 중 일부는 존재하지 않거나 여러 논문이 뒤섞인 것이었고, 틀린 인용 하나 때문에 목록 전체를 다시 의심해야 했습니다. 참고문헌을 통째로 붙여넣으면 Crossref, DataCite, Europe PMC, arXiv, OpenAlex, Semantic Scholar에 대조해 실존 여부와 메타데이터, 철회 여부를 확인합니다.

- 검증기도 틀릴 수 있다는 전제. 소스 장애로 못 찾은 것은 조작 의심이 아니라 확인 불가로 분리
- DOI가 해석돼도 제목, 저자, 연도를 교차 대조해 DOI 도용형 가짜 인용까지 탐지
- 서버 없이 정적 호스팅으로 운영비 0원, 참고문헌은 외부에 저장되지 않음
- TypeScript · React · Cloudflare Pages

### Self-Correcting GraphRAG Agent: 자가수정 루프의 지식그래프 이식
[Repo](https://github.com/freaks0/graphrag-agent)

"검증을 통과했다"가 "맞았다"를 보장하는지 확인하고 싶었습니다. SQL 연구의 자가수정 루프를 지식그래프 질의로 옮겨, 파인튜닝하지 않은 SLM의 한계를 수치로 측정했습니다.

- 검증은 스키마만 보는 결정론적 단계, 교정은 LLM이 맡도록 분리. LLM judge 없이 채점
- 300런 중 13.3%는 답은 맞았지만 경로가 틀림. 검증 통과가 의미적 정답을 보장하지 않음
- 자율 4-hop 계획은 35B 포함 3개 모델 모두 0/11. 구조화된 계획에는 태스크 특화 파인튜닝이 필요
- LangGraph · NetworkX · ollama

---

## 🔬 Research

### Text-to-SQL with a 4B SLM: 산업 시계열 데이터
1저자 · AIDataSci @ KDD 2026 · 한국정보기술학회논문지

SQL을 몰라 데이터를 조회하지 못하는 실무자가 자연어로 약 300만 건의 전력 데이터를 조회하도록, 4B 소형 모델에 자동 검증 루프를 붙였습니다.

- 정답 SQL이 없고 실행은 타임아웃이 잦아, 실행 없이 오류를 잡는 EXPLAIN을 검증기로 선택
- 270M 학습형 검증기가 틀린 SQL의 80%를 통과시키는 것을 확인하고 결정론적 검증 유지
- 형식 준수율 38%에서 90%, 학습에 없던 유형 34%에서 77%, 재시도 호출 20% 감소 (Gemma-3 4B, LoRA)

### Industrial Power Anomaly Detection: 업종 조건화 전략 비교
1저자 · 한국통신학회 2026 하계

"업종 정보를 넣으면 좋아진다"는 통념을 같은 조건 위에서 검증했습니다.

- 라벨 없는 산업 전력 데이터(2,469개 사이트, 5,706만 시간 레코드)에서 업종 정보 주입 방식 5가지를 같은 백본, 같은 손실로 비교
- 이상 유형 4가지를 직접 정의하고 주입해 평가 기준을 만듦
- 구간형 이상에서만 차이(VUS-PR 격차 0.042)가 났고 효과 크기가 작아 잠정 신호로 보고 (NBEATSx, FiLM, Hypernetwork)

---

## 📄 Publications

<!-- TODO: 두 SQL 논문의 게재 상태(accepted/published) 확인 후 링크 추가 -->

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
- **2026.04 - 05** · 미래내일 일경험사업 ABC 프로젝트 멘토링 IT 캠퍼스 · 팀장
- **2025.06** · 새싹창업캠프 해커톤 최우수상 · KOCO (외국인 근로자 AI 동반자, 4인 팀, 기획과 공공 API 조사 담당)
- **2024.06 - 12** · 엘리스 클라우드(자바/스프링) 기반 백엔드 엔지니어 트랙 수료
