# Skill Creator 비교 점수표

실험 결과를 항목별로 정리하고 비교하기 위한 템플릿입니다.

## 기본 정보

- 실험 날짜:
- Claude creator 실행 환경:
- Codex creator 실행 환경:
- 사용한 모델/세션 정보:
- 점수 체계: `1~5점` / `강함-보통-약함`

## 종합 비교표

| 항목 | Claude skill creator | Codex skill creator | 메모 |
|---|---|---|---|
| 1. 생성 프로세스 |  |  |  |
| 2. 구조 설계 |  |  |  |
| 3. SKILL.md 작성 철학 |  |  |  |
| 4. Context 관리 |  |  |  |
| 5. 테스트/검증 |  |  |  |
| 6. 성능 평가 |  |  |  |
| 7. 성능 최적화 |  |  |  |
| 8. 트리거링 최적화 |  |  |  |
| 9. 자동화/도구 활용 |  |  |  |
| 10. 기존 skill 개선 |  |  |  |

## 상세 기록 템플릿

아래 블록을 항목마다 복제해서 사용합니다.

```text
항목:
프롬프트:

[Claude creator 응답 요약]
- 

[Codex creator 응답 요약]
- 

[비교 관찰]
- 

[세부 점수]
- 구체성:
- 실행 가능성:
- 구조적 완성도:
- 평가 가능성:
- 실무 적용성:
- 도구 활용도:
- 일반화 의식:
- 트리거링 이해도:

[판정]
- Claude 우위 / Codex 우위 / 비슷함
```

## 빠른 체크리스트

각 항목에서 아래를 체크하면 비교가 더 안정적입니다.

- 요구사항을 더 잘 구조화했는가
- 절차가 더 재현 가능했는가
- 본문과 리소스 분리 기준이 더 명확했는가
- 테스트 방법이 더 구체적이었는가
- 정량/정성 평가 설계가 더 실험 가능했는가
- 개선 루프가 더 현실적이었는가
- trigger 최적화에 대한 이해가 더 깊었는가
- 자동화와 검증 도구 활용이 더 체계적이었는가

## 예상되는 패턴

- Claude creator 강점 후보:
  - baseline 비교
  - benchmark/assertion
  - human review loop
  - description optimization

- Codex creator 강점 후보:
  - 간결한 구조 설계
  - context 절약
  - scaffold/init workflow
  - validation 중심의 실무 흐름

## 최종 결론 템플릿

```text
이번 비교에서 Claude creator는 ________ 유형의 작업에서 특히 강했다.
이번 비교에서 Codex creator는 ________ 유형의 작업에서 특히 강했다.

Claude creator를 우선 쓰기 좋은 상황:
- 

Codex creator를 우선 쓰기 좋은 상황:
- 

둘을 함께 쓰면 좋은 방식:
- 
```
