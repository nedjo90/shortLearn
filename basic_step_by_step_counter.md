## Steps to Create a SAP UI5 Project: `counter`

### 1. Create the `counter` folder
- This will be the root directory of your project.

### 2. Create the `webapp` folder inside `counter`
- The `webapp` folder will contain all the files for your SAP UI5 application.

### 3. Create the `index.html` file inside `webapp`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <script
      id="sap-ui-bootstrap"
      src="https://openui5.hana.ondemand.com/resources/sap-ui-core.js"
      data-sap-ui-theme="sap_horizon"
      data-sap-ui-libs="sap.m"
      data-sap-ui-compatVersion="edge"
      data-sap-ui-async="true"
      data-sap-ui-oninit="module:sap/ui/counter/index"
      data-sap-ui-resourceroots='{
        "sap.ui.counter": "./"
      }'
    ></script>
    <meta charset="UTF-8" />
    <title>nameOfProject</title>
  </head>
  <body class="sapUiBody" id="content">
  </body>
</html>
```

### 4. Create the `view` folder inside `webapp`
- This folder will contain the XML views of your application.

### 5. Create the `App.view.xml` file inside `webapp/view`

```xml
<mvc:View
    xmlns="sap.m"
    xmlns:mvc="sap.ui.core.mvc"
    controllerName="sap.ui.counter.controller.App"
>
    <Button
        text="increment by 1"
        press=".incrementBy1"
    ></Button>
    <Text id="counter" text="0"/>
</mvc:View>
```

### 6. Create the `controller` folder inside `webapp`
- This folder will contain the JavaScript controllers of your application.

### 7. Create the `App.controller.js` file inside `webapp/controller`

```javascript
sap.ui.define(["sap/ui/core/mvc/Controller"], function (Controller) {
  "use strict";

  return Controller.extend("sap.ui.counter.controller.App", {
    incrementBy1: function () {
      let myTextElem = this.getView().byId("counter");
      let myNum = parseInt(myTextElem.getText());
      let myNewNum = myNum + 1;
      myTextElem.setText(myNewNum);
    },
  });
});
```

### 8. Create the `index.js` file inside `webapp`

```javascript
sap.ui.define(["sap/ui/core/mvc/XMLView"], function (XMLView) {
  "use strict";

  XMLView.create({
    viewName: "sap.ui.counter.view.App",
  }).then(function (oView) {
    oView.placeAt("content");
  });
});
```

### 9. Run `npm init -y` at the root
- This command initializes a `package.json` file with default values.

### 10. Run `ui5 init` at the root
- This command initializes the SAP UI5 project, creating the `ui5.yaml` file.

### 11. Create the `manifest.json` file inside `webapp`

```json
{
  "sap.app": {
    "id": "ui5"
  }
}
```

### 12. Add the `start` command to `scripts` in `package.json`

```json
"scripts": {
  "start": "ui5 serve"
}
```

```go
counter/
│
├── webapp/
│   │
│   ├── index.html
│   │
│   ├── index.js
│   │
│   │── manifest.json
│   │
│   ├── view/
│   │   │
│   │	└── App.view.xml
│   │
│   └── controller/
│	│
│       └── App.controller.js
│
├── package.json
│
└── ui5.yaml
```

