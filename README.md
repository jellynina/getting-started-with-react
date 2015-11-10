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


# States Managing

1. State overview
2. What kind of data do we store in state
3. Reconciliation
4. Never call state

>**Note**: 只改變`state`變數，是不會re-render的

```js
  var MessageBox = React.createClass({

    getInitialState: function () {
      return {
        isVisible: true,
        titleMessage: 'Hello, World'
      }
    },

    render: function() {

      var inlineStyle = {
        display: this.state.isVisible ? 'block' : 'none'
      };

      return (
        <div className="container jumbotron" style={inlineStyle}>
          <h2>{ this.state.titleMessage }</h2>

          <SubMessage />
        </div>
      );
    }
  });
```

啟動rerendering:`reactComponent`.


```js
reactComponent.setState({
  isVisible: false
});

// 這邊啟動setState都是在瀏覽器console裡面
```

# props

跟states一樣，套入了state machine 的概念

* `2.4` files
* `MessageBox` is the owner of `SubMessage`

> 這一節看不懂

使用`map`製作message替換

```js
  var messages = this.state.messages.map(function(message) {
    return <SubMessage message={message} />
  });
```


執行替換：create new array for 

```js

var newMessagesArray =reactComponent.state.messages.concat("New Item!");
// 在原有的message陣列再加上一個"New Item!"項目

reactComponent.setState({
  messages: newMessagesArray
  });


```


# Events

> 2.5-events

```js
return (
  <div className="container jumbotron" style={inlineStyles}>
    <h2>Hello, World</h2>
    <button onClick={this.handleAdd} className="btn btn-primary">Add</button>
    { messages }
  </div>
);
```

注意在`jsx`中attribute都是用`camelcase`

這邊說`onClick`不是真的放在`<button>`上面**（？）**

然後他們符合w3c的標準

> 我這邊真的聽不太懂


```js
    handleAdd: function(e) {
      console.log(e); //Synthetic Events
      console.log(e.target); // console 這個button物件
      console.log(this); // constructor
    },
```




# Using Refs

因為`React`做出來的都只是blueprints, 不是真的DOM node. 所以要抓取數值的時候

```js
return (
  <div className="container jumbotron" style={inlineStyles}>
    <h2>Hello, World</h2>
    <div className="form-group">
      <input ref="newMessage" type="text" className="form-control" />
      <button onClick={this.handleAdd} className="btn btn-primary">Add</button>
    </div>
    { messages }
  </div>
);
```


```js
<input ref="newMessage" type="text" className="form-control" />
```

先設定`ref="newMessage"`
然後在handleA

```js
handleAdd: function(e) {
  console.log(this);
  var newMessage = this.refs.newMessage.getDOMNode().value;
  var newMessages = this.state.messages.concat([newMessage]);
  this.setState({
    messages: newMessages
  });
},
```



