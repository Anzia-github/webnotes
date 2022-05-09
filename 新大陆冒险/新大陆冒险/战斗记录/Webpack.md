- 下载
	- `npm install webpack webpack-cli --save-dev`
- 基本配置
	- src/index.js
	- [[webpack.config.js]]
		```JS
		const path = require('path');
		
		module.exports = {
		  mode: 'development',
		  entry: path.join(__dirname, 'src', 'index.js'),
		  output: {
			path: path.join(__dirname, 'dist'),
			filename: 'bundle.js'
		  }
		};
		```
	- [[package.json]]
		```JS
		script: {
			'build': 'webpack'
		}
		```
- 概念
	- [[mode]]
	- [[entry]]
	- [[output]]
	- [[loader]]
	- [[plugins]]
		- [[html-webpack-plugin]]
- [[webpack-dev-server]]
- [[babel]]