# xsm-cli

Used to spawn a 'grunt' with subfolder's gruntfile by config.

在复杂前端项目中，将不同功能、模块的 Grunt 任务拆分为多个配置文件，通过 xsm 命令来加载。

## 用法

命令：
```
xsm home uglify:index
```

xsmfile.js:
```javascript
module.exports = {
  home: 'src/home/Gruntfile.js'
}
```

config/order/Gruntfile.js:
```javascript
module.exports = function (grunt) {
  grunt.initConfig({
    uglify: {
      index: {
        src: 'src/home/index/main.js',
        dest: 'dist/home/index/main.js'
      }
    }
  })

  grunt.loadNpmTasks('grunt-contrib-uglify')
}
```

目录结构：
```
- src/
  - home/
    - index/
      - main.js
    - Gruntfile.js
- dist/
  - home/
    - index/
      - main.js
- node_modules/
- xsmfile.js
- package.json
```
