## npm install react-router-dom

```js
import {
BrowserRouter as Router,
Switch,
Route
} from "react-router-dom";

function App() {
  return (
    <div className="app">
      <Router>
        <Routes>
          <Route exact path="/" element={  <HomeScreen />}>
          </Route>
        </Routes>
      </Router>
    </div>
  );
}

```

👆 this is the template for route