# react-typescript-startup

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
