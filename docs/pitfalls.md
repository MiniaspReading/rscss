# Pitfalls 注意陷阱

## Bleeding through nested components 在嵌入的套件屬性外流
Be careful about nested components with elements sharing the same name as elements in its container. 關於嵌入的套件底下有共用元素命名的情況要小心。

```html
<article class='article-link'>
 <div class='vote-box'>
    <button class='up'></button>
    <button class='down'></button>
    <span class='count'>4</span>
  </div>

  <h3 class='title'>Article title</h3>
  <p class='count'>3 votes</p>
</article>
```

```scss
.article-link {
  > .title { /* ... */ }
  > .count { /* ... (!!!) */ }
}

.vote-box {
  > .up { /* ... */ }
  > .down { /* ... */ }
  > .count { /* ... */ }
}
```

In this case, if `.article-link > .count` did not have the `>` (child) selector, it will also apply to the `.vote-box .count` element. This is one of the reasons why child selectors are preferred. <br>
在這個例子中，如果 `.article-link > .count` 沒有 `>` 連接(子)選擇器的話，它也會套用到 `.vote-box .count` 元素。這也是為何較傾向使用子選擇器的原因之一。
