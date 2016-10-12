# grunt-automatic-version

> 自动给指定文件中的js css 添加版本号【例如：1.0.1.047ac20f】【主版本.次版本.修订.文件hash值前8位】

#### 说明
该插件适用于grunt环境，本插件是基于  [automatic-version-increment](https://github.com/noahxinhao/automatic-version-increment) 二次开发

```shell
npm install grunt-automatic-version --save
```

#### 使用

```js
module.exports = function (grunt) {
  
  grunt.loadNpmTasks('grunt-automatic-version');

  grunt.initConfig({
    ……
    // 添加版本号
    automatic: {
      js: {
        options: {
          // basicSrc: [src/main/webapp/public/js_control/]
          basicSrc: ['*/js/','*/js/sns/']
        },
        version:"1.1.0",
        assetUrl: ['*.js'],
        files: {
          // 'tmp': ['src/main/webapp/views/**/*.jsp']
          'tmp': ['<%= config.export %>/**/*.vm']
        }
      },
      css: {
        options: {
          // basicSrc: [src/main/webapp/public/css/]
          basicSrc: ['*/css/']
        },
        version:"1.1.0",
        assetUrl: ['*.css'],
        files: {
          // 'tmp': ['src/main/webapp/views/**/*.jsp']
          'tmp': ['<%= config.export %>/**/*.vm']
        }
      }
    },
    ……
  })
  grunt.registerTask('export', [
    ……
    'automatic'
  ]);
}
```
#### 示例

##### 编译前
```html
<!DOCTYPE HTML>
<html lang="en-US">
<head>
    <meta charset="UTF-8">
    <title>test</title>
    <link rel="stylesheet" href="css/hello.css" />
    <link rel="stylesheet" href="css/hello1.css" />
    <link rel="stylesheet" href="https://assets-cdn.github.com/assets/frameworks-3514e6d8825ab9f55728f0030acba498e5da5b85ebc8abc35f0f466ac9d2bdda.css"/>
    <script type="text/javascript" src="js/hello.js"></script>
    <script type="text/javascript" src="js/hello1.js"></script>
    <script src="https://assets-cdn.github.com/assets/frameworks-ea5bbb2a837377ffde53e1099e5909c8df4d36cc5e90c05aeb3694b157df7e4d.js"></script>
</head>
<body>
    
</body>
</html>
```
##### 编译后 

```html
<!DOCTYPE HTML>
<html lang="en-US">
<head>
    <meta charset="UTF-8">
    <title>test</title>
    <link rel="stylesheet" href="css/hello.css?v=1.0.3.99819624" />
    <link rel="stylesheet" href="css/hello1.css?v=1.0.3.96811b45" />
    <link rel="stylesheet" href="https://assets-cdn.github.com/assets/frameworks-3514e6d8825ab9f55728f0030acba498e5da5b85ebc8abc35f0f466ac9d2bdda.css"/>
    <script type="text/javascript" src="js/hello.js?v=1.0.3.cefe2283"></script>
    <script type="text/javascript" src="js/hello1.js?v=1.0.3.cefe2283"></script>
    <script src="https://assets-cdn.github.com/assets/frameworks-ea5bbb2a837377ffde53e1099e5909c8df4d36cc5e90c05aeb3694b157df7e4d.js"></script>
</head>
<body>
</body>
</html>
```
