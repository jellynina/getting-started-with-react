### Tuts+ Course: Getting Started With React.js
**Instructor: David East**

React is a view library whose philosophy greatly differs from the usual framework. This course will cover what makes React different from all the other frameworks and libraries out there.

Source files for the Tuts+ course: [Getting Started With React.js](https://courses.tutsplus.com/courses/)

**Available on Tuts+ November 2014**

# Learnig Notes

## Why React

view only

### Virtual DOM

* Independent of Browser
* Compares changes only applies to the difference

# Template vs Components

template比較複雜，如AngularJS. 我不知道為啥

component 不是用render來的，是先定義出來的

## JAX

套用：

```html
<script src="http://fb.me/react-0.11.1.js"></script>
<script src="http://fb.me/JSXTransformer-0.11.1.js"></script>
```

### 定義一個componet:

```js
    var MessageBox = React.createClass({
      render: function() {
        return (
          <h1 className>Hello, World</h1>
        );
      }
    });
```

> 注意：`return`只能一個元件，若要多個物件就需要包在一個`<div>`當中
> 而且如果沒有`()`全都都必須寫在同一行

### Render Components

`React.renderComponent();`

```js
React.renderComponent(
  <MessageBox />,
  document.getElementById('app'),
  function () {
    console.log('after render');
  }
)
```

2015.11.05: 上完2-2













