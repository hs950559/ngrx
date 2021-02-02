# Reducer

- pure function are reducers
- reducer respond to action type
- get access to action ( payload & state)
- returns new state

```javascript
// State
const state = {
	todos: []
};
```

```javascript
// Action
{
	type: 'ADD_USER',
	payload: 'Go to market'
}
```


```javascript
function reducer(state, action) {
	switch(action.type) {
		case: 'ADD_TODO': {
			const todo = action.payload;
			const todos = [...state.todos, todo];
			return { todos };
		}
	}

	return state;
}

// Now state becomes
{
	todos: [ 'Go to market']
}
```