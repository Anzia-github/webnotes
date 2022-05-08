- 例子
	- 自动打包带有[[JS]]文件的[[HTML]]
		- 下载
			- `npm install html-webpack-plugin --save-dev`
		- webpack.config.js
			- 添加新的内容
			```JS
			const HtmlWebpackPlugin = require('html-webpack-plugin')
			
			moudle.exports = {
				...
				plugins: [
					new HtmlWebpackPlugin({
						template: path.join(__dirname, 'src', 'index.html'),
						filename: 'index.html'
					})
				]
			}
			```