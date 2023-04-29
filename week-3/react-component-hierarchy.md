---
description: 리액트 컴포넌트 계층구조
---

# React Component Hierarchy

#### 컴포넌트 계층구조

{% hint style="info" %}
[https://react.dev/learn/thinking-in-react](https://react.dev/learn/thinking-in-react) 참고

[https://react.dev/](https://react.dev/) 참고
{% endhint %}

#### 리액트의 강력한 특징

1. "Component Based"
2. "Build encapsulated components that manage their own state, then compose them to make complex UIs"

#### 계층구조의 몇가지 기준

1. SRP(Single Responsibility Principle) - 단일 책임 원칙: 하나의 클래스(캡슐화된)는 하나의 책임을 진다.
2. CSS - css의 기준에 따른다
3. Design's Layer
4. Information Architecture ( JSON schema의 영향) - 가장 많이 사용하게 됨, 자연스러운 SRP를 위해서 사실상 강제됨

{% hint style="info" %}
작은 컴포넌트(부품)을 만들어서 조립, 조합은 가지수를 폭발적으로 늘릴 수 있는 가장 전형적인 방법 ->&#x20;

Atomic Design
{% endhint %}

<figure><img src="../.gitbook/assets/스크린샷 2023-04-29 오후 9.19.31.png" alt=""><figcaption><p><a href="https://bradfrost.com/blog/post/atomic-web-design/">https://bradfrost.com/blog/post/atomic-web-design/</a></p></figcaption></figure>

#### Extract Function

{% hint style="info" %}
코드를 먼저 작성 하고, 분리하거나 잘라낼수 있는 부분을 함수로 추출하여 코드를 줄인다.

2가지 방법 - Extract / Inline
{% endhint %}

* Extract => 코드에서 다른 함수 또는 모듈로 분리하여 Import 하여 사용하는 방법

```jsx
// 대략적인 예시 - 파일을 불러와 코드에 삽입

//Name.jsx
export default function Name () {
    return(
        <b>Name ??</b>
    )
}
//Main.jsx
import Name from '@/components/Name'
const Main = () => {
    return (
        <Fragment>
            <Name/>
            <b>Age ??</b>
        </Fragment>
    )
}
```

* Inline => 코드를 먼저 작성 하고, 분리하거나 잘라낼수 있는 부분을 함수로 추출하여 사용하는 방법

```jsx
// 대략적인 예시 함수로 분리하여 내부에 함수호출. 코드를 간편하게 볼수있음

//Main.jsx
function Name = () => {
    return (
        <b>Name ??</b>
    )
};
const Main = () => {
    return (
        <Fragment>
            <Name/>
            <b>age ??</b>
        </Fragment>
    )
}
```

#### Props&#x20;

{% hint style="info" %}
컴포넌트간의 데이터를 주고받을때 사용하는 방법
{% endhint %}

```javascript
// https://react.dev/learn/passing-props-to-a-component
// 예제코드
// Avatar 컴포넌트에 Size와 person을 Props로 전달하여 컴포넌트를 그려내는 소스코드

import { getImageUrl } from './utils.js';
function Avatar({ person, size }) {
  return (
    <img
      className="avatar"
      src={getImageUrl(person)}
      alt={person.name}
      width={size}
      height={size}
    />
  );
}

export default function Profile() {
  return (
    <div>
      <Avatar
        size={100}
        person={{ 
          name: 'Katsuko Saruhashi', 
          imageId: 'YfeOqp2'
        }}
      />
      <Avatar
        size={80}
        person={{
          name: 'Aklilu Lemma', 
          imageId: 'OKS67lh'
        }}
      />
      <Avatar
        size={50}
        person={{ 
          name: 'Lin Lanying',
          imageId: '1bX5QH6'
        }}
      />
    </div>
  );
}

```

#### React의 State

{% hint style="info" %}
state는 "변경"을 다루기 위한 요소. "re-rendering"이란 주제에서 사용하게 됨.

어떤 컴포넌트의 state가 변경되면 연결된 컴포넌트를 재렌더링 한다.

일관성과 효율성을 위하여 DRY원칙을 따르는 SSOT를 만든다.

DRY - Don't repest yourself(중복배제: 모든 지식은 시스템 내에서 중복없이 유일해야함)

SSOT - Single source of truth(단일 진실 공급원: 저장소의 데이터를 기반으로 작동)
{% endhint %}

#### State인지 확인하기

* [ ] State는 변경되어야한다. 변하지않는건 state로 다룰 가치가 없음
* [ ] 부모 컴포넌트가 props를 통해 전달한다면 state가 아님
* [ ] 다른 state나 props를 이용하여 계산 가능하다면 state가 아님

다루는 state가 너무 많으면 복잡하다. 하지만 Typescript를 사용하여 직접 관리하는 상태의 수를 줄여 줄 수 있다. 리액트만 사용한다면, 상태에 의존하는 컴포넌트를 모두 포함하는(부모컴포넌트)가 상태를 소유 하면 됨&#x20;

#### Inverse Data Flow

{% hint style="info" %}
하위(자식) 컴포넌트의 props로 함수를 전달. 흔히 콜백 함수라고 부름
{% endhint %}

### 배운점과 나의 생각

1. 기존에 사용하던 방법에 대해 원론적인 부분을 다시한번 생각해보게 되었음
2. State의 선언에 대해 다시한번 정의해보게 되었음
3. Data Flow를 아직까지 완벽하게 나누는것 같진 않음
4. Props를 잘쓰기위해 Typescript의 숙련이 더 필요함

