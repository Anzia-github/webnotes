- 效果
	- 热更新打包
	- 缺点
		- 不会真的打包
		- 预览的文件是保存在内存中的
- 使用
	- 下载
		- `npm install webpack-dev-server`
	- 添加内容
		- package.json
			```JS
			script: {
				...,
				'dev': 'webpack-dev-server'
			}
			```
		- webpack.config.js
			```JS
			module.exports = {
				...,
				devServer: {
					port: 8000,
					static: path.join(__dirname, 'dist')
				}
			}
			```
