
# `Block`

```js
import { Block } from 'slate'
```

Slate [`Document`](./document.md) 中的块级节点。Block 节点实现了 [`Node`](./node.md) 接口。

Block 节点可以包含嵌套的 block 节点、inline 节点，以及 text 节点——就像 DOM 一样。它始终包含至少一个 text 节点作为子节点。

- [属性](#属性)
  - [`data`](#data)
  - [`isVoid`](#isvoid)
  - [`key`](#key)
  - [`nodes`](#nodes)
  - [`type`](#type)
- [计算属性](#计算属性)
  - [`object`](#object)
  - [`kind`](#kind)
  - [`text`](#text)
- [静态方法](#静态方法)
  - [`create`](#create)
  - [`createList`](#createList)
  - [`fromJSON`](#fromJSON)
  - [`fromJS`](#fromJS)
  - [`isBlock`](#isBlock)
  - [`isBlockList`](#isBlockList)
- [实例方法](#实例方法)
  - [`toJSON`](#tojson)


## 属性

```js
Block({
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

节点是否为 "void"，这意味着其没有子内容（如图片、视频等）。默认为 `false`。 

注意即便节点为 "void"，它仍然会包含一个空的 [`Text`](./text.md) 节点以保证适配其它操作的一致性。不过，在 Slate 渲染时这个 [`Text`](./text.md) 节点是不可见的。

### `key`
`String`

节点的唯一标识。

### `nodes`
`Immutable.List`

子节点列表。默认为包含单一文本节点的列表。

### `type`
`String`

节点的自定义类型（如 `blockquote` 或 `list-item`）。


## 计算属性

### `object`
`String`

不可变的 String，值为 `'block'` 以便于将这类节点与 [`Inline`](./Inline.md) 和 [`Text`](./Text.md) 节点区分开。

### ~~`kind`~~ <span></span>废弃
`String`

不可变的 String，值为 `'block'` 以便于将这类节点与 [`Inline`](./Inline.md) 和 [`Text`](./Text.md) 节点区分开。

### `text`
`String`

该节点的所有子 [`Text`](./text.md) 节点内容拼接成的字符串。


## 静态方法

### `create`
`create(properties: Object) => Block`

根据一个纯净对象或者节点类型创建 Block 节点

### `createList`
`createList(elements: Array<Any> | List<Any>) => List`

由原生 JS `array` 数组或者 `List` 创建一个 block 的 `List`。

### `fromJSON`
`fromJSON(obj: Object) => Block`

由 JSON `object` 创建一个 block。

### `isBlock`
`isBlock(maybeBlock: Any) => Boolean`

返回传入的参数是否为 `Block` 。

### `isBlockList`
`isBlockList(elements: Any) => Boolean`

返回传入的参数是否为多个 `Block` 组成的 `List`。


## 实例方法

### `toJSON`
`toJSON(options: Object) => Object`

返回 block 的 JSON 表示。

### `toJS` 
`alias toJSON`

### `isEmpty`
isEmpty() => Boolean

是否是空节点。
