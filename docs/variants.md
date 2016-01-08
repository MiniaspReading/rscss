# Variants

Components may have variants. Elements may have variants, too.<br>
元件可以有多種變數，元素當然以可以。

![](images/component-modifiers.png)

<br>

## Naming variants變數的命名
Classnames for variants will be prefixed by a dash (`-`).<br>
變數名稱前須加上減號(-)作為前綴詞

  ```scss
  .like-button {
    &.-wide { /* ... */ }
    &.-short { /* ... */ }
    &.-disabled { /* ... */ }
  }
  ```

## Element variants元素變數
Elements may also have variants.<br>
元素也可以有變數

  ```scss
  .shopping-card {
    > .title { /* ... */ }
    > .title.-small { /* ... */ }
  }
  ```

## Dash prefixes 減號前綴詞
Dashes are the preferred prefix for variants.<br>
變數的最佳前綴詞非減號(-)莫屬

  * It prevents ambiguity with elements.
  * A CSS class can only start with a letter, `_` or `-`.(CSS的class可以 "_" 或 "-"" 符號作為開頭)
  * Dashes are easier to type than underscores.( "-" 比 "_" 更容易輸入)
  * It kind of resembles switches in UNIX commands (`gcc -O2 -Wall -emit-last`).

How do you deal with complex elements? Nest them.<br>
遇到複雜的元素該如何處理呢?將它們巢狀化吧！
[Continue →](nested-components.md)
<!-- {p:.pull-box} -->
