# whatweb-plus


已内测、已公测, 无缺陷性问题反馈, 代码开源, 放心使用.  ---NOVASEC 酒零

    whatweb自开始改造截至目前已更新10个版本以上，
    目前版本是0.5.5.12，是最新版，也是整体功能的最终版，后续基本只会对插件进行增删和优化。
    这个版本后，我已将我目前对指纹识别工具所有的要求和理解都进行了实现。
    如果没有其他的同样功能支持的Go版本替代，这应该是最强大的指纹识别工具了。
    
    指纹在群聊有偶尔更新，更新较多指纹时会上传github
    
    希望大家积极提交指纹和指纹需求！！！

    
重点注意

    1、使用ruby运行whatweb脚本，需要安装mmh3模块 【gem install mmh3】
    
    2、whatweb.exe为了缩小打包体积，仅包含简单的基础插件，请-p 指定插件目录调用。
    
    3、关于waf识别问题：
        支持waf指纹，但没有添加会触发waf的请求。请主动请求会出发waf的url，如whatweb http://www.baidu.com/index?/etc/passed
        
    4、关于运行环境的问题：
        windows下有exe打包版本，其他系统未打包成功，需要安装ruby环境（kali ruby2.5-2.7 测试通过） 

下一步规划

    1、对指纹扫描插件进行分类规划,需要人员支持，主要是进行规则命名的规划和规则合并整理,技术难度较小,但是需要较多的时间。
    2、使用Golang等快速的跨平台的语言重构整个项目【目前决定使用基于golang编译语言的yak语言实现新版whatweb,其他也有使用golang+表达式语言实现的想法】
    3、有兴趣的朋友可以联系加入这个项目进行支持。
    
    4、其他规划：添加一个可选参数和部分语句来主动探测waf。
    5、扩展规划：如果使用yak重构成功后，尝试添加对于yaml等格式的规则进行支持。
    6、扩展规划：如果使用yak重构成功后，尝试添加被进入动扫描模块中。
    7、其他规划：尝试添加一个未匹配站点的指纹自动记录的功能,便于用户的指纹编写。
    

最近更新记录

    whatweb-Plugins-202108232230.zip
    1、更新到8000+插件,大部分由于名称问题重复。
    2、修复shiro指纹的https支持
    3、增加要给fastjson指纹插件(未找到测试站点)
    4、替换my-plugins文件夹使用


Whatweb增强版介绍与使用：

    Whatweb 0.5.5.12 完善使用及插件文档【非常重要,记录各种功能更新及基本使用】
    https://mp.weixin.qq.com/s/F9sXIhCfFCZ3WtMMltnP5Q

    痛点重谈-Web指纹识别与解决方案-NOVASEC
    https://mp.weixin.qq.com/s/lHIJmIWbm8ylK6yjjmmNkg


    Whatweb特征修改、插件编写、EXE打包
    https://mp.weixin.qq.com/s/TaYHrzw5Yb6jxj046nR_DA

    Ruby and Whatweb Install on Windows
    https://mp.weixin.qq.com/s/ZjQfsovGP-GK_xUYuP7M-A
        
    NOVASEC 开源工具记录
    https://mp.weixin.qq.com/s/h4rYBZ36xaEHF34vyW4WQg

    里程碑思路: Go工具框架实现动态插件
    https://mp.weixin.qq.com/s/ihNalwYQGNcWlG7TJ8yazw

    whatweb增强版公开发布
    https://mp.weixin.qq.com/s/njxWqxw-TJH2MKAvOvI-kg

关于[-X][-Y][-Z]三个重点匹配优化项说明:


    [关于--no-base-path, -Z 关闭的功能, 根据使用条件关闭]    
    新增，关闭自动访问高频指纹路径，默认True
    whatweb-plus 默认会请求几个内置指纹路径,表现为每个目标都会额外多出几个请求。  

    [关于--no-min-urls, -Y 关闭的功能,不建议关闭] 
    新增，关闭最小化访问插件:url，默认True
    whatweb-plus 默认会将匹配插件的每一个请求URL重写作为完整的新URL作为请求，以避免全局重复请求相同的URL
    缺点是会表现出一个站点的多个子请求，建议使用novafinger.py包装器的--log-csv参数进行结果输出，便于排序处理
   
    [关于--no-max-match, -X 关闭的功能,不建议关闭]  
    新增，忽略匹配:url要求，默认True
    whatweb-plus 匹配规则时,默认会忽略:url需要相同的前提，形成更多的结果匹配，需要最高精度的匹配时可以开启
   
    注意:URL去重使用全局数组和临时数组实现,对于【超级超级超级超级大量】请求的情况建议定时优化。

![image](https://user-images.githubusercontent.com/46115146/130211813-fc6343c8-43af-49b6-be64-8786b050a280.png)


    
指纹合并记录
    
    dismap    
    tidefinger-python3    
    tidefinger-python2     
    wappalyzer    
    Ehole+Finger  
    Fscan+glass    WAF指纹
    
    致谢开源指纹的各位工程师。
