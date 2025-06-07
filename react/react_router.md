# React Router

This is a library that manages client side routing in React applications.

For example, in this application you setup different routes within the SPA.

Route - Mapping between URL and a component.

Router - Provides the routing infrastructure.

You can add it to your projects using this:

`npm install react-router-dom`

```ts
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";

import RegisterPage from "./pages/register";
import LoginPage from "./pages/login";
import DashboardPage from "./pages/dashboard";
import ProfilePage from "./pages/dashboard/profile";
import BooksPage from "./pages/dashboard/books";
import LandingPage from "./pages/landing";

function App() {
  console.log("App loaded");

  return (
    <Router>
      <Routes>
        <Route path="/" element={<LandingPage />} />
        <Route path="/register" element={<RegisterPage />} />
        <Route path="/login" element={<LoginPage />} />

        <Route path="/dashboard" element={<DashboardPage />} />
        <Route path="/dashboard/profile" element={<ProfilePage />} />
        <Route path="/dashboard/books" element={<BooksPage />} />
      </Routes>
    </Router>
  );
}

export default App;
```
