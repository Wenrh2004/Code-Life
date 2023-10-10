# 如何做API测试？ 怎么测试自己的代码对不对？

## 1. 首先了解一个概念，作为后端开发我们，我们如何和前端交谈

> 假设一个场景，前端小朋友是个文科生，现在它遇到了一件文物，需要判断这件文物的年代，but文科小朋友不会$C^{14}$同位素标记技术，因此need一个理科的朋友也就是后端小盆友来帮助它判断文物年代。所以它带着文物来找后端小盆友，希望通过后端的方法来得到想要的答案。所以前端小朋友写了一封信，寄到了后端小朋友这里。
>
> > 其中，
> >
> > * 信的邮寄方式就相当于我们常见的 HTTP 请求方法，常用的有 POST、GET、PUT等
> > * 信上的邮寄地址中的街道就相当于我们的请求路径中的 Host
> > * 信上的邮寄地址中的门牌号就相当于我们请求路径中的 Port
> > * 而信的内容呢就相当于我们前后端常见的 JSON 文件
>
> 然后我们继续往后讲，前端小朋友和后端小朋友的专业素养都非常高，可是写起信来呢，因为双方的专业不同，又看不懂对方的专业术语，因此我们想到了一个方法，就是在专业术语前面前后端小朋友用大白话来告诉对方这是用来干什么的，因此，我们又可以向后引申了。
>
> > 在信中，
> >
> > * 通俗的大白话，就是 JSON 文件中的前半段，作用就相当于数据的身份标识
> >
> > * 专业术语，就是 JSON 文件中的后半段，作用就是专业表述
> >
> >   p.s. 这个表述并不正确，但是希望能够帮助刚接触开发的小伙伴快速上手，只能退而求其次了。

**下面，我们要严肃起来了！**

>  # JSON
>
> *JavaScript Object Notation* (**JSON**) 是一种数据交换格式。尽管不是严格意义上的子集，JSON 非常接近 [JavaScript](https://developer.mozilla.org/zh-CN/docs/Glossary/JavaScript) 语法的子集。
>
> 许多编程语言都支持 JSON，尤其是 JavaScript，它在网站和浏览器扩展应用广泛。
>
> JSON 可以表示数字、布尔值、字符串、`null`、数组（有序序列），以及由这些值组成的对象（字符串与值的映射）。JSON 不支持复杂的数据类型（函数、正则表达式、日期等）。日期对象默认会转化为 ISO 格式的字符串，因此信息不会完全丢失。
>
> > * 如果你需要使用 JSON 来表示复杂的数据类型，请在它们转化为字符串值。
> >
> > * 与 XML 非常相似，JSON 能存储 CSV 格式，同时保留它的分级信息。有许多工具能帮助你进行格式转换（例如 [JSON to CSV Converter](https://json-csv.com/) 或[JSON to CSV Converter](https://jsontoexcel.com/)）。
>
> JSON 可以作为一个对象或者字符串存在，前者用于解读 JSON 中的数据，后者用于通过网络传输 JSON 数据。这不是一个大事件——JavaScript 提供一个全局的 可访问的 [JSON](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/JSON) 对象来对这两种数据进行转换。
>
> **备注：** 将字符串转换为原生对象称为*反序列化*（deserialization），而将原生对象转换为可以通过网络传输的字符串称为*序列化*（serialization）。
>
> 一个 JSON 对象可以被储存在它自己的文件中，这基本上就是一个文本文件，扩展名为 `.json`，还有 `application/json` [MIME 类型](https://developer.mozilla.org/zh-CN/docs/Glossary/MIME_type)。
>
> ### [JSON 结构](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Objects/JSON#json_结构)
>
> 如上所述，JSON 是一个字符串，其格式非常类似于 JavaScript 对象字面量的格式。你可以在 JSON 中包含与标准 JavaScript 对象相同的基本数据类型——字符串、数字、数组、布尔值和其他对象字面量。这使你可以构建一个数据层次结构，如下所示：
>
> JSONCopy to Clipboard
>
> ```
> {
>   "squadName": "Super hero squad",
>   "homeTown": "Metro City",
>   "formed": 2016,
>   "secretBase": "Super tower",
>   "active": true,
>   "members": [
>     {
>       "name": "Molecule Man",
>       "age": 29,
>       "secretIdentity": "Dan Jukes",
>       "powers": ["Radiation resistance", "Turning tiny", "Radiation blast"]
>     },
>     {
>       "name": "Madame Uppercut",
>       "age": 39,
>       "secretIdentity": "Jane Wilson",
>       "powers": [
>         "Million tonne punch",
>         "Damage resistance",
>         "Superhuman reflexes"
>       ]
>     },
>     {
>       "name": "Eternal Flame",
>       "age": 1000000,
>       "secretIdentity": "Unknown",
>       "powers": [
>         "Immortality",
>         "Heat Immunity",
>         "Inferno",
>         "Teleportation",
>         "Interdimensional travel"
>       ]
>     }
>   ]
> }
> ```
>
> 如果我们把字符串加载到 JavaScript 程序中，并将其解析到一个名为 `superHeroes` 的变量，那么我们就可以使用在 [JavaScript 对象基础](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Objects/Basics)文章中相同的点/括号表示法来访问其中的数据。例如：
>
> JSCopy to Clipboard
>
> ```
> superHeroes.hometown;
> superHeroes["active"];
> ```
>
> 为了访问层次结构中更深层次的数据，必须将所需的属性名和数组索引链接在一起。例如，访问 members 数组第二个英雄的第三个超能力，可以这样做：
>
> JSCopy to Clipboard
>
> ```
> superHeroes["members"][1]["powers"][2];
> ```
>
> 1. 首先我们有变量名 `superHeroes`，储存对象。
> 2. 在对象中我们想访问 `members` 属性，所以我们使用 `["members"]`。
> 3. `members` 包含有对象数组，我们想要访问第二个元素，所以我们使用 `[1]`。
> 4. 在对象内，我们想访问 `powers` 属性，所以我们使用 `["powers"]`。
> 5. `powers` 属性是一个包含英雄技能的数组。我们想要第三个，所以我们使用 `[2]`。
>
> **备注：** 我们已经在 [JSONText.html](https://mdn.github.io/learning-area/javascript/oojs/json/JSONTest.html) 实例中让 JSON 对象进入变量中使其可访问（见[源代码](https://github.com/mdn/learning-area/blob/main/javascript/oojs/json/JSONTest.html)）。尝试加载它并且在你的浏览器上访问对象数据。
>
> ### [JSON 数组](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Objects/JSON#json_数组)
>
> 前面我们提到，JSON 文本基本上看起来像字符串中的 JavaScript 对象。我们也可以将数组与 JSON 相互转换。下面也是有效的 JSON，例如：
>
> JSONCopy to Clipboard
>
> ```
> [
>   {
>     "name": "Molecule Man",
>     "age": 29,
>     "secretIdentity": "Dan Jukes",
>     "powers": ["Radiation resistance", "Turning tiny", "Radiation blast"]
>   },
>   {
>     "name": "Madame Uppercut",
>     "age": 39,
>     "secretIdentity": "Jane Wilson",
>     "powers": [
>       "Million tonne punch",
>       "Damage resistance",
>       "Superhuman reflexes"
>     ]
>   }
> ]
> ```
>
> 上面是完全合法的 JSON。你只需要通过数组索引就可以访问数组元素，如 `[0]["powers"][0]`。
>
> ### [其他注意事项](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Objects/JSON#其他注意事项)
>
> - JSON 是一种纯数据格式，它只包含属性，没有方法。
> - JSON 要求在字符串和属性名称周围使用双引号。单引号无效。
> - 甚至一个错位的逗号或分号就可以导致 JSON 文件出错。你应该小心的检查你想使用的数据（虽然计算机生成的 JSON 很少出错，只要生成程序正常工作）。你可以通过像 [JSONLint](https://jsonlint.com/) 这样的应用程序来验证 JSON。
> - JSON 实际上可以是任何可以有效包含在 JSON 中的数据类型的形式。比如，单个字符串或者数字就是有效的 JSON 对象。
> - 与 JavaScript 代码中对象属性可以不加引号不同，JSON 中只有带引号的字符串可以用作属性。

## 2. API POST 工具帮我们更方便的验证自己的代码是否正确

通常，在开发过程中，我们会给出完整的**API 测试文档**（简称**API 文档**）以及**API 接口示例**用来规范我们的**API设计**、**数据规范**以及方便我们的**项目开发**与**功能测试**，我们可以通过 **POSTMAN** 工具快捷的测试我们的 **API** 是否符合需求，根据 **API测试**的结果来了解我们的代码是否能够满足需求。

## 3. 如何根据 API POST 工具帮我们纠正代码逻辑

1. 根据 **API测试** 的结果分析与目标结果不匹配的地方，进而快速定位至代码逻辑问题的大致范围。

   >  e.g. 我们在登陆功能中，如果遇到了没有返回为空，而且程序未报错的情况，代码的逻辑错误出现在何处呢？
   >
   > 1. 最容易忽视的**前置条件**，我们的测试数据 **is true**
   > 2. 没有报错与返回
   > 3. 所以大致可以定位到正确结果返回的地方啦

2. 根据 **API测试** 的结果分析代码逻辑错误

   > 根据测试结果的错误返回，我们可以快速的定位到有代码逻辑错误的代码片段。及根据返回的错误信息，寻找代码中返回该条错误信息的片段即可。