# CLAUDE.md

## UI 파운데이션: HeroUI v3 (필수)

이 저장소에서 만드는 **모든 툴·서비스의 UI는 [HeroUI v3](https://heroui.com/)를 파운데이션으로 구현한다.**
다른 UI 라이브러리(MUI, Chakra, Mantine, Ant Design, shadcn/ui, HeroUI v2/NextUI 등)를 새로 도입하지 않는다.

### 기본 스택
- React 19+ / Tailwind CSS v4+ (HeroUI v3의 peer dependency)
- 설치: `npm install @heroui/react` (React 앱), 스타일만 필요하면 `@heroui/styles`
- 메인 CSS:
  ```css
  @import "tailwindcss";
  @import "@heroui/styles";
  ```
- `<Provider>` 래퍼는 필요 없다.

### 작성 규칙
- 컴포넌트는 `@heroui/react`에서 가져오고, v3의 컴파운드 API를 사용한다
  (예: `Card`, `Card.Header`, `Card.Content`, `Select.Item`).
- v2 API(`@nextui-org/*`, `HeroUIProvider`, `heroui()` Tailwind 플러그인 등)는 쓰지 않는다.
- 색·간격·타이포는 HeroUI 테마 토큰(CSS 변수)과 Tailwind 유틸리티로 맞추고, 하드코딩을 피한다.
- 다크 모드는 `<html class="dark">` 또는 `data-theme="dark"`로 전환한다.
- HeroUI에 없는 컴포넌트가 필요하면 HeroUI 프리미티브 + Tailwind로 조합하고,
  접근성은 React Aria(HeroUI의 기반) 패턴을 따른다.

### React가 아닌 정적 페이지(HTML 단일 파일 등)
- `@heroui/styles`의 BEM 클래스(`button button--primary button--sm` 등)를 사용해
  HeroUI v3 디자인 시스템과 동일한 룩앤필을 유지한다.

### 참고
- 문서: https://heroui.com · LLM용 요약: https://heroui.com/llms.txt
- MCP 서버: `@heroui/react-mcp` · 에이전트 스킬: `npx heroui-cli agents-md`
