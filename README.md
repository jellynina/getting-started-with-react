# Learn About React!

```html
<script src="bundle.js"></script>
```
會把所有的東西丟進`bundle.js`, 使用`webpack`.


安裝webpack
```
npm install webpack -g
```

執行
```
webpack -w
```


## React 組成

* render: 定義`component`長什麼樣子。

## 為什麼需要`react-dom` ?

一般`createClass`出來的`component`是在`server side`跑完的，所以是`virtual DOM`, 而用`react-dom`可以把`component`在`clinet side`出現真的DOM.


## React Router
