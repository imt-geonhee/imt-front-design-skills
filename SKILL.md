---
name: clean-frontend-design
description: 아이엠티소프트(IMTSOFT) 사내 프론트엔드 디자인 가이드. "AI가 만든 티"가 나는 디자인 요소(특정 산세리프 폰트, 불필요한 그라데이션, 과도한 그림자, 이모지 남발, 의미 없는 애니메이션 등)를 제거하고 깔끔하고 실무적인 UI를 만들기 위한 규칙을 담고 있음. POS, 키오스크, KDS/DID, 테이블오더, QR오더, MDM, ESL 콘솔 등 사내 모든 웹 프론트엔드 작업(신규 컴포넌트, 페이지, 랜딩, 대시보드, 관리자 화면 등)에서 반드시 참고. "디자인", "UI", "화면", "프론트", "스타일", "컴포넌트 만들어줘" 등 시각적 결과물을 만들거나 수정하는 모든 요청에서 트리거해야 함. general frontend-design 스킬과 함께 사용하되, 아래 금지 항목이 충돌하면 이 스킬을 우선한다.
---

# Clean Frontend Design (IMTSOFT 사내 기준)

목적: LLM이 생성한 UI 특유의 "AI티"를 없애고, 실무 SaaS/현장 소프트웨어(POS, 키오스크 등)에 맞는 절제되고 신뢰감 있는 디자인을 만든다. 화려함보다 명료함, 장식보다 기능을 우선한다.

## 금지 항목 (구체적 체크리스트)

작업 전/후 아래 항목을 스스로 점검한다. 하나라도 걸리면 제거하거나 대체한다.

- **폰트**: Inter, Poppins, Manrope, Space Grotesk, Plus Jakarta Sans 등 AI 생성 UI에서 흔히 쓰이는 산세리프 조합 금지. 한글/영문 모두 **Pretendard**(assets/fonts 참고)로 통일한다. 디스플레이용 별도 세리프체가 브리프상 꼭 필요한 경우가 아니면 폰트는 Pretendard 하나로 충분하다.
- **그라데이션**: 배경, 버튼, 텍스트에 의미 없는 그라데이션 금지. 기본은 단색. 진행률·강조 포인트처럼 그라데이션이 실제 정보를 전달하는 경우에만 아주 제한적으로 허용한다.
- **그림자**: 여러 겹의 부드러운 컬러 그림자(soft glow), 큰 blur 값의 box-shadow 금지. 구분이 필요하면 1px 테두리나 아주 얕은 단일 그림자 한 단계만 사용한다.
- **이모지**: 버튼, 헤더, 카드 제목, 알림 등 UI 텍스트에 이모지 남발 금지. 아이콘이 필요하면 실제 아이콘 세트(lucide 등)를 쓴다.
- **애니메이션**: 의미 없는 hover scale-up, bounce, 과도한 transition 남발 금지. 로딩, 상태 전환처럼 기능적 피드백에만 짧고 절제된 애니메이션을 쓴다.
- **색상**: 무채색(회색 스케일) 기반 + 명확한 accent 컬러 1개가 기본. 다색을 동시에 쓰지 않는다. accent는 브랜드/서비스 성격에 맞게 정하되 자의적으로 남발하지 않는다.
- **모서리 둥글기**: pill 형태 버튼이나 과도한 border-radius를 기본값으로 쓰지 않는다. 프로젝트 톤(업무용 콘솔 vs 고객 대면 키오스크)에 맞게 절제된 값을 정하고 전체에 일관 적용한다.
- **레이아웃 클리셰**: 근거 없는 큰 숫자 + 작은 라벨 + 그라데이션 카드 조합, 의미 없는 01/02/03 넘버링 등 템플릿 느낌의 장식은 실제 콘텐츠가 그 구조를 요구할 때만 사용한다.

## 폰트 적용 방법

Pretendard Variable 파일이 `assets/fonts/`에 있다.

- `assets/fonts/PretendardVariable.woff2` — variable font 본체
- `assets/fonts/pretendard.css` — `@font-face` 정의 (variable weight 45~920 지원)

적용 순서:
1. 프로젝트에 `PretendardVariable.woff2`를 복사하고 `pretendard.css`의 `@font-face`를 프로젝트 CSS에 포함한다 (경로만 맞게 조정).
2. `font-family: 'Pretendard Variable', -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif;`를 기본 body 폰트로 설정한다.
3. CDN이 가능한 프로젝트라면 자체 호스팅을 우선하되, 부득이한 경우 `https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/variable/pretendardvariable.min.css`도 대안이 될 수 있다.
4. 두께는 variable font 특성상 `font-weight: 400/500/600/700` 등 숫자로 세밀하게 조정 가능하다. 굵기 단계를 과도하게 남발하지 말고 2~3단계(본문/중간강조/제목)로 제한한다.

## 색상/타이포 기준을 새로 정할 때

컬러 팔레트가 브리프에 지정되어 있지 않다면:
- 배경/텍스트/보더용 무채색 스케일 4~6단계 (예: `#0A0A0A`, `#4A4A4A`, `#8A8A8A`, `#D4D4D4`, `#F5F5F5`, `#FFFFFF`)와 accent 1개를 정하고 hex 값으로 명시한다.
- 흔히 반복되는 AI 생성 팔레트(크림 배경 + 세리프 + 테라코타 accent, 검정 배경 + 형광 accent 등)를 별다른 이유 없이 재사용하지 않는다.
- 타이포는 Pretendard 하나로 role별(제목/본문/캡션) 크기·굵기·자간만 다르게 가져가는 것을 기본으로 한다.

## 작업 전 자가 점검

코드를 넘기기 전에 위 "금지 항목" 리스트를 다시 훑는다. 특히:
- 그라데이션이나 그림자를 습관적으로 넣지 않았는지
- 버튼/헤더에 불필요한 이모지가 들어가지 않았는지
- hover/transition이 기능과 무관하게 화려하기만 한지
- 폰트가 Pretendard로 통일되어 있는지

하나라도 걸리면 수정 후 결과물을 전달한다.
