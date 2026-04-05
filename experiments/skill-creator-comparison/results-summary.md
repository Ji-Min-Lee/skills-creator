# Skill Creator 비교 결과 요약

모든 항목은 `fork_context=false`인 새 서브에이전트 스레드에서 독립적으로 실행했다.

비교 대상:
- Claude skill creator: `../../.codex/skills/skill-creator/SKILL.md`
- Codex skill creator: `../../../../.codex/skills/.system/skill-creator/SKILL.md`

## 한눈에 보기

| 항목 | Claude skill creator | Codex skill creator | 우세 |
|---|---|---|---|
| 1. 생성 프로세스 | 테스트와 반복 개선까지 포함한 설계 | 입력/출력 계약과 scaffold 중심 설계 | 비슷함 |
| 2. 구조 설계 | `evals/`, `agents/`, 평가용 리소스까지 적극 포함 | `agents/openai.yaml` 중심, 더 lean한 구조 | 목적 따라 다름 |
| 3. SKILL.md 작성 철학 | why 중심, 과도한 MUST 경계, 예시와 설명 균형 | `description=when`, `body=how`를 매우 선명하게 분리 | Codex 우위 |
| 4. Context 관리 | 분기형 구조를 잘 제안, examples 분리 적극 권장 | conditional loading과 routing 구조를 더 체계적으로 설명 | Codex 우위 |
| 5. 테스트/검증 | 테스트 수, 실패 케이스, 자동/수동 비율까지 제안 | 출력 스키마 고정, 회귀세트 설계, 형식/의미 분리 명확 | Codex 근소 우위 |
| 6. 성능 평가 | baseline, 블라인드 리뷰, 정성+정량 혼합 강함 | 골드셋, precision형 지표, 반복 실행 안정성 강함 | Claude 근소 우위 |
| 7. 성능 최적화 | 사용자 피드백과 로그를 보고 lean하게 줄이는 철학 강함 | 실패 유형 분류와 수술적 구조 개선이 선명함 | 비슷함 |
| 8. 트리거링 최적화 | pushy description, should/should-not 세트, precision/recall 튜닝 강함 | 문서 종류+행동 조합으로 범위를 정밀하게 조정 | Claude 우위 |
| 9. 자동화/도구 활용 | scaffold, eval, benchmark, review, package까지 전체 루프 강함 | init/validate 중심의 안정적 도구 흐름 강함 | Claude 우위 |
| 10. 기존 skill 개선 | baseline을 기존 버전으로 두고 작은 수정 반복 | 호환성 유지, 수술적 수정, 회귀 방지 절차가 선명 | Codex 근소 우위 |

## 항목별 관찰

### 1. Skill 생성 프로세스
- Claude 쪽은 `질문 -> 대표 예시 -> 테스트 -> 반복 개선`의 평가 루프가 강하다.
- Codex 쪽은 `출력 정의 -> 입력 계약 -> 범위/예외 -> 초안 -> 검증`처럼 더 공학적인 단계 분해가 강하다.
- 실험 루프까지 포함해 보고 싶으면 Claude가 더 풍부하다.
- 실제 새 skill을 빠르게 안정적으로 세우려면 Codex 답변이 더 정돈돼 있다.

### 2. 권장 skill 구조
- Claude 쪽은 `SKILL.md + scripts + references + assets + agents + evals`처럼 평가용 구조를 더 적극적으로 포함했다.
- Codex 쪽은 `agents/openai.yaml`을 분명히 넣고, dependency 파일과 메타데이터 관리까지 더 현실적으로 다뤘다.
- 평가/반복 개선까지 한 패키지로 보려면 Claude 구조가 더 풍성하다.
- 배포 가능한 깔끔한 기본 구조는 Codex 쪽이 더 lean하다.

### 3. SKILL.md 작성 철학
- Claude 쪽은 why 설명, 과도한 MUST 지양, 예시 활용, 일반화 강조가 두드러졌다.
- Codex 쪽은 `description에는 언제`, `body에는 어떻게`를 매우 선명하게 구분했다.
- 실전 문서 작성 원칙의 분해력은 Codex 쪽이 더 명확했다.

### 4. Progressive disclosure / context 관리
- 두 creator 모두 `SKILL.md는 얇게`, `references는 상세하게`라는 방향은 같았다.
- Codex 쪽은 conditional loading, 1단계 링크, 공통 파일 분리, provider별 동일 섹션 구조 같은 운영 규칙이 더 체계적이었다.
- Claude 쪽은 examples와 troubleshooting 분리를 잘 제안했지만, Codex가 정보 분할 기준을 더 엄밀하게 설명했다.

### 5. 테스트/검증 방법
- Claude 쪽은 현실적인 테스트 프롬프트 분포와 수동/자동 비율 설계가 좋았다.
- Codex 쪽은 출력 스키마 고정, 템플릿 통일, 형식 검증 vs 의미 검증 분리, 회귀 테스트 세트 확장이 더 명확했다.
- 검증 프레임 자체는 Codex 쪽이 더 공학적으로 강하다.

### 6. 성능 평가 방법
- Claude 쪽은 baseline 비교, 블라인드 리뷰, 정성/정량 혼합, 사용자 피드백 반영 루프가 강점이다.
- Codex 쪽은 골드셋, 자동 채점 지표, 반복 실행 분산 같은 안정성 중심 측정이 강점이다.
- “skill 개선 실험”이라는 맥락에는 Claude 쪽이 더 직접적이다.

### 7. 성능 최적화 방법
- Claude 쪽은 “더 세게 지시하지 말고 더 적게 쓰라”는 lean prompting 철학이 강했다.
- Codex 쪽은 실패를 `트리거/지침/구조`로 나누고, `scripts/references/assets`로 수술적으로 분리하는 기준이 좋았다.
- 두 creator 모두 과적합 방지와 대표/경계 케이스 재검증을 강조했다.

### 8. 트리거링 최적화
- Claude 쪽은 description을 pushy하게 만들고, should-trigger / should-not-trigger 셋과 precision/recall 튜닝까지 적극적으로 제안했다.
- Codex 쪽은 “문서 종류 + 행동” 조합으로 오탐을 줄이는 쪽에 더 강했다.
- 트리거 최적화 전용 방법론은 Claude 쪽이 확실히 더 풍부하다.

### 9. 자동화/도구 활용도
- Claude 쪽은 scaffold 생성부터 eval 실행, grading, benchmark, review viewer, package까지 end-to-end 도구 체인을 상정했다.
- Codex 쪽은 `init_skill.py`, `quick_validate.py`, `openai.yaml` 정합성, smoke test 같은 안정적 기본 흐름에 집중했다.
- 자동화 철학은 Claude가 더 공격적이고, Codex는 더 실무적으로 절제돼 있다.

### 10. 기존 skill 개선 접근
- Claude 쪽은 기존 버전을 baseline으로 두고 실패 패턴 변화 중심으로 보자는 점이 좋았다.
- Codex 쪽은 호환성 유지, 작은 변경 단위, 트리거/본문/테스트 분리 수정, 회귀 시 즉시 원복 같은 안전 장치가 더 선명했다.
- 기존 운영 skill 개선에는 Codex 쪽 절차가 조금 더 안정적이다.

## 종합 결론

### Claude skill creator가 특히 강한 부분
- 평가 루프 설계
- baseline 비교
- human review + benchmark 결합
- trigger optimization
- 반복 개선 실험을 하나의 workflow로 묶는 능력

### Codex skill creator가 특히 강한 부분
- `description`과 `body` 역할 분리
- context 절약과 progressive disclosure
- 구조를 lean하게 유지하는 원칙
- validation/호환성/회귀 방지 중심의 실무 절차
- 기존 skill을 수술적으로 개선하는 방식

### 추천 사용 가이드
- 새 skill을 만들고 실험 루프까지 돌리고 싶다: Claude 쪽이 더 강함
- 문서를 짧고 명확하게 정리하고 구조를 다듬고 싶다: Codex 쪽이 더 강함
- 트리거링 최적화와 benchmark 설계가 중요하다: Claude 쪽 우선
- 운영 중인 skill을 안전하게 리팩터링하고 싶다: Codex 쪽 우선

### 함께 쓰는 최적 조합
1. Codex creator로 초기 구조와 `SKILL.md` 역할 분리를 설계한다.
2. Claude creator로 eval, benchmark, baseline 비교, description optimization을 설계한다.
3. 다시 Codex creator 기준으로 문서를 lean하게 정리하고 validation을 통과시킨다.

## 최종 판정

- **실험 설계와 개선 루프**: Claude skill creator 우세
- **문서 구조와 context discipline**: Codex skill creator 우세
- **운영/유지보수 안정성**: Codex skill creator 근소 우세
- **트리거 최적화와 평가 도구 활용**: Claude skill creator 우세

결론적으로, 둘은 경쟁 관계라기보다 **Claude는 evaluator/optimizer 성향**, **Codex는 architect/refiner 성향**으로 보는 게 가장 정확하다.
