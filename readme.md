# json5/json5 [![explain]][source] [![translate-svg]][translate-list]

<!-- [![size-img]][size] -->

[explain]: http://llever.com/explain.svg
[source]: https://github.com/chinanf-boy/Source-Explain
[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list
[size-img]: https://packagephobia.now.sh/badge?p=Name
[size]: https://packagephobia.now.sh/result?p=Name

「 数据交换格式(JSON5)是[JSON]的超集 」

[中文](./readme.md) | [english](https://github.com/json5/json5)

---

## 校对 ✅

<!-- doc-templite START generated -->
<!-- repo = 'json5/json5' -->
<!-- commit = '69c4a75d345a58a773148dd9c05ce74e668dc87d' -->
<!-- time = '2018-09-28' -->

| 翻译的原文 | 与日期        | 最新更新 | 更多                       |
| ---------- | ------------- | -------- | -------------------------- |
| [commit]   | ⏰ 2018-09-28 | ![last]  | [中文翻译][translate-list] |

[last]: https://img.shields.io/github/last-commit/json5/json5.svg
[commit]: https://github.com/json5/json5/tree/69c4a75d345a58a773148dd9c05ce74e668dc87d

<!-- doc-templite END generated -->

- [x] Readme
- [ ] 我在想[官方规范](https://json5.github.io/json5-spec/)要不要翻译，


### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

## 生活

[help me live , live need money 💰](https://github.com/chinanf-boy/live-need-money)

---

### 目录

<!-- START doctoc -->
<!-- END doctoc -->

# JSON5 - 人类的 JSON

[![Build Status](https://travis-ci.org/json5/json5.svg)][build status]
[![Coverage
Status](https://coveralls.io/repos/github/json5/json5/badge.svg)][coverage status]

数据交换格式(JSON5)是[JSON]的超集，旨在通过从[ECMAScript 5.1]学到的些东东，来扩展JSON语法，以减轻 JSON 的一些限制.

此 JavaScript 库是 JSON5 解析{parse}和序列化{serialization}库的官方参考实现.

[build status]: https://travis-ci.org/json5/json5
[coverage status]: https://coveralls.io/github/json5/json5
[json]: https://tools.ietf.org/html/rfc7159
[ecmascript 5.1]: https://www.ecma-international.org/ecma-262/5.1/

## 功能摘要

以下 (JSON 不支持) ECMSONcript 5.1 的功能已扩展成为 JSON5.

### 对象-Objects

- 对象 **keys** 可以是 ECMAScript 5.1 的 *[IdentifierName]*.
- 对象可以只有一个尾随逗号.

### 数组-Arrays

- 数组可以只有一个尾随逗号.

### 字符串-Strings

- 字符串可以是单引号.
- 字符串可以通过转义换行符，来跨越多行.
- 字符串可以包括字符转义.

### 数字-Numbers

- 数字可以是十六进制的.
- 数字可以有一个小数点，起头或尾随.
- 数字可以是[IEEE 754]正无穷大{+infinity},负无穷大{-infinity}和 NaN.
- 数字可以以明确的加号开头.

### 注释-Comments

- 允许单行和多行注释.

### 额外空格-White Space

- 允许使用额外的空格字符.

[identifiername]: https://www.ecma-international.org/ecma-262/5.1/#sec-7.6
[ieee 754]: http://ieeexplore.ieee.org/servlet/opac?punumber=4610933

## 简短的例子

```js
{
  // 注释
  unquoted: 'and you can quote me on that',
  singleQuotes: 'I can use "double quotes" here',
  lineBreaks: "Look, Mom! \
No \\n's!",
  hexadecimal: 0xdecaf,
  leadingDecimalPoint: .8675309, andTrailing: 8675309.,
  positiveSign: +1,
  trailingComma: 'in objects', andIn: ['arrays',],
  "backwardsCompatible": "with JSON",
}
```

## 规范

有关 JSON5 格式的详细说明,请阅读[官方规范](https://json5.github.io/json5-spec/).

## 安装

### Node.js

```sh
npm install json5
```

```js
const JSON5 = require('json5');
```

### 浏览器

```html
<script src="https://unpkg.com/json5@^2.0.0/dist/index.min.js"></script>
```

这将创造一个全局`JSON5`变量.

## API

JSON5 API 兼容[JSON API].

[json api]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON

### JSON5.parse()

解析一个 JSON5 字符串，构造由字符串描述的 JavaScript 值或对象.可以提供可选的 reviver 函数 - 可在返回结果对象之前，对其执行转换.

#### 语法参考

```js
JSON5.parse(text[, reviver])
```

#### 参数

- `text`: 要解析为 JSON5 的字符串.
- `reviver`: 若是一个函数,它规定了在返回之前，如何转换最初解析的生成值.

#### 返回值

给定 JSON5 文本的对应对象.

### JSON5.stringify()

将 JavaScript 值，转换为 JSON5 字符串,如果指定了 replacer 函数,则可以选择替换值,或者如果指定了 replacer 数组,则可选择要包括的指定属性.

#### 语法参考

``` js
JSON5.stringify(value[, replacer[, space]])
JSON5.stringify(value[, options])
```

#### 参数

- `value`:要转换为 JSON5 字符串的值.
- `replacer`:一个改变此过程行为的函数,或一个 String 和 Number 对象数组,的白名单。用于**选择/过滤**要包含在 JSON5 字符串中的值对象的属性.如果此值为 null 或未提供,则对象的所有属性都包含在生成的 JSON5 字符串中.
- `space`:一个 String 或 Number 对象,用于将空格插入输出 JSON5 字符串以实现可读性。如果这是一个数字,则表示用作空格的空格字符数;这个数字的上限为 10(如果它更大,哪该值就 10 到头)。小于 1 的值表示不应使用空格。如果这是一个字符串，则该字符串(或字符串的前 10 个字符,如果长于该字符串)会被用作空格填充。如果未提供此参数(或为 null), 则不使用空格。如果使用空格,则将在对象和数组中使用尾随逗号。
- `options`:具有以下属性的对象:
  - `replacer`:与`replacer`参数相同.
  - `space`:与`space`参数相同.
  - `quote`:一个 String,表示序列化字符串时，要使用的引号字符.

#### 返回值

表示js值的JSON5 字符串.

### Node.js 的JSON5 文件`require()`

使用 Node.js 时,您可以通过添加以下语句，让 Node `require()`JSON5 文件，正常解析.

```js
require('json5/lib/register');
```

就这样,您已经能加载 JSON5 文件， 通过Node.js 的 `require()`声明.例如:

```js
const config = require('./config.json5');
```

## CLI

由于 JSON 比 JSON5 使用得更广泛,因此该软件包包括一个用于将 JSON5 转换为 JSON ，以及验证 JSON5 文档语法的 CLI.

### 安装

```sh
npm install --global json5
```

### 用法

```sh
json5 [options] <file>
```

如果`<file>`未提供,则使用 STDIN.

#### 选项:

- `-s`,`--space`: 缩进或缩进的空格数，也可以使用Tab的`t`
- `-o`,`--out-file [file]`: 输出到指定文件,否则输出 STDOUT
- `-v`,`--validate`:验证 JSON5 ，但不输出 JSON
- `-V`,`--version`: 输出版本号
- `-h`,`--help`:输出使用信息

## 贡献

### 开发

```sh
git clone https://github.com/json5/json5
cd json5
npm install
```

在提供代码时,请编写相关测试，并运行`npm test`和`npm run lint`。在提交拉取请求之前.请使用支持的编辑器[EditorConfig](http://editorconfig.org/).

### 问题

要报告有关 JSON5 数据格式的错误或请求功能,请向[官方规范库Issue](https://github.com/json5/json5-spec)提交问题.

要报告有关 JSON5 的 JavaScript 实现的错误或请求功能,请向此存储库提交问题.

## 执照

麻省理工学院.看到[LICENSE.md](./LICENSE.md)详情.

## 里程

[Assem Kishore](https://github.com/aseemk)成立了这个项目.

[Michael Bolin](http://bolinfest.com/)单人扛鼎，并发表了一些相同的想法与**awesome**的解释和细节.推荐阅读:[JSON 改进的建议](http://bolinfest.com/essays/json.html)

[Douglas Crockford](http://www.crockford.com/)，当然他设计和构建了 JSON,但是他[JSON 网站](http://json.org/)上的状态机图，虽然听起来很俗气,但却让我们有动力和信心, 兼触手可及的，建立一个新的解析器来实现这些想法! JSON5 的原始实现也直接模仿 Doug 的开源[json_parse.js]解析器.我们非常感谢这些干净，且记录良好的代码.

[json_parse.js]: https://github.com/douglascrockford/JSON-js/blob/master/json_parse.js

[Max Nanasy](https://github.com/MaxNanasy)一直是一个早期和的积极贡献的支持者,贡献了多个补丁和想法.

[Andrew Eisenberg](https://github.com/aeisenberg)贡献了原始的`stringify`方法.

[Jordan Tucker](https://github.com/jordanbtucker)已经将 JSON5 与 ES5 更紧密地结合在一起,编写了官方 JSON5 规范,从头开始完全重写代码库,并积极维护这个项目.
