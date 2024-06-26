# Storybook

데이터, API 또는 비즈니스 로직으로 벗어나 UI 컴포넌트와 페이지를 독립적으로 구축할 수 있는 프론트엔드 워크샵으로 UI 개발, 테스트 및 문서화를 제공해준다.

- 내구성이 뛰어난 UI를 개발할 수 있다.
- 팀이 재사용할 수 있도록 UI를 문서화할 수 있다.
- 스토리를 통해 UI가 실제로 어떻게 작동하는지 공유할 수 있다.
- CI 단계에 추가하여 UI 테스트를 자동화할 수 있다.
- 스토리를 한번 작성하면 다양한 개발 환경에서 재사용할 수 있다.

> **프론트엔드 워크샵**<br/>애플리케이션 환경 외부에서 UI 코드를 작성할 수 있는 환경

## Storybook을 사용하는 이유

https://storybook.js.org/docs/get-started/why-storybook

웹의 보편성으로 인해 프론트엔드의 복잡성이 더욱 커지고 있습니다. 반응형 웹 디자인으로 디바이스 크기 등에 따라 사용자는 서로 다른 UI를 보게 되었습니다. 이렇게 사용자가 사용하는 UI에는 디바이스, 브라우저, 접근성, 성능, 비동기 상태 등 추가적인 요구 사항이 생겼습니다.

React, Vue 3, Angular 등 컴포넌트 기반 도구는 복잡한 UI를 단순한 컴포넌트로 분해하는 데 도움을 주지만 비즈니스 로직, 인터랙티브 상태, 앱 컨텍스트에 얽혀 있어 디버깅하기가 어렵고, 문제를 더욱 복잡하게 만들 수 있습니다.

### UI를 독립적으로 구축할 수 있다.

컴포넌트의 강력한 장점은 렌더링 방식을 확인하기 위해 전체 앱을 실행할 필요가 없다는 것입니다. props을 전달하거나 데이터를 모킹하거나 이벤트를 가짜로 만들어 특정 변형을 따로 렌더링할 수 있습니다.

Storybook은 앱과 함께 제공되는 작은 개발 전용 워크샵으로 패키징되어 있습니다. 앱 비즈니스 로직 및 컨텍스트의 간섭 없이 컴포넌트를 렌더링할 수 있는 환경을 제공합니다. 이를 통해 컴포넌트의 각 변형, 심지어 도달하기 어려운 엣지 케이스까지 테스트할 수 있습니다.

### UI 변형을 스토리로 캡처할 수 있다.

스토리는 컴포넌트 변형을 시뮬레이션하기 위해 props와 mock data를 제공하는 선언적 구문입니다. 각 컴포넌트는 여러 개의 스토리를 가질 수 있습니다. 각 스토리를 통해 해당 컴포넌트의 특정 변형을 시연하여 모양과 동작을 검증할 수 있습니다.

세분화된 UI 컴포넌트 변형을 위한 스토리를 작성한 다음 개발, 테스트 및 문서화에서 해당 stories를 사용합니다.

### 모든 스토리를 추적할 수 있다.

Storybook은 UI 컴포넌트와 해당 스토리의 대화형 디렉토리입니다. 과거에는 앱을 실행하고 페이지로 이동한 다음 UI를 올바른 상태로 조정해야 했습니다. Storybook을 사용하면 특정 상태의 UI 컴포넌트로 바로 이동할 수 있습니다.

## 스토리

https://storybook.js.org/docs/get-started/whats-a-story

스토리는 UI 컴포넌트의 렌더링된 상태를 캡처합니다. 개발자는 컴포넌트가 지원할 수 있는 모든 상태를 설명하는 스토리를 컴포넌트당 여러 개 작성할 수 있습니다.

스토리는 컴포넌트 예제 작성을 위한 ES6 모듈 기반 표준인 Component Story Format(CSF)으로 작성됩니다.

> **Component Story Format(CSF)**<br/>스토리 작성에 권장되는 방식입니다. ES6 모듈을 기반으로 하는 개방형 표준으로 Storybook을 넘어 이식할 수 있습니다.

```ts
// Button.stories.ts|tsx

import type { Meta, StoryObj } from '@storybook/react';

import { Button } from './Button';

const meta: Meta<typeof Button> = {
  component: Button,
};

export default meta;
type Story = StoryObj<typeof Button>;

// args에 지정된 값이 컴포넌트를 렌더링하는 데 어떻게 사용되고 컨트롤 탭에 표시되는 값과 일치하는 확인할 수 있다.
export const Primary: Story = {
  args: {
    primary: true,
    label: 'Button',
  },
};
```

## Addons

https://storybook.js.org/docs/get-started/browse-stories#addons

스토리북의 핵심 기능을 확장하는 플러그인입니다. Storybook 하단의 예약된 위치인 Addons 패널에서 찾을 수 있습니다. 각 탭에는 선택한 스토리에 대해 생성된 메타데이터, 로그 또는 정적 분석이 표시됩니다.

- Controls : 컴포넌트의 인수(입력)와 동적으로 상호작용할 수 있습니다.
- Actions : 콜백을 통해 상호작용이 올바른 출력을 생성하는지 확인하는 데 도움이 됩니다.
- Interactions : 플레이 기능으로 인터렉션 테스트를 디버깅하는 데 유용한 사용자 인터페이스를 제공합니다.
- Visual Tests : 이 기능을 사용하면 Storybook에서 바로 피드백을 제공하여 로컬 개발 환경의 UI 버그를 찾아낼 수 있습니다.

## React & Vite에서 설치

### 요구 사항

- React 16.8 이상
- Vite 4.0 이상
- Storybook 8.0 이상

### 설치

```
npm create vite@latest storybook-example -- --template react-ts
npx storybook@latest init // 설치
npm run storybook // 실행
```
