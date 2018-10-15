### Intro

### 1. How to use
> npm i pri-json-picker --save-dev

### 2. How to import
**webpack.config.js:**
```javascript
var path = require('path');
module.exports = {
entry : {...},
output : {...},
module : {
	loaders :[{
		test: /\.css$/,
		loader: 'style!css'
	}, {
		test: /\.js$/,
		exclude: path.resolve('./node_modules'),
		loader: 'babel',
	}]
}
}
```

**html：**
```html
<body>
	<!-- the #targetInput can be any other dom for your convenient-->
	<input id="targetInput" type="text" readonly/>
	<!-- the #targetContainer must be the outermost dom below body -->
	<div id="targetContainer"></div>
</body>
```

**js：**
```javascript
import MultiPicker from 'pri-json-picker';
new MultiPicker({ ... });
```

**Parameter List：**

| Attributes |  Type  |  Value  | Details | 
| -----| -----| -----| -----|
|  **input**    |  {String} |*eg:'targetInput'* | the id of the dom you touch. |
|  **container**    |  {String} |*eg:'targetContainer'*| the id of the container you ready to append dom. |
|  **jsonData**    | {Array} |*eg:'[{'id':001,'value':'北京市'，'child':[{'id':00101,'value':'朝阳区'}，{'id':00102,'value':'海淀区'}]}]'*| user-defined JSON must be legal. A obj  is made up of  three attrs, `id`, `value` and `child`. |
|  **success**   |  {function} |*function(arr){alert(arr)}*| function(arr){} User-defined callback. The first param is the result.  And you'll see other prop "index" which means the obj's index depends on the child prop of the straight parent(after v1.2.0).|


**The JSON Object:**

| Attributes | Type | Details | 
| -----| -----|  -----|
|  **id**    |  {String} | the identity of it |
|  **value**    |  {String} |  the value of it  |
|  **child**    | {Array} |  the next linkage of it. If it's the last linkage, the `child` can be an empty array or null. |


