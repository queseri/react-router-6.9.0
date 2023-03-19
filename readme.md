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

## Nested Routes

- when a component should render inside another component (child component). That is a child of the main component,
- the above code is adjusted as follows. Take note of the `children` route inside the object.

```jsx
const router = createBrowserRouter([
  {
    path: "/",
    element: <Root />,
    errorElement: <ErrorPage />,
    children: [
      {
        path: "contacts/:contactId",
        element: <Contact />,
      },
    ],
  },
]);
```

-  lastly we need to indicate where the child component should be rendered in the parent element. That is done by importing
`import { Outlet } from "react-router-dom";` in the parent element and placing the `Outlet` at the position where the child 
component should be rendered.

```jsx
// src/routes/root.jsx
 import { Outlet } from "react-router-dom";

export default function Root() {
  return (
    <>
      {/* all the other elements */}
      <div id="detail">
        <Outlet />
      </div>
    </>
  );
}
```

## client side routing
- using the anchor element `a` causes the browser to do a full document request for the next URL instead of using React Router.
Client side routing allows our app to update the URL without requesting another document from the server. Instead, the app can immediately render new UI.
That can be done using the `Link` element.
