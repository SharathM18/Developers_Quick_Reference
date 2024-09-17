# useLocalStorage Custom Hook

#### Paste the following code into your `useLocalStorage.jsx`

```bash
const useLocalStorage = ({ setError }) => {

  const setItem = (key, item) => {
    try {
      window.localStorage.setItem(key, JSON.stringify(item));
    } catch (error) {
      setError(error.message);
    }
  };

  const getItem = (key) => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : null;
    } catch (error) {
      setError(error.message);
    }
  };

  const removeItem = (key) => {
    try {
      window.localStorage.removeItem(key);
    } catch (error) {
      setError(error.message);
    }
  };

  return { setItem, getItem, removeItem };
};

export default useLocalStorage;
```
#### Usage:

```bash
import useLocalStorage from "./components/useLocalStorage";
```

```bash
const { setItem, getItem, removeItem } = useLocalStorage();
```

```bash
  useEffect(() => {
    if (items.length) {
      setItem("key", items);
    }
  }, [items]);
```

- The key should be in the string

```bash
  useEffect(() => {
    setTasks(getItem("key"));
  }, []);
```
