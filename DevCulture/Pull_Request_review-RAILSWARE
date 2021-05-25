# Pull Reqeust Review - RAILSWARE

Created: May 25, 2021 11:53 AM
Tags: CodeReview, DevCulture

## Pull Request?

- `Github` 저장소에서 특정 코드의 검토 절차의 요청
- 동료에게 특정 코드의 변경 사항이 적용 가능한지 확인하도록 요청

## Why are pull requests useful?

### 업무 분리 및 Conflict 해결

- 팀이 커지면 충돌을 피하기 위해 엔지니어들의 작업을 별도로 유지하는 것이 좋음
- 하나의 파일에서 생기는 `Conflict`를 해결
- 필요에 따라 `Merge tool`을 사용하여 `Confilct`를 해결할 수 있음

### 코드 품질 및 응집력 향상

- `author bias(저자 편향)` : 코드를 만든 자는 코드를 항상 이해하기 쉽다고 생각한다
- 누구나 다른 관점을 가지고 있기 때문에 누군가는 코드를 이해하지 못할 수 있음
- 버그, 오류 뿐만이 아닌 일반적으로 합의된 관행, 어휘, 다른 코드와의 불일치 등을 발견할 수 있음
- 모호한 용어를 피하고 동의어 대신 용어 하나를 선택하는 것이 중요
- 두 개의 다른 팀의 서로의 개별 플랫폼에서 하나의 제품을 만드는 경우 (ex : IOS/Android)
    - 서로의 코드 일부를 재사용 할 수 있고 공통의 디자인 패턴을 적용할 수 있음
    - 이 때, 코드의 `Author`와 `Reviewer`는 코드 품질에 대해 공통된 책임이 있음

### 지식 공유

- 코드를 다듬기 위해 노력하는 과정에서 엔지니어의 전문 지식도 향상됨

## Flow of a pull request

- Flow of a pull request
    - Create a feature branch
    - Make and commit changes
    - Open a pull request
    - Request a review
    - Get reviewer's comments

## Commit

- 해당 브랜치에 적용하거나 다른 브랜치에 적용할 변경사항 세트의 이름
- 따라서, 커밋 내용은 작고 `원자적`이어야함 (분할 불가)
- 커밋 제목은 일반적으로 짧게 한다(up to 100 characters)
- 커밋 메세지는 무엇이 변경되었는지에 대한 답과 변경 이유가 포함되어야함
- 무슨 일이 일어났는지 코드를 볼 필요 조차 없어야함
- 이해하기 쉬운 커밋 메세지 만들기
    - 변경 이유의 문맥적 디테일
    - 코드의 다른 부분에 미치는 영향 (부작용)
    - 코드 작성과 관련된 모든 도메인 지식

커밋 메시지의 대안 인 코드의 주석은 개발자가 코드를 변경했지만 주석 업데이트를 잊어 버린 경우 쉽게 구식이 될 수 있으므로 효율성이 떨어집니다.

## Self-Review

- 내 시간이 중요한 만큼 동료의 시간도 중요하다
- `Self-review` 없이 `pull-request`를 날리는 것은 비매너
- 목표는 검토요청 하기 전에 코드를 분리하여 정리하는 것
- 오타, 오류, 변경점을 새로운 시각으로 볼 것

## Requesting a review

### How many reviewers?

- 기본적으로 소규모 팀에선 2명 이상일 필요가 없음
- `Merge`전에 몇 번의 승인을 받을 것인지가 나타남

### Pull request description

- 리뷰어는 요청한 PR의 정보를 모름
- 요청한 `PR`을 검토할 수 있도록 도와줘야함
- 확장된 커밋의 짧은 버전
- 예상 상태의 스크린샷을 포함할 수 있음
- 체크리스트를 만들 수도 있음

## Reviewing process

### Manual approach

- 작업을 인계하는 것처럼 코드리뷰해야함
- 변경된 라인에 대해 `Comment`를 남길것
- 큰 `PR`은 검토하기 어렵기 때문에 작은 `PR`로 쪼개야함
- 그래도 큰 `PR`을 해야한다면 적절한 `Commit`별 `Commit message`가 필수

### Automatic approach

- `Linter`를 사용하여 스타일 오류, 버그, 구조 등을 자동 감지
- `CI`를 통해 자동화 된 테스트를 실행할 수도 있음
- 하지만 추상적인 사고와 코드의 의미론에 대한 이해가 필요한 것은 자동화할 수 없음

## Three outcomes of the review

### Request for change

- 코드 변경 요청

### Discussion

- PR을 거부할지 여부에 대한 결정에 도달하지 않았음
- 가장 시간이 많이 소요됨
- 검토자와 변경사항이 괜찮은지 추가 수정이 필요한지에 대해 논의

### Approval

- 검토자가 제안한 변경 사항에 만족하면 마스터 브랜치에 병합
- 또는 병합 전 통과하는 검사를 구성

## Pull request trains

- 먼저 수행되어야 하는 작업이 아직 병합되지 않은 경우 `PR Train`이 발생함

## Solution approach

- 다른 작업을 처리하고 이전 분기 위에 새 분기를 시작
- 새분기의 `PR` 제목에 접미사를 추가해서 명확하게 해야함

## How long does it take from opening PR to closing it?

- 20일 이상까지 걸릴 수 있음
- 한 `Sprint` 내에 완료 하려고 해야함

## 참고

- [https://railsware.com/blog/pull-request-review-from-a-railsware-engineers-perspective/](https://railsware.com/blog/pull-request-review-from-a-railsware-engineers-perspective/)