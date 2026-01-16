# Semantic Equity Research + InfraNodus 통합 분석

## 개요

`/semantic-research` 분석의 Event Ontology를 **자동으로 InfraNodus 지식그래프로 변환**하는 통합 워크플로우입니다.

**트리거**: `semantic-infra:`, `시맨틱-인프라:`, `/semantic-research-infranodus`

---

## 언어 및 번역 설정

### 분석 → 번역 워크플로우
```
┌─────────────────────────────────────────────────────────────┐
│  1. 분석 수행: 항상 영어(English)로 실행                       │
│     - WebSearch, 데이터 수집, 분석 모두 영어 기반             │
│     - 정확성과 데이터 품질 보장                               │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  2. 최종 번역: 사용자 지정 언어로 번역하여 제출                 │
│     - 기본값: 한국어 (Korean)                                │
│     - 옵션: 영어, 일본어, 중국어 등                           │
└─────────────────────────────────────────────────────────────┘
```

### 언어 옵션
| 옵션 | 출력 언어 | 사용 예시 |
|------|----------|----------|
| 미지정 (기본) | 한국어 | `semantic-infra: AAPL` |
| `--lang=ko` | 한국어 | `semantic-infra: AAPL --lang=ko` |
| `--lang=en` | English | `semantic-infra: AAPL --lang=en` |
| `--lang=ja` | 日本語 | `semantic-infra: AAPL --lang=ja` |
| `--lang=zh` | 中文 | `semantic-infra: AAPL --lang=zh` |

### 핵심 원칙
> **분석은 영어로, 리포트는 사용자 언어로**
> - 영어 소스 데이터의 정확성 유지
> - 최종 단계에서 고품질 번역 적용
> - 전문 용어는 원어 병기 (예: 밸류에이션(Valuation))

---

## 저장 폴더 설정

### 최초 실행 시 폴더 지정
첫 실행 시 저장 폴더를 질문합니다:

```
📁 리포트 저장 폴더를 지정해주세요:
1. /Users/moon/LearningMaster/400-Personal/430-Goals (기본 투자분석 폴더)
2. 직접 입력
```

### 폴더 기억 (Session Persistence)
- **1회 지정 후 자동 저장**: 한 번 폴더를 지정하면 세션 내에서 동일 폴더에 자동 저장
- **변경 시**: `--folder` 옵션으로 새 폴더 지정 가능
  ```
  semantic-infra: NVDA --folder=/새로운/경로
  ```

### 저장 구조
```
[지정된 폴더]/
├── [티커]_투자분석_YYYY-MM-DD.md          # 메인 리포트
└── [티커]_투자온톨로지_YYYY-MM-DD.md      # Event Ontology (선택적)
```

---

## 통합 워크플로우

### Phase 1: Semantic Equity Research 실행 (영어)
1. `/semantic-research [티커]` 명령어로 11개 섹션 분석 수행 (영어)
2. **Event Ontology (섹션 9)** 추출

### Phase 2: InfraNodus 자동 연동
Event Ontology 텍스트를 InfraNodus MCP로 전송:

```yaml
실행_순서:
  1. 지식그래프 생성:
     tool: mcp__infranodus__create_knowledge_graph
     params:
       graphName: "[티커]-investment-analysis-YYYY-MM-DD"
       text: "[Event Ontology 전체 텍스트]"
       modifyAnalyzedText: "none"

  2. 콘텐츠 갭 분석:
     tool: mcp__infranodus__generate_content_gaps
     params:
       text: "[Event Ontology 전체 텍스트]"

  3. 연구 질문 생성:
     tool: mcp__infranodus__generate_research_questions
     params:
       text: "[Event Ontology 전체 텍스트]"
       modelToUse: "gpt-4o"
       gapDepth: 2
```

### Phase 3: 번역 및 리포트 생성
1. 영어 분석 결과를 사용자 지정 언어로 번역
2. InfraNodus 분석 결과 추가
3. 지정된 폴더에 자동 저장

---

## 출력 형식

### 추가되는 섹션: 12. 🕸️ INFRANODUS 시각화

```markdown
### 12. 🕸️ INFRANODUS 시각화

#### 인터랙티브 지식그래프
> **[👉 InfraNodus에서 투자 관계 네트워크 보기](https://infranodus.com/[username]/[ticker]-investment-analysis-YYYY-MM-DD/edit)**

#### 발견된 콘텐츠 갭 (투자 블라인드 스팟)
| Gap # | 연결 약한 영역 | 투자 의미 |
|-------|---------------|----------|
| 1 | [클러스터 A] ↔ [클러스터 B] | [해석] |
| 2 | [클러스터 C] ↔ [클러스터 D] | [해석] |

#### AI 생성 연구 질문
1. [갭 기반 질문 1]
2. [갭 기반 질문 2]
3. [갭 기반 질문 3]

#### 네트워크 통계
- 총 노드 수: XX개
- 총 관계 수: XX개
- 클러스터 수: X개
- 네트워크 밀도: X.XX
```

---

## 사용법

### 기본 사용 (한국어 리포트)
```
semantic-infra: AAPL
```

### 영어 리포트
```
semantic-infra: AAPL --lang=en
```

### 일본어 리포트
```
semantic-infra: TSLA --lang=ja
```

### 중국어 리포트
```
semantic-infra: MSFT --lang=zh
```

### 상세 분석 + 언어 지정
```
semantic-infra: NVDA --detailed --lang=en
```

### 저장 폴더 변경
```
semantic-infra: PLTR --folder=/Users/moon/Documents/Investment
```

### 한국 주식
```
semantic-infra: 005930.KS
```

---

## Event Ontology → InfraNodus 변환 규칙

### 관계 코드 매핑
| Event Ontology | InfraNodus 해석 |
|---------------|-----------------|
| `[enables]` | 긍정적 인과 관계 |
| `[threatens]` | 부정적 리스크 연결 |
| `[dependentOn]` | 의존성 화살표 |
| `[supports]` | 지지 관계 |
| `[opposes]` | 대립 관계 |
| `[correlatesWith]` | 상관 관계 |
| `[amplifies]` | 강화 관계 |
| `[mitigates]` | 완화 관계 |

### [[Wikilink]] 변환
```
# Event Ontology 원본
[[AIP Commercial Adoption]] enables [[Customer Count Growth]] [enables]

# InfraNodus 입력 형식 (자동 변환)
AIP Commercial Adoption enables Customer Count Growth
```

---

## 워크플로우 다이어그램

```
┌─────────────────────────────────────────────────────────────────┐
│                    /semantic-infra: PLTR                        │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│  Phase 1: Semantic Equity Research (영어로 분석)                │
│  ├─ WebSearch: 영어 데이터 수집                                  │
│  ├─ 섹션 1-8: 핵심 분석 (영어)                                   │
│  └─ 섹션 9-11: 시맨틱 강화 (Event Ontology 생성)                │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼ Event Ontology 추출
┌─────────────────────────────────────────────────────────────────┐
│  Phase 2: InfraNodus MCP 자동 연동                              │
│  ├─ mcp__infranodus__create_knowledge_graph                    │
│  │   └─ 영구 저장 그래프 생성 + URL                              │
│  ├─ mcp__infranodus__generate_content_gaps                     │
│  │   └─ 투자 블라인드 스팟 발견                                   │
│  └─ mcp__infranodus__generate_research_questions               │
│      └─ 추가 연구 영역 제안                                       │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│  Phase 3: 번역 및 리포트 생성                                    │
│  ├─ 영어 분석 → 사용자 언어 번역 (기본: 한국어)                   │
│  ├─ 섹션 12 추가: InfraNodus 시각화                              │
│  └─ 지정된 폴더에 자동 저장                                       │
└─────────────────────────────────────────────────────────────────┘
```

---

## 주의사항

1. **Claude Code 재시작 필요**: InfraNodus MCP 서버 설정 후 Claude Code를 재시작해야 `mcp__infranodus__*` 도구가 활성화됩니다.

2. **API 사용량**: InfraNodus API 호출 횟수에 따라 요금이 발생할 수 있습니다.

3. **그래프 이름 규칙**: 소문자, 대시(-) 사용, 특수문자 금지
   - Good: `pltr-investment-analysis-2026-01-17`
   - Bad: `PLTR_Investment_Analysis`

4. **번역 품질**: 전문 금융 용어는 원어 병기로 정확성 유지

---

## 버전 정보

- **버전**: 1.1.0
- **업데이트**: 2026-01-17
- **변경사항**:
  - 영어 분석 → 다국어 번역 워크플로우 추가
  - 저장 폴더 1회 지정 후 자동 저장 기능
  - 언어 옵션 추가 (ko, en, ja, zh)
- **의존성**:
  - semantic-equity-research 스킬
  - InfraNodus MCP 서버 (`infranodus-mcp-server`)
  - InfraNodus API 키
