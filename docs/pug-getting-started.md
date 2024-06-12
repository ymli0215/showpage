# 使用說明

1. 新增樣版檔
   - 樣版檔放至 `.vscode/coder-template` 目錄，附檔名為 `*.md`
   - 支援多種樣版檔，每次執行時都可以決定使用的樣版
2. 執行
   - 選取 pug 檔案，並執行 `AutoCoder-pug`，
   - 自動套用： 當樣版或 pug 檔異動，會自動進行套版

## Pug 檔範例

以下範例會在同目錄輸出 home / confirm / result 三個檔案

```pug
htwqu002-home(layout=query01, title=abcd, name=DDDD)
  head
    title Home11
  body
    h1 Hello, World!
    p
      span Span Content1
      span Span Content2
htwqu002-confirm(layout=query01, title=abcd, name=DDDD)
  head
    title Confirm1
  body
    h1 Hello, World!
    p
      span Span Content1
      span Span Content2
htwqu002-result(layout=query01, title=abcd, name=DDDD)
  head
    title Result1
  body
    h1 Hello, World!
    p
      span Span Content1
      span Span Content2
```

## 樣版範例

版檔內容如下，以 `p`的樣版為例，樣版內容是下面使用[handlebars](https://handlebarsjs.com/)描述

    ### Base

    - DEFAULT

    ```xml
    <DEFAULT
        {{#if style}} style="{{style}}" {{/if}}
        {{#if class}} class="{{class}}" {{/if}}
        {{#if id}} id="{{id}}" {{/if}}
        {{#if name}} name="{{name}}" {{/if}}
        {{#if type}} type="{{type}}" {{/if}}
        {{#if value}} value="{{value}}" {{/if}}
        {{#if placeholder}} placeholder="{{placeholder}}" {{/if}}
        {{#if required}} required {{/if}}
        {{#if disabled}} disabled {{/if}}
        {{#if readonly}} readonly {{/if}}
        {{#if checked}} checked {{/if}}
    >
    {{CONTENT}}
    </DEFAULT>
    ```

    ### Component


    ### Layout

    - query01

    ```xml
    <template>
    {{CONTENT}}
    </template>

    <script setup lang='ts'>
    </script>

    <style scoped lang='scss'></style>
    ```

---

結束位置

## 異動歷程

- 2024/05/21 新增多行處理與多檔案類型
  以下內容中的 `fileType`允許輸出到不檔案類型，另外，內文如有需要輸出多行時可以在 tag 後面加上`.`，就可以輸出多行的資訊，以下方 `p.` 的定義，就會就會合併輸出 Content1~3

```pug
page1(fileType=vue, layout=query01, title=abcd, name=DDDD)
  head
    title Pug Parser Example
  body
    h1 Hello, World!
    p.
      Span Content1
      Span Content1

      Span Content2
      Span Content3
```

輸出結果

```html
<template>
  head title Pug Parser Example body h1 Hello, World! p. Span Content1 Span
  Content2 Span Content3 Span Content4 Span Content5
</template>

<script setup lang="ts"></script>

<style scoped lang="scss"></style>
```
