
# `Inline`

```js
import { Inline } from 'slate'
```

Slate [`Document`](./Document.md) Inline 节点实现了 [`Node`](./Node.md) 接口。

Block 节点可以包含嵌套的 inline 节点以及 text 节点——就像 DOM 一样。它始终包含至少一个 text 节点作为子节点。

- [属性](#属性)
  - [`data`](#data)
  - [`isVoid`](#isvoid)
  - [`key`](#key)
  - [`nodes`](#nodes)
  - [`type`](#type)
- [计算属性](#计算属性)
  - [`kind`](#kind)
  - [`text`](#text)
- [静态方法](#静态方法)
  - [`create`](#create)
  - [`createList`](#createList)
  - [`fromJSON`](#fromJSON)
  - [`isInline`](#isInline)
  - [`isInlineList`](#isInlineList)
- [实例方法](#实例方法)
  - [`toJSON`](#toJSON)
  - [`toJS`](#toJS)


## Properties

```js
Inline({
  data: Data,
  isVoid: Boolean,
  key: String,
  nodes: Immutable.List<Node>,
  type: String
})
```

### `data`
`Immutable.Map`

与节点相关的任意数据。默认为一个空 `Map`。

### `isVoid`
`Boolean`

节点是否为 "void"，这意味着其没有子内容（如 emoji 表情、图标等）。默认为 `false`。

注意即便节点为 "void"，它仍然会包含一个空的 [`Text`](./text.md) 节点以保证适配其它操作的一致性。不过，在 Slate 渲染时这个 [`Text`](./text.md) 节点是不可见的。

### `key`
`String`

节点的唯一标识。

### `nodes`
`Immutable.List`

子节点列表。默认为包含单一文本节点的列表。

### `type`
`String`

节点的自定义类型（如 `link` 或 `hashtag`）。


## 计算属性
### `object`
`String`

不可变的 String，值为 `'inline'` 以便于将这类节点与 [`Block`](./Block.md) 和 [`Text`](./Text.md) 节点区分开。


### ~~`kind`~~ 废弃
`String`

不可变的 String，值为 `'inline'` 以便于将这类节点与 [`Block`](./Block.md) 和 [`Text`](./Text.md) 节点区分开。

### `text`
`String`

该节点的所有子 [`Text`](./Text.md) 节点内容拼接成的字符串。


## 静态方法

### `create`
`create(properties: Object) => Inline`

由原生 JS `properties` 对象创建一个 inline。

### `createList`
`createList(elements: Array<Any> | List<Any>) => List`

由原生 JS `array` 数组 或者 `List` 创建一个 inline 的 `List`。

### `fromJSON`
`fromJSON(object: Object) => Inline`

由 JSON `object` 创建一个 inline。

### `fromJS`
`alias fromJSON`

### `isInline`
`isInline(maybeInline: Any) => Boolean`

返回传入的参数是否为 `Inline`。

### `isInlineList`
`isInlineList(elements: Any) => Boolean`

返回传入的参数是否为多个 `Inline` 节点组成的 `List`。


## 实例方法

### `toJSON`
`toJSON() => Object`

返回 inline 的 JSON 表示。

### `toJS`
`alias toJS`

### `isEmpty`
isEmpty() => Boolean

是否是空节点。
