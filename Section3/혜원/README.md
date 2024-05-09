# 섹션 3

클라이언트 서버에서 백엔드 서버로 요청 보내기

가짜 서버로! MSW

redirect는 try catch에서 쓰면 안 됨!!

</br>

### Middleware

로그인 비로그인 구분하는 데 사용할 수 있는 Next.js 기능

페이지 접근 권한을 관리하기 편함

auth를 그대로 middleware로 호출하면 됨

auth를 호출 해서 로그인 여부를 확인할 수 있음

</br>

### catch-all route

`[…nextauth]`

dynamic route에서 … 이 들어간 폴더 구조

slug에 여러가지 경로가 들어올 수 있음

</br>

### next-auth

pages 속성으로 해당 auth에 대한 페이지를 지정해줄 수 있음

useSession → 모든 페이지에서 로그인 여부를 확인 하기 때문에 가장 바깥에 session provider로 감싸줘야 함

session token이 있어야 로그인이 된 것임 → next-auth에서 토큰을 쿠키에 저장 했을 때 자동으로 보안 적용을 해줌!

middleware에서 session 유무 여부를 통해 리다이렉트 시키는 방식이 더 자연스러움 → 해당 페이지에 접근 할 때 로그인 여부에 따라 리다이렉트

hydrate → server에서 받은 data를 client에서 그대로 물려 받는 것

이런 key를 갖고 있는 애는 이 함수를 실행 해서 값을 가져와라!

```jsx
const queryclient = new QueryClient();
await queryclient.prefetchQuery({queryKey: [’posts’, ‘recomments’], queryFn: getPostRecommends})
```

```jsx
const res = await fetch(url, {
  next: {
    tags: ["posts", "recommends"],
  },
  cache: "no-store",
});

revalidateTag("recommends");
revalidatePath("/home");
```

`cache: 'no-store'` server에 cache 되지 않게 함

`revalidateTag('recommends')` 이 태그를 가진 애들만 새로고침

`revalidatePath('/home')` 이 페이지 전체에 대해 새로고침

</br>

### React Query vs Redux

react-query → data를 가져오는 것

redux → 컴포넌트 사이에서 data를 공유하는 것

react-query는 caching을 잘 해줌

한 번 작성 하면 수정이 잘 안 되는 애들은 굳이 매번 데이터를 가져올 필요가 없으니, 일주일 정도 cache 공간에 넣어두고, 수정이 있을 때 마다 새로 받아오게 하는 것이 **traffic 절약**에 좋음

Redux는 caching 기능이 약하기 때문에 react-query가 더 많이 사용 됨

react-query도 컴포넌트 공유가 가능함

react-query는 interface를 표준화 함

데이터를 가져올 때는 로딩, 성공, 실패 상태가 있음

이것을 표준 api로 사용 가능 함

</br>

### react-intersection-observer

가장 밑에 react-intersection-observer를 두고, 이게 화면에 렌더링 되면 다음 페이지를 호출하게 함

인피니티 스크롤에서 어디가 마지막 요소인지 확인하기 위해 사용되는 라이브러리

inView → 화면에 보였는가? 를 판단하는 요소
