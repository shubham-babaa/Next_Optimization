A Custom React Hook is a function that allows you to reuse stateful logic between components. 
Custom hooks are a way to extract component logic into a reusable function, 
making your code more modular and easier to maintain.


Custom hooks follow the naming convention of starting with use, 
allowing React to identify them as hooks. Inside a custom hook, you can use other hooks (like useState, useEffect, etc.) to implement logic.


import { useState, useEffect } from 'react';

// Create a custom hook for fetching data
const useFetch = (url) => {
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch(url);
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const result = await response.json();
        setData(result);
      } catch (error) {
        setError(error);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, [url]); // Re-run if the URL changes

  return { data, error, loading };
};

export default useFetch;


import React from 'react';
import useFetch from './useFetch';

const DataDisplay = () => {
  const { data, error, loading } = useFetch('https://api.example.com/data');

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <div>
      <h1>Data:</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
};

export default DataDisplay;

