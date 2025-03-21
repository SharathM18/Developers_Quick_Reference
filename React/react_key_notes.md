# React Key Notes

## 1. Fragments

```
Use fragments - <> </> or <Fragment> </Fragment>
```

## 2. Exports

### Named export

```javascript
export function func_name() {}

import {} from "...";
```

### Default export

```javascript
export default function func_name() {}

import ... from "..."
```

## 3. Folder structure

```
src/
	components/
		/Buttons
			Button.jsx
			Button.css
```

## 4. Props

```javascript
// if there is one props, pass like this
<Component {...data} />;

function Component(props) {
  const { name, age } = props;
}

// passing the state values and default values for props
<Component
  data={data}
  name="Alex"
  number={9}
  obj={{ a: 1 }}
  array={[1, 2]}
  counter={counter}
  setCounter={setCounter}
/>;

function Component({ data, name, counter = "", setCounter }) {
  const { name, age } = data;
}

<button
  onClick={onClickHandler} // passing function as a props
  style={{ color: colorScheme === "dark" ? "white" : "black" }} // handling the ternary inside the inline style
  className={colorScheme === "dark" ? "text-white" : "text-black"} // handling the ternary for attributes
>
  {text}
</button>;
```

## 5. Events

```javascript
onClick();
onChange();
onBlur();
onFocus();
```

## 6. Form Handling

```javascript
const [formData, setFormData] = useState({name: "", age: "", course: ""})

const FormValueChangeHandler = (e) => {
		const {name, value}= e.target

		setFormData((prev) => {...prev, [name] : value})
	}

<input type="text" name="age" value={formData.age} onChange={FormValueChangeHandler} />
```

### Best Practice (`select` and `option`)

```javascript
const OPTIONS = ["Maths", "Literature", "History"]; // Move them out of the component

function CoursesSelector() {
  return (
    <select
      name="course"
      value={formData.course}
      onChange={FormValueChangeHandler}
    >
      <option value="">Select option</option>
      {OPTIONS.map((opt, idx) => (
        <option key={idx} value={opt}>
          {opt}
        </option>
      ))}
    </select>
  );
}
```

### React Hook Form

```javascript
const demoSchema = z.object({
  name: z.string().optional().min(3, { message: "name must be 3 characters" }),
  image: z.array(z.instanceof(File)).optinal(),
});

const {
  register,
  handleSubmit,
  setValue,
  formState: { isSubmitting, errors },
} = useForm({
  resolver: zodResolver(demoSchema),
  defaultValues: previousData || {},
});

const onFormSubmit = (data) => {
  console.log(data);
};

const handleImageChange = (e) => {
  const files = Array.from(e.target.files);

  if (files.length > 0) {
    setValue("images", files); // Register images in react-hook-form
    const previews = files.map((file) => URL.createObjectURL(file));
    setImagePreviews(previews); // Use state for display images
  }
};

<form onSubmit={handleSubmit((data) => onFormSubmit(data))}>
  <input type="text" {...register("name")} />
  {errors.name && <p>{errors.name.message}</p>}
  <input type="file" accept="image/*" multiple onChange={handleImageChange} />

  <button type="submit" disabled={isSubmitting}>
    {isSubmitting ? "Loading..." : "Submit"}
  </button>
</form>;
```

### forwardRef - `input` tag

```javascript
import React from "react";

const Input = React.forwardRef(function Input(
  { label, id, type = "text", className = "", ...props },
  ref
) {
  return (
    <div>
      {label && <label htmlFor={id}>{label}</label>}
      <input type={type} id={id} className={className} {...props} ref={ref} />
    </div>
  );
});

export default Input;
```

### forwardRef - `select` tag

```javascript
import React from "react";

const Select = React.forwardRef(function Select(
  { label, id, options, className = "", ...props },
  ref
) {
  return (
    <>
      <div>
        {label && <label htmlFor={id}>{label}</label>}
        <select id={id} className={className} {...props} ref={ref}>
          <option value="">--Select One--</option>
          {options.map((item, idx) => (
            <option value={item} key={idx}>
              {item}
            </option>
          ))}
        </select>
      </div>
    </>
  );
});

export default Select;
```

### forwardRef - `datalist` tag

```javascript
import React from "react";

const Datalist = React.forwardRef(function Datalist(
  { label, id, options, className = "", ...props },
  ref
) {
  return (
    <div>
      {label && <label htmlFor={id}>{label}</label>}
      <input list={id} className={className} {...props} ref={ref} />
      <datalist id={id}>
        {options.map((item, idx) => (
          <option value={item} key={idx} />
        ))}
      </datalist>
    </div>
  );
});

export default Datalist;
```

### forwardRef - `button` tag

```javascript
const Button = ({ children, type = "button", className = "", ...props }) => {
  return (
    <>
      <div>
        <button type={type} className={className} {...props}>
          {children}
        </button>
      </div>
    </>
  );
};

export default Button;
```

### forwardRef use case

```javascript
<Input
  label="Email: "
  id="email"
  type="email"
  placeholder="Email"
  {...register("email")}
/>
```

```javascript
<Select
  label="Select one: "
  id="choose"
  options={["1rgfergrg", "2gergergre", "3rgrgreg", "4grgrg", "5dggrg"]}
  data-color="red" // static attributes
  onChange={(e) => handleChange(e)} // without using RHF
/>
```

or

```javascript
<Select
  label="Select one: "
  id="choose"
  options={["1rgfergrg", "2gergergre", "3rgrgreg", "4grgrg", "5dggrg"]}
  data-color="red" // static attributes
  {...register("select", {
    onChange: (e) => {
      handleChange(e);
    },
  })}
/>
```

```javascript
<Datalist
  label="Enter the city: "
  id="city"
  options={["america", "mandya", "bengaluru"]}
  {...register("datalist")}
/>
```

```javascript
<Button type="submit" disabled={isSubmitting}>
  {isSubmitting ? "Loading..." : "Submit"}
</Button>
```

## 7. Timing Events

```javascript
const timer = setTimeout(callback_function, delay);
return () => clearTimeout(timer);

const interval = setInterval(callback_function, delay);
clearInterval(interval);
```

## 8. Array methods - find, some, every, includes, map, filter, reduce

```
.filter() is great when you have multiple selections and want the array of full objects.
.find() works best when you’re looking for one specific item.

.some() tests whether at least one element in the array passes the test (returns true/ false)
.every() tests whether all elements in the array pass the test (returns true/ false)
```

```javascript
{
  value.lenght > 0 && <Component {...props} />;
}
```

## 9. Execptional Handling with throw keyword

```javascript
try {
  throw new Error("error message");
} catch (error) {
  console.log(error.message);
} finally {
  // finally block
}
```

## 10. `useSearchParams()`

```javascript
const [searchParams, setSearchParams] = useSearchParams();

const sortValue = searchParams.get("sort") || "";
const filterValue = searchParams.get("filter") || "";
const categoryValue = searchParams.get("category") || "";

const handleSearchParamsChanges = (e) => {
  const name = e.target.name || e.currentTarget.getAttribute("data-name");
  const value = e.target.value || e.currentTarget.getAttribute("data-value");

  const existingParams = Object.fromEntries(searchParams);

  if (value) {
    existingParams[name] = value;
  } else {
    delete existingParams[name];
  }

  setSearchParams(existingParams);
};
```

```html
<select name="sort" value="{sortValue}" onChange="{handleSearchParamsChanges}">
  <option value="">Default</option>
  <option value="asc">Ascending</option>
  <option value="desc">Descending</option>
</select>

<select
  name="filter"
  value="{filterValue}"
  onChange="{handleSearchParamsChanges}"
>
  <option value="">All</option>
  <option value="price">Price</option>
  <option value="rating">Rating</option>
</select>

<p data-name="category" data-value="" onClick="{handleSearchParamsChanges}">
  Default
</p>
<p
  data-name="category"
  data-value="laptops"
  onClick="{handleSearchParamsChanges}"
>
  Laptop
</p>
<p
  data-name="category"
  data-value="smartphones"
  onClick="{handleSearchParamsChanges}"
>
  Smart Phones
</p>
```

### `useParams()`

```javascript
const { id } = useParams();
```

## 11. ReactQuery

### `get` request

```javascript
const { data, isPending, isError, errors, refetch } = useQuery({
  queryKey: ["posts", sortValue, filterValue],
  queryFn: async () => {
    const response = await axios.get("/api/post", {
      params: { sort: sortValue, filter: filterValue },
    });
    return reponse.data;
  },
  enabled: !!(sortValue || filterValue), // The query will not execute until the sortValue or filterValue exists
});

const [{}, {}] = useQueries({ queries: [{}, {}] });

if (isPending) return <p>Loading...</p>;
if (isError) return <p>Error: {error.message}</p>;
<button onClick={() => refetch()}>Refetch Posts</button>;
```

If you're not uploading files → stick with JSON ({})

If you need to upload files → FormData

```javascript
const formData = new FormData()
formData.append("key", value)
images.forEach((image) => {
formData.append("images": image)
})
```

### `post` request

```javascript
const queryClient = useQueryClinet();

const { mutate } = useMutation({
  mutationFn: async (data) => {
    const response = await axios.post("/posts", data);

    return response.data;
  },

  onMutate: (newPost) => {
    const previousPosts = queryClient.getQueryData(["posts"]);

    queryClient.setQueryData(["posts"], (oldPosts) => [...oldPosts, newPost]);

    return { previousPosts };
  },

  onSuccess: () => {},

  onError: (error, context) => {
    queryClinet.setQueryData(["posts"], context.previousPosts);

    const errorMessage =
      error.response?.data?.message ||
      "Something went wrong. Please try again.";
  },

  onSettled: () => {
    queryClient.invalidateQueries(["posts"]);
  },
});
```

### `put` request

```javascript
onMutate: (editedData) => {
    const previousPosts = queryClient.getQueryData(["posts"]);

    queryClient.setQueryData(["posts"], (oldPosts) =>
      oldPosts.map((post) =>
        post.id === editedData.id ? { ...post, ...editedData } : post
      )
    );

    return { previousPosts };
  },
```

### `delete` request

```javascript
onMutate: (postId) => {
  const previousPosts = queryClient.getQueryData(["posts"]);

  queryClient.setQueryData(["posts"], (oldPosts) => {
    oldPosts.filter((oldPost) => oldpost.id !== postId);
  });

  return { previousPosts };
};
```
