---
name: imtsoft-clean-frontend
description: In-house Frontend & Design Guide Skills. Always trigger these skills when working on frontend tasks.
---

# IMTSoft Clean Frontend

LLM이 생성한 UI 특유의 "AI 느낌"을 제거하고, 실무 SaaS/현장 소프트웨어(POS, 키오스크 등)에 맞는 절제되고 신뢰감 있는 디자인을 만든다. 화려함보다 명료함을, 장식보다 기능을 우선한다.
프론트 작업 시 general frontend 스킬 사용을 허용하되, 이 스킬에 명시한 사항을 우선 적용한다.

## 금지 항목

작업 전/후 아래 항목을 하나씩 점검한다. 하나라도 걸리면 제거하거나 대안으로 대체한다.

- **폰트**
  - 금지: Inter, Poppins, Manrope, Space Grotesk, Plus Jakarta Sans 등 AI 생성 UI에서 흔히 쓰이는 산세리프 조합
  - 대안: 한글/영문 모두 Pretendard로 통일한다. 별도 세리프체가 브리프상 반드시 필요한 경우가 아니면 Pretendard 단일 폰트만 사용한다
  - 적용: `./assets/fonts/PretendardVariable.woff2`를 프로젝트에 복사하고, `./assets/fonts/pretendard.css`의 font-face 정의를 참고한다

- **그라데이션**
  - 금지: 배경, 버튼, 텍스트에 정보 전달 목적이 없는 그라데이션
  - 기본값: 단색
  - 예외: 진행률 표시, 강조 포인트처럼 그라데이션 자체가 정보를 전달하는 경우에만 제한적으로 허용한다

- **그림자**
  - 금지: 여러 겹의 부드러운 컬러 그림자(soft glow), blur 값이 큰 box-shadow
  - 대안: 구분이 필요하면 1px 테두리 또는 얕은 단일 그림자 1단계만 사용한다

- **보더**
  - 원칙: 사용을 최소화한다
  - 대안: 영역 구분이 필요하면 위 "그림자" 항목의 대안(1px 테두리 또는 얕은 그림자 1단계)을 우선 검토한다

- **이모지**
  - 금지: 버튼, 헤더, 카드 제목, 알림 등 UI 텍스트 내 이모지
  - 대안: 아이콘이 필요하면 실제 아이콘 세트(lucide 등)를 사용한다

- **애니메이션**
  - 금지: 기능과 무관한 hover scale-up, bounce, 과도한 transition
  - 허용 범위: 로딩, 상태 전환 등 기능적 피드백에 한해 짧고 절제된 애니메이션만 사용한다

- **색상**
  - 기본 구조: 무채색(회색 스케일) + accent 컬러 1개
  - 금지: 다색을 동시에 사용하는 것
  - 기준: accent는 브랜드/서비스 성격에 맞게 정하고, 근거 없이 추가하지 않는다

- **모서리 둥글기**
  - 금지: pill 형태 버튼, 과도한 border-radius를 기본값으로 사용하는 것
  - 기준: 프로젝트 톤(업무용 콘솔 vs 고객 대면 키오스크)에 맞는 절제된 값을 하나 정하고 전체에 일관 적용한다

- **레이아웃 클리셰**
  - 금지: 근거 없는 "큰 숫자 + 작은 라벨 + 그라데이션 카드" 조합, 의미 없는 01/02/03 넘버링
  - 기준: 실제 콘텐츠 구조가 해당 형식을 요구하는 경우에만 사용한다 — 콘텐츠 구조 요구 여부는 "이 숫자/넘버링이 없으면 정보 전달이 안 되는가"로 판단한다

- **설명 텍스트**
  - 금지: 기능/UI마다 사용법을 풀어 쓰는 설명 문구
  - 원칙: 사용자는 타이틀만으로 대부분 이해한다고 가정한다
  - 예외 처리: 설명이 꼭 필요하면 물음표 아이콘 등으로 tooltip을 만들고, 기본 크기는 최소화하되 클릭 시 전체 내용을 확인할 수 있도록 구성한다

- **로딩 처리**
  - 원칙: API 요청 중에는 사용자가 동일 작업을 중복 실행하지 못하도록 UI를 구성한다 (버튼 비활성화 또는 전체 화면 로딩 처리)
  - 기준: 단일 API 요청이면 spinner를 사용하고, 여러 API를 동시에 요청하면 progress bar로 진행 상태를 표시한다

- **용어**
  - 금지: 프론트 UI 텍스트에 API, 프론트, 서버, 상태코드, DB 등 전문용어를 노출하는 것
  - 대안: 프론트에는 일반 사용자가 이해할 수 있는 단어를 쓰고, 전문용어는 로그에만 남긴다

- **에러 처리**
  - 금지: 화면에 Stack Trace를 노출하는 것
  - 기준: 네트워크 오류 등으로 API 응답을 받지 못한 경우, "인터넷 연결을 확인해주세요"처럼 일반 사용자가 바로 이해할 수 있는 표현으로 상황을 설명한다

- **엣지케이스**
  - 항상 확인할 것: 짧은 문자열 placeholder도 글자가 길어질 경우를 고려한다
  - 적용 범위: 텍스트 길이뿐 아니라 창의 가로/세로 크기 변화, 컴포넌트 내 요소 개수가 극단적으로 많아지는 경우도 함께 고려한다
  - 기본 처리: 오버플로우 발생 시 truncate-end 등 대응을 항상 적용해둔다

## 폰트 적용 방법

Pretendard Variable 파일은 `assets/fonts/`에 있다.

- `assets/fonts/PretendardVariable.woff2` — variable font 본체
- `assets/fonts/pretendard.css` — `@font-face` 정의 (variable weight 45~920 지원)

적용 순서:
1. 프로젝트에 `PretendardVariable.woff2`를 복사하고, `pretendard.css`의 `@font-face`를 프로젝트 CSS에 포함시킨다 (경로만 프로젝트에 맞게 조정한다).
2. `font-family: 'Pretendard Variable', -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif;`를 기본 body 폰트로 설정한다.
3. CDN이 가능한 프로젝트에서는 자체 호스팅을 우선하고, 부득이한 경우에만 `https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/variable/pretendardvariable.min.css`를 대안으로 사용한다.
4. 두께는 `font-weight: 400/500/600/700` 등 숫자로 세밀하게 조정한다. 굵기 단계는 2~3단계(본문/중간강조/제목)로 제한한다.

## 색상/타이포 기준을 새로 정할 때

컬러 팔레트가 브리프에 지정되어 있지 않으면 다음 순서로 정한다:
1. 배경/텍스트/보더용 무채색 스케일 4~6단계를 hex 값으로 명시한다 (예: `#0A0A0A`, `#4A4A4A`, `#8A8A8A`, `#D4D4D4`, `#F5F5F5`, `#FFFFFF`).
2. accent 컬러 1개를 hex 값으로 명시한다.
3. Primary, Active 등 활성 UI에는 배경/secondary 색상 체계를 적용한다.
4. 공용 컴포넌트가 지정되어 있지 않으면 색상을 프로젝트 내 공용 컴포넌트로 저장한다. 공용 컴포넌트의 색상 값만 바꾸면 앱 전체 색상을 제어할 수 있도록 구성한다.
5. 크림 배경+세리프+테라코타 accent, 검정 배경+형광 accent 등 흔히 반복되는 AI 생성 팔레트는 브리프상 근거가 없으면 재사용하지 않는다.
6. 타이포는 Pretendard 하나로 통일하고, 제목/본문/캡션 등 role별로 크기·굵기·자간만 다르게 적용한다.

## 작업 전 자가 점검

코드를 넘기기 전에 다음 항목을 확인한다:
- 그라데이션이나 그림자를 습관적으로 넣지 않았는가
- 버튼/헤더에 불필요한 이모지가 들어가지 않았는가
- hover/transition이 기능과 무관하게 화려하기만 하지 않은가
- 폰트가 Pretendard로 통일되어 있는가

하나라도 걸리면 금지 항목을 확인하고 수정한 뒤 결과물을 전달한다.