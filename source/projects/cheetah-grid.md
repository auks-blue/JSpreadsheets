---
title: cheetah-grid
repo: future-architect/cheetah-grid
homepage: https://future-architect.github.io/cheetah-grid
examples: https://future-architect.github.io/cheetah-grid
license: MIT
author: Future Corporation. Japan.
authorurl: https://www.future.co.jp
description: The fastest open-source data table for web.
---

## What it is

Cheetah Grid is a high performance JavaScript data table component that works on canvas

not require jQuery

## Show 1,000,000 records without stress

You can display data of 1 million records in a moment.

https://future-architect.github.io/cheetah-grid/documents/introduction/

## Note

Support for IME

IMEを使用した入力によるデータ編集が可能です。事前にセルを編集モードにしておく必要もありません。

Multiple Input Editor

[SmallDialogInputEditor](https://future-architect.github.io/cheetah-grid/documents/api/js/column_actions/SmallDialogInputEditor.html)と[InlineInputEditor](https://future-architect.github.io/cheetah-grid/documents/api/js/column_actions/InlineInputEditor.html)の2つの入力エディタを利用できます。

The fastest open-source data table for web.

[![capture.png](https://github.com/future-architect/cheetah-grid/raw/master/images/capture.png)](https://future-architect.github.io/cheetah-grid/)

[DEMO & Documents](https://future-architect.github.io/cheetah-grid/)

## Downloading Cheetah Grid

### Using Cheetah Grid with a CDN

[![npm](https://img.shields.io/npm/v/cheetah-grid.svg)](https://www.npmjs.com/package/cheetah-grid)

```html
<script src="https://unpkg.com/cheetah-grid@1.13"></script>
```

### Downloading Cheetah Grid using npm

[![npm](https://img.shields.io/npm/v/cheetah-grid.svg)](https://www.npmjs.com/package/cheetah-grid)

```sh
npm install -S cheetah-grid
```

```js
import * as cheetahGrid from "cheetah-grid";

// or

const cheetahGrid = require("cheetah-grid");
```

### Downloading Cheetah Grid source code

[![npm](https://img.shields.io/npm/v/cheetah-grid.svg)](https://www.npmjs.com/package/cheetah-grid)

[cheetahGrid.es5.min.js](https://unpkg.com/cheetah-grid@1.13/dist/cheetahGrid.es5.min.js)

SourceMap  
[cheetahGrid.es5.min.js.map](https://unpkg.com/cheetah-grid@1.13/dist/cheetahGrid.es5.min.js.map)

### Downloading Cheetah Grid using GitHub

[![GitHub package version](https://img.shields.io/github/package-json/v/future-architect/cheetah-grid.svg)](https://github.com/future-architect/cheetah-grid)

#### git clone

```bash
git clone https://github.com/future-architect/cheetah-grid.git
```

#### npm install & build

```bash
npm install
npm run build
```

built file is created in the `./packages/cheetah-grid/dist` directory

## Usage

### Example for basic usage

```html
<div id="sample" style="height: 300px; border: solid 1px #ddd;"></div>
<script>
  // initialize
  const grid = new cheetahGrid.ListGrid({
    // Parent element on which to place the grid
    parentElement: document.querySelector("#sample"),
    // Header definition
    header: [
      {
        field: "check",
        caption: "",
        width: 50,
        columnType: "check",
        action: "check",
      },
      { field: "personid", caption: "ID", width: 100 },
      { field: "fname", caption: "First Name", width: 200 },
      { field: "lname", caption: "Last Name", width: 200 },
      { field: "email", caption: "Email", width: 250 },
    ],
    // Array data to be displayed on the grid
    records,
    // Column fixed position
    frozenColCount: 2,
  });
</script>
```

Please refer to the [documents](https://future-architect.github.io/cheetah-grid/) for details

> **Using the Vue Component of Cheetah Grid**  
> Please refer to the [`vue-cheetah-grid`](https://www.npmjs.com/package/vue-cheetah-grid)
>
> **Using the React Component of Cheetah Grid**  
> Please refer to the [`react-cheetah-grid`](https://www.npmjs.com/package/react-cheetah-grid)

### Definition of columns and headers

The `header` property, the property of `cheetahGrid.ListGrid`, decides the behave and appearance of columns and header cells.
We can set this property by constructor arguments or instance property.

The `header` property must be set by objects array (`Array<object>`).
In the standard definition, each object consists of following properties.

| Property              | Description                                                            |
| --------------------- | ---------------------------------------------------------------------- |
| caption               | define the header caption                                              |
| field                 | define the field name or function of the record to display in the cell |
| width (optional)      | define the width of column                                             |
| columnType (optional) | define the type of column                                              |
| style (optional)      | define the style of column                                             |
| action (optional)     | define the action of column                                            |

To use multiple header, set the hierarchical structured Object to the `header` property.

```js
const grid = new cheetahGrid.ListGrid({
  //...
  header: [
    //...
    {
      /* multiple header */
      caption: "Name",
      columns: [
        { field: "fname", caption: "First Name", width: 200 },
        { field: "lname", caption: "Last Name", width: 200 },
      ],
    },
    //...
  ],
  //...
});
```

### Definition of column type

Set the column type by using `columnType`.

For example, you can set the following strings:

| Property          | Description                                  |
| ----------------- | -------------------------------------------- |
| none              | draw text in the cell                        |
| `'number'`        | draw number in the cell with comma-separated |
| `'check'`         | draw checkbox in the cell                    |
| `'button'`        | draw button in the cell                      |
| `'image'`         | draw image in the cell                       |
| `'multilinetext'` | draw multiline text in the cell              |

If you define a class instance you can define an advanced column types.

Please refer to the [column types documents](https://future-architect.github.io/cheetah-grid/documents/api/js/column_types/Classes.html) for details

### Definition of column action

Define column action by using `action` property.

| `action`  | Description                   |
| --------- | ----------------------------- |
| `'check'` | make the check box clickable. |
| `'input'` | make the cell enterable.      |

If you define a class instance you can define an advanced column actions.

Please refer to the [column actions documents](https://future-architect.github.io/cheetah-grid/documents/api/js/column_types/Classes.html) for details

### Definition of column style

Define column style by using `style` property.

Properties below are prepared in standard.

| Property     | Description                                                                                      |
| ------------ | ------------------------------------------------------------------------------------------------ |
| color        | define the color of cell.                                                                        |
| textAlign    | define the horizontal position of text in cell.                                                  |
| textBaseline | define the vertical position of text in cell.                                                    |
| bgColor      | define the background color of cell.                                                             |
| font         | define the font of cell.                                                                         |
| padding      | define the padding of cell. if you set 4 values separately, please set the `Array`.              |
| textOverflow | define how to display when text overflows the area of a cell. `clip` or `ellipsis` is available. |

In addition, there is an extended style property for each column type.

---

Please refer to the [documents](https://future-architect.github.io/cheetah-grid/) for details

## License

See the [LICENSE](https://github.com/future-architect/cheetah-grid/blob/master/LICENSE) file for license rights and limitations (MIT).

## Supporting Cheetah Grid

[![sponsors](https://img.shields.io/badge/-Sponsor-fafbfc?logo=GitHub%20Sponsors)](https://github.com/sponsors/ota-meshi)
