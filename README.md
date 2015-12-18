# JSON 编辑器
https://github.com/josdejong/jsoneditor
http://jsoneditoronline.org/

Website: http://jsoneditoronline.org/
Github: https://github.com/josdejong/jsoneditor


## 描述

JSON编辑器是一个基于网络的工具来查看、编辑和格式JSON。 这模式如树有各种编辑器，代码编辑器和一个纯文本 。

编辑可以作为你自己的Web应用程序的一个组成部分。图书馆可以为 CommonJS模块，加载和模块，或作为一个JavaScript文件。

支持的浏览器：Chrome，Firefox，Safari，Opera，Internet Explorer 9.

<img alt="json editor" src="https://raw.github.com/josdejong/jsoneditor/master/misc/jsoneditor.png">

<img alt="code editor" src="https://raw.github.com/josdejong/jsoneditor/master/misc/codeeditor.png">


## 功能特色

### 树编辑

编辑、添加、移动、删除、复制字段和值。
改变的值的类型。
排序数组和对象。
彩色编码。
搜索和突出树视图中的文本。
撤消和重做所有的行动。

### 代码编辑器

格式和紧凑的JSON。
彩色编码（由ACE）。
检查JSON（由ACE）。




### 文本编辑器
- 格式和紧凑的JSON。


## Documentation

- Documentation:
  - [API](https://github.com/josdejong/jsoneditor/tree/master/docs/api.md)
  - [Usage](https://github.com/josdejong/jsoneditor/tree/master/docs/usage.md)
  - [Shortcut keys](https://github.com/josdejong/jsoneditor/tree/master/docs/shortcut_keys.md)
- [Examples](https://github.com/josdejong/jsoneditor/tree/master/examples)
- [Source](https://github.com/josdejong/jsoneditor)
- [History](https://github.com/josdejong/jsoneditor/blob/master/HISTORY.md)


## Install

with npm:

    npm install jsoneditor

with bower:

    bower install jsoneditor

download:

[http://jsoneditoronline.org/downloads/](http://jsoneditoronline.org/downloads/)


#### More

There is a directive available for using JSONEditor in Angular.js:

[https://github.com/angular-tools/ng-jsoneditor](https://github.com/angular-tools/ng-jsoneditor)


## Use

```html
<!DOCTYPE HTML>
<html>
<head>
    <!-- when using the mode "code", it's important to specify charset utf-8 -->
    <meta http-equiv="Content-Type" content="text/html;charset=utf-8">

    <link href="jsoneditor/dist/jsoneditor.min.css" rel="stylesheet" type="text/css">
    <script src="jsoneditor/dist/jsoneditor.min.js"></script>
</head>
<body>
    <div id="jsoneditor" style="width: 400px; height: 400px;"></div>

    <script>
        // create the editor
        var container = document.getElementById("jsoneditor");
        var editor = new JSONEditor(container);

        // set json
        var json = {
            "Array": [1, 2, 3],
            "Boolean": true,
            "Null": null,
            "Number": 123,
            "Object": {"a": "b", "c": "d"},
            "String": "Hello World"
        };
        editor.set(json);

        // get json
        var json = editor.get();
    </script>
</body>
</html>
```


## Build

The code of the JSON Editor is located in the folder `./src`. To build 
jsoneditor:

- Install dependencies:

  ```
  npm install
  ```

- Build JSON Editor:

  ```
  npm run build
  ```

  This will generate the files `./jsoneditor.js`, `./jsoneditor.css`, and  
  minified versions in the root of the project.


## Custom builds

The source code of JSONEditor consists of CommonJS modules. JSONEditor can be bundled in a customized way using a module bundler like [browserify](http://browserify.org/) or [webpack](http://webpack.github.io/). First, install all dependencies of jsoneditor:

    npm install

To create a custom bundle of the source code using browserify:

    browserify ./index.js -o ./jsoneditor.custom.js -s JSONEditor

The Ace editor, used in mode `code`, accounts for about 75% of the total
size of the library. To exclude the Ace editor from the bundle:

    browserify ./index.js -o ./jsoneditor.custom.js -s JSONEditor -x brace -x brace/mode/json -x brace/ext/searchbox

To minify the generated bundle, use [uglifyjs](https://github.com/mishoo/UglifyJS2):

    uglifyjs ./jsoneditor.custom.js -o ./jsoneditor.custom.min.js -m -c
