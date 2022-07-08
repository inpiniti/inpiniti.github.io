---
title: 11 React Router
author: 최유진
date: 2022-07-11
category: 04 react
layout: post
---

# React 스터디 5차 - React Router

## 개요
### 1. react-router-dom 설치 및 세팅
### 2. Route
### 3. Redirect
### 4. Switch
### 5. Link, NavLink
### 6. Hooks
---
> 리액트 라우터 v5 공식문서 <br> https://v5.reactrouter.com/web/guides/quick-start
---
# **1. react-router-dom 설치 및 세팅**
- ### 리액트 라우터를 사용하기 위해 라이브러리 설치
```bash
npm install react-router-dom
yarn add react-router-dom
```
- ### 최상단 컴포넌트를 BrowserRouter로 감싸기
  - BrowserRouter : HTML5의 history API를 활용하여 UI 업데이트
  - HashRouter : URL의 해시를 활용한 라우터
```jsx
// index.js
import React from 'react';
import { BrowserRouter } from 'react-router-dom';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```
- ### `basename`: string
  - 모든 라우터의 base URL을 지정함
```jsx
<BrowserRouter basename="/calendar">
  <Link to="/today"/> // <a href="/calendar/today">
  <Link to="/tomorrow"/> // <a href="/calendar/tomorrow">
  ...
</BrowserRouter>
```
- ### `getUserConfirmation`: function
  - window confirm 메세지를 띄우고 창을 전환할 때 사용
```jsx
<BrowserRouter
  getUserConfirmation={(message, callback) => {
    const allowTransition = window.confirm(message);
    callback(allowTransition);
  }}
>
</BrowserRouter>
```
- ### `forceRefresh`: boolean
  - true 값을 줄 시 페이지 라우팅 시 전체 페이지가 리로딩 됨
```jsx
<BrowserRouter forceRefresh={true} />
```
---  
# **2. Route**
- ### 요청 경로에 렌더링 할 컴포넌트 연결
```jsx
import React from 'react';
import { Route } from 'react-router-dom';
import About from './About';
import Home from './Home';

const App = () => {
  return (
    <div>
      <Route path="/" exact={true} component={Home} />
      <Route path="/about" component={About} />
      <Route path="/Home"><Home/></Route>
    </div>
  );
};
```
- `path`: string
  - 라우팅 할 주소
  - `*` 를 넣어줄 경우 여러 경로가 매칭 됨
```jsx
// 'baseUrl/category/~' 
<Route path="/category/*" component={Category} />
```
- `component`: React.Component
  - 라우팅 할 주소에 연결될 컴포넌트
- `exact`: boolean
  - path가 정확히 일치할 때만 렌더링 되도록 함
```jsx
// exact를 설정하지 않은 경우
// '/' 주소로 이동 시 Home 과 About 이 모두 렌더링 됨
<Route path="/" component={Home} />
<Route path="/about" component={About} />
```

- ### 라우팅 된 컴포넌트에서는 props로 Route 속성 접근 가능
```jsx
// App.jsx
import { Route } from 'react-router-dom';
import { Product } from './Product';

const App = () => {
  ...
  return () {
    ...
    <Route path='/product/:category_id/:product_id' component={Product} />
    ...
  }
}
```
```jsx
// Product.jsx
import { Route } from 'react-router-dom';

const Product = (props) => {
  /*
  props = {
    history: {...},
    location: {...},
    match: {...},
    ...
  }
  */
  const { params, path } = props.match;
  const categoryId = params.category_id;
  const productId = params.product_id;
  ...
  return () {
    ...
    <Route path={`${path}/new-path`} component={Product} />
    ...
  }
}
```
---
# **3. Redirect**
- ### 요청 라우팅 주소를 다른 경로로 리다이렉션 함
```jsx
<Redirect from="/old-path" to="/new-path" />
```
- `from`: string - 이전 주소
- `to`: string - 리다이렉션 할 새 주소

```jsx
// loggedIn = true : /dashboard 경로로 리다이렉션
// loggedIn = false : PublicHomePage 렌더링
<Route exact path="/">
  {loggedIn ? <Redirect to="/dashboard" /> : <PublicHomePage />}
</Route>
```
---
# **4. Switch**
- ### `Route` 또는 `Redirect` 중에서 라우팅 주소와 일치하는 첫 번째 컴포넌트만을 렌더링 함
- ### v6에서 `Routes` 로 변경됨
```jsx
<Switch>
  <Route path="/" exact component={Home} />
  <Route path="/about" component={About} />
  <Route path="/profile" component={Profile} />
  <Redirect path="*" to="/" />
</Switch>
```
---
# **5. Link, NavLink**
## **Link**
- ### 클릭 시 브라우저 주소 변경
- ### <b><u>`Link`는 브라우저의 주소만 바꾸고 페이지를 새로 불러오지 않음</u></b>
  - 리액트 사용 시 `a` 태그 대신 `Link`를 사용해야 함

```jsx
import React from 'react';
import { Route, Switch, Link, Redirect } from 'react-router-dom';
import Home from './Home';
import About from './About';
import Dashboard from './Dashboard';

const App = () => {
  return (
    <div>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
        <Link to="/dashboard">Dashboard</Link>
      </nav>

      <Switch>
        <Route path="/" exact component={Home} />
        <Route path="/about" component={About} />
        <Route path="/dashboard" component={Dashboard} />
        <Redirect path="*" to="/" />
      </Switch>
    </div>
  );
};

export default App
```
## **NavLink**
- ### 스타일 속성이 추가된 `Link`
- ### 현재 주소와 일치하는 `NavLink`에 `active` 클래스가 부여됨
```jsx
// App.jsx
<nav>
  <NavLink exact to="/">Home</NavLink>
  <NavLink to="/about">About</NavLink>
  <NavLink to="/dashboard">Dashboard</NavLink>
</nav>
```
```jsx
// Home 클릭 시 실제로 DOM에 그려지는 엘리먼트
<a href="/" class="active">Home</a>
<a href="/about">About</a>
<a href="/dashboard">Dashboard</a>
```
--- 
# **6. Hooks**
## **1) useHistory()**
- ### DOM의 `history` 객체에 접근할수 있음
```jsx
import { useHistory } from "react-router-dom";

const HomeButton = () => {
  const history = useHistory();

  const handleClick = () => {
    history.push("/home");
  }

  return (
    <button type="button" onClick={handleClick}>
      Go home
    </button>
  );
}
```

## **2) useLocation()**
- ### 호출 시 현재 URL 정보를 담은 `location` 객체를 반환함
```jsx
import { useLocation } from "react-router-dom";

const HomeButton = () => {
  const location = useLocation();
  ...
}
```
## **3) useParams()**
- ### URL 파라미터 값을 반환함
```jsx
<Route path="/dashboard/:id" component={Dashboard} />
```
```jsx
// '/dashboard/23' 주소로 접속 시
import { useParams } from 'react-router-dom';

const params = useParams(); // params = { id: 23 }
const { id } = useParams();
```
---