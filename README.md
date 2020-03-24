## passwhl.github.io对应hexo网站源码

### 环境
* 基础
    * node npm git
* 其他
    * hexo-cli: 
        * 说明:hexo命令行工具
        * 安装:npm install hexo-cli -g
        * 使用
            * hexo init dirName 创建hexo
            * hexo s  本地启动 localhost:4000
            * hexo d  部署     
    * hexo-deployer-git
        * 说明:自动部署到github工具
        * 安装:npm install hexo-deployer-git --save
        * 使用:_config.yml配置  
        `deploy:`   
        `type: 'git'`   
        `repo: 'git@github.com:passwhl/passwhl.github.io.git'`
    * hexo-browsersync 
        * 说明: hexo s 自动刷新插件
        * 安装: npm install hexo-browsersync --save
        * 使用: ctrl+s保存时会自动刷新
* 常用配置_config.yml中
    * theme: next 配置主题
            




