# Store

- State container
- Component interacts with store
	- subscribes to slice of store
	- dispatch action to store
- Store invokes reduces with previous state and current action
- Once store modified by reducers it notifies subscribers

Single object contains state of your application

```
// State
{
	users: [],
	todos: [],
	albums: [],
	books: {
		java: [],
		php: [],
		nodejs: []
	},
	messageCount: 0
}
```

Store is big global application-level state: the store is an application wide singleton service.

<div class="card border-danger mb-3">
  <div class="card-header text-danger">Caution!</div>
  <div class="card-body">
    <p class="card-text">All of that helps, but we have still created global application state, and the main problem is still there: it exists and we need to clean it up at all in all the right places, and that does not scale well in complexity.</p>
  </div>
</div>

### What is the best way to deal with global state?

The best way to avoid global application state is to not create it unless it's necessary

### Create Local state that cleans itself

create a state that is local only to that interaction with that particular master-detail setup, and to make it so that it cleans itself up automatically after use.

```javascript
@Component({
  selector: 'messages-container',
  providers: [MessagesService],
  template: `
        Messages Master Detail Container:
        <router-outlet></router-outlet>
  `
})
export class MessagesContainerComponent {
      ...
}
```