The useReducer hook is a React hook used for managing complex state logic in functional components. It is similar to useState, 
but it is preferred when the state logic involves multiple sub-values or when the next state depends on the previous one.


it is Similar to useState but insted of provideing state and setter funtion it provide state and dispatch funtion
it accecpt two arrgument 
reducer funtion
initial state
and return current state and dispatch funtion

const [state, dispatch] = useReducer(reducer, initialState);

reducer: A function that takes two arguments (the current state and an action) and returns the new state.
initialState: The initial state value.


const initialState = { count: 0 };

// Define the reducer function
const reducer = (state, action) => {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    case 'reset':
      return { count: 0 };
    default:
      return state;
  }
};


const Counter = () => {
  // Use the useReducer hook
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <h1>Count: {state.count}</h1>
      <button onClick={() => dispatch({ type: 'increment' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>Decrement</button>
      <button onClick={() => dispatch({ type: 'reset' })}>Reset</button>
    </div>
  );
};
