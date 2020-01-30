회원가입, 로그인 하면 토큰, 이메일, 이름을 데이터로 넘겨주고



1. 유저 데이터를 vuex state에 저장

2. local storage에 저장
3. 토큰을 Axios 헤더에 추가



logout

1. 유저 데이터를 state에서 지움
2. Local storage에서 유저 데이터 지움
3. Axios header에서 토큰 지움



## Navigation Guard

Meta 는 사용자가 임의로 속성값는 지정할 수 있게 하는 속성

```js
meta: {
				requireAuth: true
			}
```

to = 갈 곳 from = 현재 위치 next = 실행될 곳

>  requireAuth 를 True로 해준다.
>
> 밑에 로직 실행되면 requireAuth 가 True인 애들은 조건문들로 들어감
>
> 아닌 애들은 젤 밑에 else 문에 next() 타고 원래 갈라는데 감
>
> ->  requireAuth가 True인 애들은 권한 있는지 봐야하는 애들

```js
router.beforeEach((to, from, next) => {
	const loggedIn = localStorage.getItem('user')
	const userType = localStorage.getItem('userType')

	if (to.matched.some(record => record.meta.requireAuth)) {
		if (!loggedIn) {
			if (userType == 1) {
				next('mlogin')
			} else if (userType === 2) {
				next('StoreLogin')
			} else if (userType === 3) {
				next('/')
			} else {
				next('/')
			}
		} else {
			next()
		}
	} else {
		next()
	}
});

export default router
```



# Vuex 

컴포넌트 간의 데이터를 더 효율적으 전달 하기 위해 사용함

### 기존

> 1. Props, event emit 으로 넘기면 중간에 거쳐갈 컴포넌트가 많음
> 2. Event Bus를 사용하면 데이터 흐름을 파악하기 힘들다.



### state

> 컴포넌트간에 공유할 데이터들을 담아 놓음. (Vuex의 box역할)



### Mutation

> state의 값을 변경하는 로직
>
> 인자를 받아 Vuex에 넘겨줄 수 있음 (두번째 인자)
>
> methods에서 commit으로  호출해야함
>
> 동기적 로직 정의



### Actions

> 비동기 로직 정의
>
>  methods에서 dispatch로 호출



### Getters

> computed에서 this.$store.getters.~~ 로 호출