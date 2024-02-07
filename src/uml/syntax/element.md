# 元素

元素是活动界面中的可视或可交互的对象, 定义方式如下: 

```js
type(attr1: value1, attr2: value2, ...) { Hello! }
```

其中, `type` 为元素的类型, `attrN` 和 `valueN` 分别为属性名称和属性值. 不同类型的元素的属性也各不相同, 其中一些是必填, 会在介绍元素时具体标注. 

元素的 `id` 属性为所有元素共有的可选属性, 在元素被定义后, 其 `id` 属性将自动对应一个表示该元素绘制范围的 `Rect` 变量. 

后面的 `{ Hello }` 是可选内容, 代表该元素的文字内容. 只对 `p`(段落元素)生效. 

下面逐个介绍各类型的元素: 

## 段落元素 `p`

```js
p(id, x, y, ax, ay, size, ml, mw, bl, c)
```

- `id`(选填): 元素 ID
- `x`(选填, 默认为 `0`): 文本 `x` 坐标
- `y`(选填, 默认为 `0`): 文本 `y` 坐标
- `ax`(选填, 默认为 `0`): 文本横向对齐, `[0, 1]` 间的浮点数. 为 `0` 时, 按照 `x` 坐标左对齐, 为 `1` 时右对齐, `0.5` 时居中
- `ay`(选填, 默认为 `0`): 文本纵向对齐, 具体意义同上
- `size`(选填, 默认为 `1`): 文本大小
- `ml`(选填, 默认为 `false`): 文本是否多行渲染, 只在设置了 `mw` 的条件下有效
- `mw`(选填): 文本最大宽度. 在单行模式下, 超出范围的文本将被省略；多行模式下将自动换行
- `bl`(选填, 默认为 `true`): 纵向对齐时是否按照基准线对齐
- `c`(选填, 默认为 `"white"`): 文本颜色

## 图片元素 `img`

```js
img(id, url, r, c, t)
```

- `id`(选填): 元素 ID
- `url`(必填): 图片 URL, 用双引号括起来
- `r`(必填): 图片显示的位置矩形, 类型为 `Rect`
- `c`(选填, 默认为 `"white"`): 在图片上叠加的颜色. 若颜色半透明, 图片也会半透明
- `t`(选填, 默认为 `cropCenter`): 图片的裁剪方式. 可选值有: 
  - `cropCenter`: 从图片中心裁剪
  - `inside`: 保持图片比例, 使图片完全显示在 `r` 中
  - `fit`: 拉伸为 `r` 的大小

## 谱面合集元素 `col`
  
```js
col(id, cid, r, rn, rh)
```

- `id`(选填): 元素 ID
- `cid`(必填): 谱面合集 ID
- `r`(必填): 谱面合集显示的位置矩形, 类型为 `Rect`
- `rn`(选填, 默认为 `4`): 一行显示的谱面数
- `rh`(选填, 默认为 `0.3`): 谱面高度

## 按钮元素 `btn`

```js
btn(id, r, action)
```

- `id`(选填): 元素 ID
- `r`(必填): 按钮显示的位置矩形, 类型为 `Rect`
- `action`(选填): 按钮的点击行为, 可用的值参见数据类型一节

在元素被定义后, 其 `id` 属性除了表示该元素绘制范围的 `Rect` 变量, 还具有以下属性: 

- `id.pressing`: 按钮是否正在被按下, 被按下时值为 `1`, 否则为 `0`
- `id.last`: 按钮上次被按下的时刻, 从未被按下时值为 `-1`
- `id.count`: 按钮被按下的次数