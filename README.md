# Ngrx

## Setup
```
ng add @ngrx/store
ng add @ngrx/store-devtools

// install Redux devtools chrome extension

ng g store auth/Auth --module auth.module.ts
```

## Create action

```javascript
// user.component.ts
this.store.dispatch({
	type: 'Login',
	payload: {name: 'hemant'}
})
```

Better way to write action..

```javascript
// user.actions.ts
export const login = createFunction(
	'[Login Screen] User Login',
	props<{user: User}>()
);

// action without arguments
export const logout = createFunction(
	'[Login Screen] User Logout'
);
```

## Reducer

```javascript
export interface CounterState {
	count: number;
}

export const initialCounterState: CounterState = 0;
export function counterReducer(state, action): CounterState {
  initialCounterState,
  on(increment, state => state + 1)
}
```

## Query from store

```javascript
const user$ = this.store.pipe(map(user => !user), distinctUntilChanged());

// user.selectors.ts
const user$ = this.store.pipe(map(user => !user), distinctUntilChanged());

// better
export const isUserLoggedIn = createSelector(
	state => state['user'], // select global state
	(user) => user.loggedIn // select specific part
)
```

### Feature Selector

```javascript
exort const selectAuthState = createFeatureSelector<AuthState>('auth');
exort const isLoggedIn = createSelector(
	selectAuthState,
	(user) => user.loggedIn
)
```

## Effects
Do something extra when action is dispatched.

Handle async data, addition of storing data in store also it may store somewhere else ie database, local storage etc.

```javascript
// user.module.ts
@NgModule({
	imports: [
		EffectsModule.forFeature([SideEffects])
	]
})

//user.effects.ts
export class SideEffects {
	constructor(action$: Action) {
		action$.subscribe(action => {
			if (action.type === '[Login Screen] Login') {
				// do something
			}
		});
	}
}

// With manual subscription
export class SideEffects {
	constructor(private action$: Action) {
		login $ = this.action$.pipe(
			ofType(AuthActions.login),
			tap(action => {
				// do something
			});
		);

		login$.subscribe();
	}
}

// Without manual subscription
// dispatch required if not dispatching action from here
export class SideEffects {
	login$ = createEffect( () =>
		this.action$.pipe(
			ofType(AuthActions.login),
			tap(action => {
				// do something
			});
		), {dispatch: false)};

	constructor(private action$: Action) {

	}
}
```






























