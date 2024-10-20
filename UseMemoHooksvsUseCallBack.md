
The useMemo hook in React is used to memoize expensive calculations, ensuring that 
the calculation is only recomputed when its dependencies change. 
This can help improve performance in components that rely on computationally intensive 
logic or when rendering large lists.
it return a memoised value 

When to Use useMemo
Expensive Calculations: If you have a calculation that takes a lot of time and you want to avoid recalculating it on every render.
Referential Equality: When you want to ensure that a function or object reference remains the same between renders, which can help prevent unnecessary re-renders in child components that rely on React.memo.

How useMemo Works
useMemo takes two arguments:

A function that returns a computed value.
An array of dependencies that the memoization is based on. The computed value will only be recalculated when one of the dependencies changes.

const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);

import React, { useState, useMemo } from 'react';

const SumComponent = () => {
  const [numbers, setNumbers] = useState([1, 2, 3, 4, 5]);
  const [inputValue, setInputValue] = useState('');

  // Function to calculate the sum
  const calculateSum = (nums) => {
    console.log('Calculating sum...');
    return nums.reduce((acc, num) => acc + num, 0);
  };

  // Memoize the sum calculation
  const memoizedSum = useMemo(() => calculateSum(numbers), [numbers]);

  const handleInputChange = (e) => {
    setInputValue(e.target.value);
  };

  const addNumber = () => {
    const num = parseInt(inputValue);
    if (!isNaN(num)) {
      setNumbers((prevNumbers) => [...prevNumbers, num]);
      setInputValue('');
    }
  };

  return (
    <div>
      <h1>Sum: {memoizedSum}</h1>
      <input
        type="text"
        value={inputValue}
        onChange={handleInputChange}
      />
      <button onClick={addNumber}>Add Number</button>
      <h2>Numbers: {numbers.join(', ')}</h2>
    </div>
  );
};

export default SumComponent;



The useMemo hook is a powerful tool for optimizing performance in React applications. It allows you to avoid unnecessary recalculations, 
especially in components that deal with complex data processing or 
rendering large lists. By using useMemo wisely, you can enhance the responsiveness of your applications.



The useCallback hook in React is used to memoize callback functions, ensuring that a function reference remains stable between renders unless its dependencies change.
This is particularly useful when passing functions to child components to avoid unnecessary re-renders.

When to Use useCallback
Preventing Unnecessary Re-renders: When you pass a callback function to a child component, React creates a new function on every render. If the child component is wrapped with React.memo, it will re-render whenever the function reference changes. useCallback helps to maintain the same function reference unless its dependencies change.
Performance Optimization: In components with performance-critical code, using useCallback can prevent re-renders and recalculations.
How useCallback Works
useCallback takes two arguments:

A function that returns a callback.
An array of dependencies that the callback is based on. The function will only be recreated when one of the dependencies changes.
const memoizedCallback = useCallback(() => {
  // Your callback logic here
}, [dependencies]);



// Child component
const NumberDisplay = React.memo(({ number, onIncrement }) => {
  console.log(`Rendering NumberDisplay: ${number}`);
  
  return (
    <div>
      <h2>{number}</h2>
      <button onClick={onIncrement}>Increment</button>
    </div>
  );
});

// Parent component
const App = () => {
  const [numbers, setNumbers] = useState([0, 1, 2]);

  // Memoize the increment function
  const incrementNumber = useCallback((index) => {
    setNumbers((prevNumbers) => {
      const newNumbers = [...prevNumbers];
      newNumbers[index] += 1; // Increment the specific number
      return newNumbers;
    });
  }, []);

  return (
    <div>
      <h1>Number List</h1>
      {numbers.map((number, index) => (
        <NumberDisplay 
          key={index} 
          number={number} 
          onIncrement={() => incrementNumber(index)} 
        />
      ))}
    </div>
  );
};

Child Component: The NumberDisplay component is wrapped with React.memo, meaning it will only re-render if its props change. 
It receives a number prop to display and an onIncrement prop (a function) to increment the number.

useCallback is react hook that allow u to cache a funtion between rerender it mean when u use callback it does not allow  a multple instance of funtion when rerender happen

