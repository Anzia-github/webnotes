- 效果
	- [[ES6]]转[[ES5]]
- 使用
	- 下载
		- `npm install @babel/core @babel/preset-env babel-loader --save-dev`
	- 添加内容
		- 新建.babelrc文件，专门用于babel配置
		```JS
		{
			"presets": ["@babel/preset-env"]
		}
		```
		- [[webpack.config.js]]
		```js
		module.exports = {
			...,
			module: [
				{
					test: /\.js$/,
					loader: ['babel-loader'],
					include: path.join(__dirname, 'src'),
					exclude: /node_module/
				}
			]
		}
		```