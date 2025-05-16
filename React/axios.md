## Axios Guide

```
import axios from 'axios';
```

### Base URL configuration

#### Create a new file called `axiosInstance.js`

```javascript
import axios from "axios";

const axiosInstance = axios.create({
  baseURL: "https://example.com", // Base URL for all requests
  headers: {
    "Content-Type": "application/json",
  },
});

export default axiosInstance;
```

```
headers: {
    "Content-Type": "multipart/form-data",
},
```

#### Usage:

```
import axiosInstance from './axiosInstance'; // Import the Axios instance

const response = await axiosInstance.get('/products'); //https://example.com/products
```
