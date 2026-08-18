# Clean Frontend Skills

아이엠티소프트(IMTSOFT) 사내 프론트엔드 & 디자인 가이드 스킬. LLM이 생성한 UI 특유의 "AI티"(특정 산세리프 폰트, 불필요한 그라데이션, 과도한 그림자, 이모지 남발, 의미 없는 애니메이션 등)를 제거하고, POS·키오스크·KDS/DID·테이블오더·QR오더·MDM·ESL 콘솔 등 사내 제품에 맞는 절제되고 실무적인 UI를 만들기 위해 사용합니다.

## 언제 트리거되는가

"디자인", "UI", "화면", "프론트", "스타일", "컴포넌트 만들어줘" 등 시각적 결과물을 만들거나 수정하는 모든 요청에서 트리거됩니다. 신규 컴포넌트, 페이지, 랜딩, 대시보드, 관리자 화면 등 사내 웹 프론트엔드 작업 전반에 적용됩니다.

일반 `frontend-design` 스킬과 함께 사용하되, 두 스킬의 지침이 충돌하면 이 스킬(금지 항목)을 우선합니다.

## 폴더 구성

```
clean-frontend-design/
├── SKILL.md                        # 스킬 본문 (금지 항목, 폰트 적용법, 색상 기준, 체크리스트)
├── README.md                       # 이 문서
└── assets/
    └── fonts/
        ├── PretendardVariable.woff2  # 사내 표준 폰트 (variable, weight 45~920)
        └── pretendard.css            # @font-face 정의
```

## 금지 항목

- **폰트**: Inter, Poppins, Manrope 등 AI 생성 UI 클리셰 폰트 금지 → Pretendard로 통일
- **그라데이션**: 정보 전달 목적이 없는 장식용 그라데이션 금지, 단색 기본
- **그림자**: 다중/컬러 soft shadow 금지, 1px 테두리 또는 얕은 그림자 1단계만
- **이모지**: UI 텍스트(버튼, 헤더, 알림)에 이모지 남발 금지, 아이콘 세트 사용
- **애니메이션**: 기능과 무관한 hover scale/bounce 등 장식용 모션 금지
- **색상**: 무채색 스케일 + accent 1개 기본, 다색 남발 금지
- **모서리 둥글기**: 과도한 border-radius/pill 버튼 남발 금지
- **레이아웃 클리셰**: 근거 없는 큰 숫자+그라데이션 카드, 의미 없는 01/02/03 넘버링 지양

자세한 기준과 예시 hex 값 등은 `SKILL.md`를 참고하세요.

## Pretendard 폰트 적용 방법

1. `assets/fonts/PretendardVariable.woff2`와 `pretendard.css`를 대상 프로젝트로 복사합니다.
2. `pretendard.css`의 `@font-face` 정의를 프로젝트 전역 CSS에 포함합니다(경로만 프로젝트 구조에 맞게 조정).
3. 기본 body 폰트로 아래를 지정합니다.
   ```css
   font-family: 'Pretendard Variable', -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif;
   ```
4. Variable font이므로 `font-weight`를 400/500/600/700 등 숫자로 세밀 조정할 수 있습니다. 본문/중간강조/제목 2~3단계로 제한해 사용합니다.
5. 자체 호스팅이 어려운 경우 CDN 대안:
   `https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/variable/pretendardvariable.min.css`

## 라이선스

Pretendard 폰트(`assets/fonts/`)는 SIL Open Font License 1.1을 따릅니다. 저작권자: Kil Hyung-jin. 원본: https://github.com/orioncactus/pretendard — 재배포·수정 시 OFL 조건을 확인하세요.

## 설치

패키징된 `.skill` 파일을 Claude에 업로드하면 프로필에 설치되며, 이후 프론트엔드 작업 시 자동으로 참고됩니다.
