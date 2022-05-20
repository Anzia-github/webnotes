- 安装步骤
	```shell
	npm init
	# 下载不用浏览器版本
	npm i pupputeer-core --save 
	```
- 配置
	- 引入
	```JS
	const puppeteer = require("puppeteer-core");
	```
	- 浏览器启动配置
	```JS
	const browser = await puppeteer.launch({
		// 默认无头，即不显示浏览器，这里打开以显示浏览器
		headless: false, 
		// 使用本地浏览器打开
		executablePath: 'C:\\Program Files (x86)\\Microsoft\\Edge\\Application\\msedge.exe'
	});
	```
	- 打开浏览器
	```JS
	const page = await browser.newPage();
	```
	- 转到链接
	```JS
	await page.goto(
		'https://www.bilibili.com/v/dance/hiphop/?spm_id_from=333.1073.0.0'
	);
	```
	- 解析DOM获取内容
	```JS
	let titles = await page.$$eval(
		"#videolist_box > div.vd-list-cnt > ul > li > div > div.r > a", (links) => links.map((x) => x.innerText)
	);

	console.log(titles);
	```