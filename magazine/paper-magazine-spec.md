# Paper Magazine Specification

> 논문 1편의 PDF만 입력받아 신문 스타일 매거진을 생성하는 구성안
> 참조: digbro.vercel.app/v2 (연구자 포트폴리오 브로셔)

---

## 입력

- 논문 PDF 1건 (외부 API 없이 PDF 텍스트 + LLM 분석만으로 구성)

---

## PDF에서 추출 가능한 정보

| 정보 | 방법 |
|------|------|
| 제목, 저자, 소속, 저널명, 연도 | PDF 텍스트 파싱 |
| Abstract, 키워드 | 텍스트 추출 |
| 연구 배경·목적·방법·결과·결론 | LLM 분석 |
| 연구 유형 분류 (실험/리뷰/시뮬레이션 등) | LLM 분류 |
| 핵심 발견 (Key Findings) | LLM 요약 |
| 강점 & 한계점 | LLM 분석 |
| 실용적 시사점 | LLM 생성 |
| 후속 연구 방향 제안 | LLM 생성 |
| 연구 키워드 | 본문 빈도 + LLM 추출 |
| 참고문헌 목록 (이 논문이 인용한 것) | References 섹션 파싱 |
| 분야 분류 비중 | LLM 판단 |

## PDF만으로는 불가능한 정보

| 정보 | 이유 |
|------|------|
| 피인용 수 | 외부 DB(OpenAlex 등)에만 존재 |
| Journal IF | Clarivate 데이터 |
| FWCI | Scopus/SciVal 산출 |
| Altmetric Score | 외부 서비스 |
| 피인용 추이 차트 | 시계열 데이터 필요 |
| 이 논문을 인용한 후속 논문 | 외부 DB 필요 |
| 분야 내 상위 % | 비교 데이터 필요 |

---

## 매거진 레이아웃 구성

### Page 1 — 논문 프로필

#### Masthead
- "THE RESEARCH DAILY" 동일 스타일
- 날짜, 서브타이틀: `PAPER ANALYSIS · KEY FINDINGS · RESEARCH OUTLOOK`

#### 논문 메타정보
- 논문 제목 (대형 헤드라인)
- 저자 · 소속기관 · 저널명 · 출판연도

#### 핵심 지표 카드 (4칸 가로 배치)

| 카드 | 설명 |
|------|------|
| 참고문헌 수 | References 섹션에서 파싱 |
| 페이지 수 | PDF 메타데이터 |
| Figure/Table 수 | 본문 파싱 |
| 연구 유형 | LLM 분류 (실험/리뷰/시뮬레이션/이론 등) |

#### AI 핵심 요약
- LLM이 생성한 논문 핵심 메시지 1-2문장

#### 연구 유형 분류
- 아이콘 + 유형명 + 설명
- 예: 실험연구 — 실제 실험 데이터 기반 정량적 분석을 수행한 연구

#### 연구 분야 비중
- 논문이 걸쳐있는 학제 분류 가로 바차트
- 예: Energy 60%, Materials 25%, Environment 15%
- LLM이 본문 내용 기반으로 판단

#### 논문 구조 개요 (Key Metrics 자리 대체)

| 좌측: Paper Structure | 우측: Research Scope |
|----------------------|---------------------|
| 연구 배경 | 연구 대상/재료 |
| 연구 목적 | 분석 기법 |
| 핵심 방법론 | 데이터 규모 |
| 주요 결과 | 적용 범위 |
| 결론 | 한계점 요약 |

#### 연구 구조 다이어그램
- 배경 → 가설/목적 → 방법 → 결과 → 결론 5단계 플로우
- 기존 Publication & Citation Trends 차트 자리에 배치

---

### Page 2 — 심층 분석

#### Key Findings (핵심 발견)
- 3-5개 bullet point
- 각 항목에 논문 내 데이터 수치 포함
- 예: "바이오디젤 수율 94.2% 달성 (기존 대비 12% 향상)"

#### 방법론 평가
- 실험 설계 요약
- 사용된 데이터/재료
- 분석 기법 정리

#### 참고문헌 분석 (Collaboration & Journals 자리 대체)

| 좌측: 선행연구 분석 | 우측: 주요 참고문헌 Top 5 |
|-------------------|------------------------|
| 참고문헌 연도 분포 차트 | 1. 논문 제목 · 저널 · 연도 |
| 자기인용 비율 | 2. 논문 제목 · 저널 · 연도 |
| 분야별 분포 파이차트 | 3. 논문 제목 · 저널 · 연도 |
| | 4. 논문 제목 · 저널 · 연도 |
| | 5. 논문 제목 · 저널 · 연도 |

#### 논문 품질 평가 (Portfolio Concentration Risk 자리 대체)

| 항목 | 시각화 | 판정 |
|------|--------|------|
| 방법론 견고성 | ████████░░ | 높음 |
| 데이터 충분성 | ██████░░░░ | 보통 |
| 재현가능성 | ████████░░ | 높음 |
| 참신성 | ██████████ | 매우 높음 |

#### Strengths & Limitations (Portfolio Strengths & Opportunities 자리)

| 좌: 강점 (Strengths) | 우: 한계점 (Limitations) |
|---------------------|----------------------|
| - 방법론 참신성 | - 샘플 크기 제한 |
| - 데이터 규모 | - 일반화 한계 |
| - 실용적 적용 가능성 | - 장기 검증 부재 |
| - 선행연구 대비 개선점 | - 비용 분석 미포함 |

#### 실용적 시사점 (Strategic Directions 자리)

| 산업계 적용 | 정책적 시사점 | 학술적 기여 |
|-----------|------------|-----------|
| 구체적 활용 방안 | 관련 정책 제안 | 이론적 기여점 |

#### 후속 연구 로드맵 (Research Roadmap 자리)

| 시나리오 A | 시나리오 B | 시나리오 C |
|-----------|-----------|-----------|
| 심화 연구 | 응용 확장 | 학제간 융합 |
| 동일 주제 깊이 확장 | 다른 분야/재료 적용 | 타 분야와 결합 연구 |

---

### Page 3 — 키워드 & 전망

#### Research Keywords
- 논문 키워드를 워드클라우드 스타일로 배치
- 빈도·중요도에 따라 크기 차등
- Author Keywords + LLM 추출 키워드 통합

#### 관련 논문 Top 5 (Highly Cited Papers 자리 대체)
- 논문이 인용한 참고문헌 중 가장 핵심적인 5편 선별
- LLM이 본문 인용 맥락을 분석하여 중요도 판단

| # | 논문 제목 | 인용 맥락 |
|---|---------|---------|
| 1 | 제목 · 저널 · 연도 | 방법론 차용 |
| 2 | 제목 · 저널 · 연도 | 비교 대상 |
| 3 | 제목 · 저널 · 연도 | 이론적 기반 |
| 4 | 제목 · 저널 · 연도 | 데이터 참조 |
| 5 | 제목 · 저널 · 연도 | 선행 결과 확장 |

#### AI 종합 평가 (Comprehensive Outlook 자리)
- 학술적 기여도
- 연구의 참신성
- 재현가능성
- 후속 연구 잠재력
- 종합 1-2문단 서술

#### Footer
- BIBLO Research Analytics · 소속 대학 · 생성일 · FOR RESEARCH PLANNING PURPOSES

---

## 기존 브로셔와의 매핑 관계

```
연구자 포트폴리오 버전          →    논문 1편 버전
─────────────────────────────────────────────────
Total Publications (119)       →    참고문헌 수
H-index (36)                   →    페이지 수
Total Citations (3,968)        →    Figure/Table 수
Avg. IF                        →    연구 유형
Portfolio Allocation           →    연구 분야 비중 (LLM 판단)
Researcher Profile Type        →    연구 유형 분류
Key Metrics                    →    논문 구조 개요
Growth Indicators              →    Research Scope
Publication Trends             →    연구 구조 다이어그램
Collaboration 파이차트          →    참고문헌 분석 (연도/분야 분포)
Top Journals                   →    주요 참고문헌 Top 5
Portfolio Concentration Risk   →    논문 품질 평가
Strengths & Opportunities      →    Strengths & Limitations
Strategic Directions           →    실용적 시사점
Research Roadmap               →    후속 연구 로드맵 (시나리오 A·B·C)
Research Keywords              →    Research Keywords (그대로 유지)
Highly Cited Papers            →    관련 논문 Top 5 (인용한 핵심 논문)
Comprehensive Outlook          →    AI 종합 평가
```

---

## 기술 구현 방향

1. **입력**: 논문 PDF 업로드
2. **파싱**: PDF 텍스트 추출 (pdf-parse 등)
3. **분석**: LLM에 전문 전달 → 구조화된 JSON 응답 생성
4. **렌더링**: 신문 스타일 레이아웃에 데이터 바인딩
5. **출력**: 웹 뷰 + PDF 다운로드
