# 섹션 2

</br>

### CSS

fixed는 %가 잘 안 먹음

그래서 inherit → 상속을 사용

부모의 사이즈를 그대로 받아 옴

</br>

### ActiveLink

주소와 연결 됨

client side에서 가능! → 어느 게 선택 되어 있는지

`useSelectedLayoutSegment()` 이 훅이 사용 됨

현재 선택 된 segment를 알려줌

현재 레이아웃에 있는 부모 폴더들만 segment로 취급해서 반환

만약 그 안에 있는 자식 경로까지 받고 싶다면? → `useSelectedLayoutSegments()`

s를 붙이면 됨!!

```jsx
const segment = useSelectedLayoutSegment();
console.log(segment); // compose

const segments = useSelectedLayoutSegments();
console.log(segments); // ['compose', 'tweet']
```

useHook, event Listener는 모두 client side!

</br>

### useContext

use client → client 컴포넌트

provider 필요

</br>

### dayjs

날짜, 시간 계산하는 라이브러리

</br>

### classnames로 클래스 합성하기

cx 라이브러리

객체, 배열 다 됨

```jsx
<div className={cx(style.commentButton, { [style.commented]: commented })}> </div>
<div className={cx(style.repostButton, reposted && style.reposted)}> </div>
<div className={cx([style.hearButton, liked && style.liked])}> </div>
```

</br>

### Modal

@modal 폴더 만듦

항상 default.tsx가 존재 해야 함

parallel 할 때는 layout에 항상 modal 자리를 마련해줘야 함

intercepting 해야 함 (.) 붙여서 폴더 만들기

</br>

### usePathname

/ 부터 해서 물음표 앞까지가 pathname

useSearchParams → & 연산자로 묶인 params 읽어옴

</br>

### 이벤트 캡처링

server component는 client component의 children, props로 보낸다!!

client component에 server component가 있으면 client로 성격이 바뀌어 버림

onClickCapture → a 태그가 겹칠 때 사용

_move 기능 설명!!! → 7분쯤_

</br>

### faker.js

npm i @faker-js/faker

→ 더미 데이터 쉽게 넣어주는 라이브러리

photo modal에서 페이지가 존재하는 폴더 안에는 무조건 default.tsx가 있어야 함

[username], [id]는 default.tsx가 있어야 함

얘네는 페이지가 존재하기 때문에 인터셉트 문제를 위해 꼭 default 넣어 주기
