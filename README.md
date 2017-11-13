# react-typescript-startup

The steps to create app using [React](https://reactjs.org/) + [TypeScript](http://typescriptlang.org/).

## Prepare

Install [create-react-app](https://github.com/facebookincubator/create-react-app "create-react-app") in global.

    npm install -g create-react-app

## Setup steps

### Install [react-scripts-ts](https://github.com/wmonk/create-react-app-typescript "react-scripts-ts")

> Create React apps (with Typescript) with no build configuration.

```shell-session
git init
create-react-app . --scripts-version=react-scripts-ts
```

### Require all css from `index.tsx`

> You can hot reloading all ts, tsx, css

```diff
diff --git a/src/index.tsx b/src/index.tsx
index 1c66245..bf693b2 100644
--- a/src/index.tsx
+++ b/src/index.tsx
@@ -2,10 +2,16 @@ import * as React from 'react';
 import * as ReactDOM from 'react-dom';
 import App from './App';
 import registerServiceWorker from './registerServiceWorker';
-import './index.css';
+
+// import all *.css files
+function requireAll(r: any) {
+    r.keys().forEach(r);
+}
+
+requireAll((require as any).context('./', true, /\.css$/));
```

## Start app

> Finish setup and start your app

```shell-session
npm start
```

----

## Tips

### Want to disable tslint

> [How to disable tslint? · Issue #133 · wmonk/create-react-app-typescript](https://github.com/wmonk/create-react-app-typescript/issues/133 "How to disable tslint? · Issue #133 · wmonk/create-react-app-typescript")

Make [tslint.json](tslint.json)'s `rules` field empty.

```diff
diff --git a/tslint.json b/tslint.json
index eb5d66a..2b86576 100644
--- a/tslint.json
+++ b/tslint.json
@@ -1,99 +1,3 @@
 {
-    "extends": ["tslint-react"],
-    "rules": {
-        "align": [
-            true,
-            "parameters",
-            "arguments",
-            "statements"
-        ],
-        "ban": false,
-        "class-name": true,
-        "comment-format": [
-            true,
-            "check-space"
-        ],
-        "curly": true,
-        "eofline": false,
-        "forin": true,
-        "indent": [ true, "spaces" ],
-        "interface-name": [true, "never-prefix"],
-        "jsdoc-format": true,
-        "jsx-no-lambda": false,
-        "jsx-no-multiline-js": false,
-        "label-position": true,
-        "max-line-length": [ true, 120 ],
-        "member-ordering": [
-            true,
-            "public-before-private",
-            "static-before-instance",
-            "variables-before-functions"
-        ],
-        "no-any": true,
-        "no-arg": true,
-        "no-bitwise": true,
-        "no-console": [
-            true,
-            "log",
-            "error",
-            "debug",
-            "info",
-            "time",
-            "timeEnd",
-            "trace"
-        ],
-        "no-consecutive-blank-lines": true,
-        "no-construct": true,
-        "no-debugger": true,
-        "no-duplicate-variable": true,
-        "no-empty": true,
-        "no-eval": true,
-        "no-shadowed-variable": true,
-        "no-string-literal": true,
-        "no-switch-case-fall-through": true,
-        "no-trailing-whitespace": false,
-        "no-unused-expression": true,
-        "no-use-before-declare": true,
-        "one-line": [
-            true,
-            "check-catch",
-            "check-else",
-            "check-open-brace",
-            "check-whitespace"
-        ],
-        "quotemark": [true, "single", "jsx-double"],
-        "radix": true,
-        "semicolon": [true, "always"],
-        "switch-default": true,
-
-        "trailing-comma": [false],
-
-        "triple-equals": [ true, "allow-null-check" ],
-        "typedef": [
-            true,
-            "parameter",
-            "property-declaration"
-        ],
-        "typedef-whitespace": [
-            true,
-            {
-                "call-signature": "nospace",
-                "index-signature": "nospace",
-                "parameter": "nospace",
-                "property-declaration": "nospace",
-                "variable-declaration": "nospace"
-            }
-        ],
-        "variable-name": [true, "ban-keywords", "check-format", "allow-leading-underscore", "allow-pascal-case"],
-        "whitespace": [
-            true,
-            "check-branch",
-            "check-decl",
-            "check-module",
-            "check-operator",
-            "check-separator",
-            "check-type",
-            "check-typecast"
-        ]
-    }
+    "rules": {}
 }
````
