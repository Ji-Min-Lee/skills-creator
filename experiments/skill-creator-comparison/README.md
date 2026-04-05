# Skill Creator 비교 실험

Claude용 `skill-creator`와 Codex용 `skill-creator`를 같은 프롬프트로 비교하기 위한 실험 패키지입니다.

## 목적

- 두 creator의 강점이 어디에 있는지 구조적으로 비교
- 같은 입력에 대해 어떤 종류의 방법론을 더 잘 제시하는지 관찰
- 결과를 재현 가능하게 기록

## 비교 대상

- Claude skill creator: `C:\Users\user\workspace\create-skills\.codex\skills\skill-creator\SKILL.md`
- Codex skill creator: `C:\Users\user\.codex\skills\.system\skill-creator\SKILL.md`

## 구성

- [prompts.md](/C:/Users/user/workspace/create-skills/experiments/skill-creator-comparison/prompts.md): 항목별 동일 비교 프롬프트
- [scorecard.md](/C:/Users/user/workspace/create-skills/experiments/skill-creator-comparison/scorecard.md): 결과 기록 및 채점 시트

## 실행 방법

1. `prompts.md`에서 한 항목의 프롬프트를 복사합니다.
2. 같은 프롬프트를 Claude creator와 Codex creator에 각각 입력합니다.
3. 두 응답을 `scorecard.md`에 붙여 넣거나 요약합니다.
4. 항목별로 점수와 메모를 기록합니다.
5. 10개 항목을 모두 수행한 뒤 종합 관찰을 작성합니다.

## 권장 채점 기준

- `구체성`: 실제로 따라 할 수 있을 정도로 단계가 명확한가
- `실행 가능성`: 바로 실험/구현/검증에 옮길 수 있는가
- `구조적 완성도`: 앞뒤 흐름과 구성 원칙이 잘 연결되는가
- `평가 가능성`: 결과를 검증하거나 비교할 수 있게 설계하는가
- `실무 적용성`: 실제 skill 제작 업무에 곧바로 도움이 되는가
- `도구 활용도`: 스크립트, 자동화, 검증 도구 활용이 좋은가
- `일반화 의식`: 특정 예시를 넘어 재사용성/과적합 방지를 고려하는가
- `트리거링 이해도`: skill description과 호출 조건을 얼마나 잘 다루는가

점수는 `1~5점` 또는 `강함/보통/약함` 중 하나로 통일해서 쓰면 됩니다.

## 관찰 포인트

- Claude creator는 평가 루프, baseline, benchmark, feedback 반영에서 강할 가능성이 큽니다.
- Codex creator는 구조 설계, context 절약, scaffold/validate 흐름에서 강할 가능성이 큽니다.
- 같은 프롬프트라도 Claude는 실험 중심, Codex는 설계 원칙 중심으로 답할 수 있습니다.
- 특히 `성능 평가`, `반복 개선`, `description optimization` 항목에서 차이가 크게 드러날 수 있습니다.

## 실험 운영 팁

- 각 creator의 답변 길이가 너무 다르면, 길이보다 정보 밀도와 실행 가능성을 우선 봅니다.
- “무엇을 해야 하는지”뿐 아니라 “왜 그렇게 해야 하는지” 설명 수준도 함께 비교합니다.
- 단순히 더 많은 항목을 나열한 쪽보다, 더 재현 가능하고 판별 가능한 워크플로우를 준 쪽을 높게 평가합니다.
