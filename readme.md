# Introduction to React-router 6.9.0

## installing using vite

- npm create vite@latest react-router-demo -- --template react

## start the project

- cd react-router-demo
- install dependencies `npm install react-router-dom localforage match-sorter sort-by`

## adding a router

- First thing to do is create a Browser Router and configure our first route. This will enable client side routing for our web app.
  The main.jsx file is the entry point. Open it up and we'll put React Router on the page. This first route is what we often call the "root route" since the rest of our routes will render inside of it. It will serve as the root layout of the UI

  `src/main.jsx`

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import { createBrowserRouter, RouterProvider } from "react-router-dom";
import "./index.css";

const router = createBrowserRouter([
  {
    path: "/",
    element: <div>Hello world!</div>,
  },
]);

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <RouterProvider router={router} />
  </React.StrictMode>
);
```
