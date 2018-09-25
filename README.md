## Installation

This package is not yet published to the npm registry. Install from GitHub:

```
yarn add --dev react-app-rewired-svg-sprite-loader
```

OR

```
npm install --save-dev react-app-rewired-svg-sprite-loader
```

## Usage

Import your `*.svg` files and use them as React components.

### Example

In your react-app-rewired configuration:

```javascript
/* config-overrides.js */

const rewireSvgSpriteLoader = require("react-app-rewired-svg-sprite-loader");

module.exports = function override(config, env) {
  // ...
  config = rewireSvgSpriteLoader(config, env);
  // ...
  return config;
};
```

In your React application:

```jsx harmony
// src/App.js

import React from "react";
import ReactDom from "react-dom";
import Icon from "./Icon";

ReactDom.render(
  <div>
    <Icon name="icon1" />
    <Icon name="icon2" />
  </div>,
  document.getElementById("app")
);
```

```jsx harmony
// src/Icon.js comp
import React from "react";
import "./icons.svg";

const Icon = (props) => (
  <svg className={`icon icon-${props.name}`}>
    <use xlinkHref={`#icons_${props.name}`} />
  </svg>
);

export default Icon;
```

```svg
<!-- src/icons.svg -->

<svg version="1.1" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <symbol id="icon1" viewBox="0 0 32 32">
      <path d="M32 19l-6-6v-9h-4v5l-6-6-16 16v1h4v10h10v-6h4v6h10v-10h4z"></path>
    </symbol>
    <symbol id="icon2" viewBox="0 0 32 32">
      <path
        d="M9.5 19c0 3.59 2.91 6.5 6.5 6.5s6.5-2.91 6.5-6.5-2.91-6.5-6.5-6.5-6.5 2.91-6.5 6.5zM30 8h-7c-0.5-2-1-4-3-4h-8c-2 0-2.5 2-3 4h-7c-1.1 0-2 0.9-2 2v18c0 1.1 0.9 2 2 2h28c1.1 0 2-0.9 2-2v-18c0-1.1-0.9-2-2-2zM16 27.875c-4.902 0-8.875-3.973-8.875-8.875s3.973-8.875 8.875-8.875c4.902 0 8.875 3.973 8.875 8.875s-3.973 8.875-8.875 8.875zM30 14h-4v-2h4v2z"></path>
    </symbol>
  </defs>
</svg>
```
