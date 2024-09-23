## Axios Guide

```
import axios from 'axios';
```

### Get Method

```
const fetchData = async () => {
    try {
      // Making the GET request to the API
      const response = await axios.get("https://example.com/api/resource");

      // Log the data received from the server
      console.log("Data:", response.data);

    } catch (error) {

      if (error.response) {
        // Server responded with an error
        console.error("API Error:", error.response.status, error.response.data);

      } else if (error.request) {
        // Request was made but no response received
        console.error("Network Error:", error.request);

      } else {
        // Other errors
        console.error("Error:", error.message);
      }
    }
  };
```

### Post Method

```
  const postData = async () => {
    try {
      const data = { key: "value" }; // Data to send

      const response = await axios.post("https://example.com/api/resource", data);

      console.log("Success:", response.data); // data
      console.log("Success:", response.status); // status code: 201

      if (response.status === 201) {
        console.log("Resource created successfully.");
      }

    } catch (error) {
      --Same as above--
    }
  };
```

### Delete Method

```
  const deleteData = async (id) => {
    try {
      // Validate ID
      if (!id) {
        throw new Error("Invalid ID");
      }

      // Send DELETE request to the API
      const response = await axios.delete(`/resource/${id}`);

      // Handle successful deletion
      if (response.status === 204) {
        console.log("Resource successfully deleted. No content returned.");

      } else if (response.status === 200) {
        console.log("Resource successfully deleted. Data:", response.data);

      } else {
        console.log("Unexpected status:", response.status);
      }
    } catch (error) {
      --Same as above--
    }
  };
```

### Put Method

```
  const putData = async () => {
    try {
      const id = 1; // ID of the resource to update
      const data = { key: "newValue" }; // Data to update

      // Send PUT request to the API
      const response = await axios.put(
        `https://example.com/api/resource/${id}`,
        data
      );

      // Handle response based on status code
      if (response.status === 200) {
        console.log("Resource successfully updated. Response Data:",response.data);

      } else if (response.status === 204) {
        console.log("Resource successfully updated. No content returned.");

      } else {
        console.log("Unexpected status code:", response.status);
      }
    } catch (error) {
      --Same as above--
    }
  };
```
### Base URL configuration
#### Create a new file called `axiosInstance.js`
```
import axios from 'axios';

const axiosInstance = axios.create({
  baseURL: "https://example.com" // Base URL for all requests
});

export default axiosInstance;
```

#### Usage:
```
import axiosInstance from './axiosInstance'; // Import the Axios instance

const response = await axiosInstance.get('/products'); //https://example.com/products
```
