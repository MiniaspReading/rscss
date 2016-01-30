# 巢狀元件(Nested components)

![](images/component-nesting.png)

```html
<div class='article-link'>
  <div class='vote-box'>
    ...
  </div>
  <h3 class='title'>...</h3>
  <p class='meta'>...</p>
</div>
```

Sometimes it's necessary to nest components. Here are some guidelines for doing that. <br>
有時候巢狀結構的元件是必要的。這裡有一些小技巧需要知道。

## Variants 變形
A component may need to appear a certain way when nested in another component. Avoid modifying the nested component by reaching into it from the containing component. <br>
當一個元件嵌在另一個元件中時，需要一個較明確的方法區隔開來。避免直接透過元件所包含的小元件來進行修改。


```scss
.article-header {
  > .vote-box > .up { /* ✗ avoid this */ }
}
```

  Instead, prefer to add a variant to the nested component and apply it from the containing component. 相反的，較傾向在元件中所包含嵌入的目標元件加入變形並套用。

```html
<div class='article-header'>
  <div class='vote-box -highlight'>
    ...
  </div>
  ...
</div>
```

```scss
.vote-box {
  &.-highlight > .up { /* ... */ }
}
```

## 簡化巢狀式元件
Sometimes, when nesting components, your markup can get dirty:<br>
有時候當嵌入元件時，你 class 看起來像下面一樣，會變的很雜亂：

```html
<div class='search-form'>
  <input class='input' type='text'>
  <button class='search-button -red -large'></button>
</div>
```

You can simplify this by using your CSS preprocessor's `@extend` mechanism: <br>
你可以利用 CSS 預處理的其中一項功能 `@extend` 來進行簡化的動作。

```html
<div class='search-form'>
  <input class='input' type='text'>
  <button class='submit'></button>
</div>
```

```scss
.search-form {
  > .submit {
    @extend .search-button;
    @extend .search-button.-red;
    @extend .search-button.-large;
  }
}
```

What about repeating elements like lists? Learn about Layouts. <br>
那關於重複性較高的元素，像是清單(list)，要怎麼處理呢？我們來看一下 Layouts 版面佈局的部分。
[Continue 繼續 →](layouts.md)
<!-- {p:.pull-box} -->
