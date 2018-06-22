title: Travis-CI简单搭建
date: 2016-02-01 19:57:46

---
# Travis-CI

[Travis CI](https://travis-ci.org/)是一个基于云的持续集成项目, 目前支持大多数的主流语言。


## 使用步骤
1. 今天Travis CI 官网，使用github账号登录。

2. 进入Accounts页面，开启仓库开关。

3. 在你的项目中添加`.travis.yml`文件。

4. 在`.travis.yml`的文件中配置所需信息。

	例如：
	这部分只是为了说明可以配置写什么内容，与下文中的代码不是一体的。谢谢，请勿黏贴。

	```
	language: ruby

	rvm:
  		- 2.2.3

	env:
  		- TRAVIS_NODE_VERSION="4"

	services:
		- mysql

	install:
  		- rm -rf ~/.nvm && git clone https://github.com/creationix/nvm.git ~/.nvm && (cd ~/.nvm && git checkout `git describe --abbrev=0 --tags`) && source ~/.nvm/nvm.sh && nvm install $TRAVIS_NODE_VERSION
  		- bundle install --path vendor/bundle

	before_script:
  		- mysql -e 'create database ILearnC_test;' -uroot
  		- bundle install
  		- npm install -g gulp
  		- npm install

	script:
  		- npm test && gulp build
	```
	具体的牌子可以看Travis CI的官方文档。链接在这里：[点我](https://docs.travis-ci.com/user/getting-started/)

5. 添加测试，使其测试通过。

6. commit & push (当这一切都配置好后，只需push代码到github的仓库即可)。

**以下为demo**

# DEMO

### 步骤
1. 初始一个项目，创建`test`文件夹，并在[Github](https://github.com/)上创建一个仓库。确保你的电脑上安装过[node](https://nodejs.org/en/)，如果没有，请安装。

	*步骤如下*

	推荐使用[nvm](https://github.com/creationix/nvm)安装, 你也可以使用[Homebrew](http://brew.sh/)安装`nvm`，在用`nvm`安装`node`。

	**当所有准备好后，现在开始了**
	* `npm init`初始化项目。
	* 安装[jest](https://facebook.github.io/jest/)测试框架，`npm install jest-cli --save-dev`。
	* 配置`package.json`文件。

		```
		"scripts": {
   			"test": "jest"
 		}
		```

2. 创建`__tests__`和`src`文件夹。

3. 添加测试，命名为：`sum-test.js`。

	```
	var sum = function (a, b) {
  		return a + b;
	}
	module.exports = sum;
	```

4. 在`sum.js`中实现。

	```
	jest.dontMock('../src/sum');

	describe('sum', function() {
 		it('adds 1 + 2 to equal 3', function() {
   			var sum = require('../src/sum');
   			expect(sum(1, 2)).toBe(3);
 		});
	});
	```
5. 运行测试`npm test`。

6. push 到github上。这一步就要与travis连接了。
