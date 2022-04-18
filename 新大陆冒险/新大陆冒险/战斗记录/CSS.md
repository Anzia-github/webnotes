- [[CSS]]3新特性
	- 选择器
		- last-child
		- nth-child(n)
		- nth-last-child(n)
	- [[rgba]]
	- 多栏布局
		- ```css
		  .mul-col {
		    column-count: 3;
		    column-gap: 5px;
		    column-rule: 1px solid gray;
		    border-radius: 5px;
		    border: 1px solid gray;
		    padding: 10px;
			}
	- 多背景图
		- `backgroundimage:url('1.jpg),url('2.jpg');`
	- word-wrap
		- `word-wrap: break-word;`
	- text-shadow
		- `text-shadow: 5px 2px 6px rgba(64, 64, 64, 0.5);`
	- @font-face
		- ```CSS 
		  @font-face {
		    font-family: BorderWeb;
		    src: url(BORDERW0.eot);
			}
	- border-radius
	- border-image
	- box-shadow
	- box-sizing
	- @media
	- 动画
		- @keyframes
			- ```CSS
			  @keyframes abc {
					from {
						transform: rotate(0);
					}
					50% {
						transform: rotate(90deg);
					}
					to {
						transform: rotate(360deg);
					}
				}
		- animation
			- `animation：name duration timing-function delay interation-count direction play-state;`
	- 渐变效果
		- ```CSS
		  background-image: -webkit-gradient(linear,
		    0% 0%,
		    100% 0%,
		    from(#2a8bbe),
		    to(#fe280e));
	- 弹性盒模型
		- `display: flex;`
	- 过渡
		- ```CSS
		  div {
				transition: width 2s;
				-moz-transition: width 2s;
				/* Firefox 4 */
				-webkit-transition: width 2s;
				/* Safari 和 Chrome */
				-o-transition: width 2s;
				/* Opera */
			}
	- 变换
		- rotate()旋转
		- translate()平移
		- scale()缩放
		- skew()倾斜
		- 变换基点
		- 3D转换