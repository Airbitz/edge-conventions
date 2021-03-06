# [<](README.md) &nbsp; Redux Conventions

* [Async Error Handling](#async-error-handling)
* [Connectors](#connectors)

&nbsp;

----
&nbsp;

## Async Error Handling

```javascript
import { InsufficientFundsError } from ‘edge-core-js’
WALLET_API.someCall(edgeWallet, someInputs).then(handleSuccess, handleError)
const handleSuccess = (someData) => {...do stuff with data}
const handleError = (error: Error) => {
  if (error instanceof InsufficientFundsError) {
    return dispatch(displayInsufficientFundsAlert())
  }
  dispatch(unknownError(error)) // Handles all other error types
}
```

----

[Back to the top](#--redux-conventions)

&nbsp;

## Connectors

* Do not create new objects in connectors

```javascript
const defaults = {
  d: 123,
  e: 456
}
const mapStateToProps = (state: State) => {
  return {
    a: {
      ...defaults,
      ...state.a
    },
    b: state.b,
    c: state.c
  }
}
export const connectedMyComponent = connect(mapStateToProps, mapDispatchToProps)(MyComponent)
```

----

[Back to the top](#--redux-conventions)

&nbsp;
