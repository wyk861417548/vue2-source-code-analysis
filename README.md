- 代码目录结构
- benchmarks  做性能测试
- dist 打包结果
- examples 官方例子
- flow 类型检查（没人用了） 和 ts功能类似
- packages 一些写好的包（vue源码中包含了weex）
- script 所有打包的脚本都放在这里
- src 源代码目录
  - compiler专用于模板编译的
  - core vue2的核心代码
  - platform 
  - server 服务端渲染相关
  - sfc 解析单文件组件的
  - shared 就是模块之间的共享属性和方法


- 通过package.json 找到打包入口
  - scripts/config.js (web-full-dev, web-runtime-cjs-dev,web-runtime-esm....)
- 打包的入口
  - src/platforms/web/entry-runtime.js
  - src/platforms/web/entry-runtime-with-compiler.js (两个入口的区别是带有compiler的会重写$mount，将template变成render函数)
  - runtime/index.js (所谓的 运行时会提供一些dom操作的api、属性操作、元素操作、提供一些组件和指令)
    - modules
      - attrs (属性处理)
      - class (类名处理)
      - dom-props (dom属性处理)
      - events （事件处理）
      - styles （样式处理）
      - transition
    - directives
    - components

  - core/index initGlobalAPI 初始化全局api
  - /instance/index Vue构造函数

> 指定sourcemap参数开启调试
  - scripts/config.js 输出配置中加sourcemap:true
  - 或者 文件package.json中命令中加 --sourcemap

