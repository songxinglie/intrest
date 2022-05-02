## job\task\workflow\pipeline
- https://help.aliyun.com/document_detail/122482.html?spm=a2c4g.11186623.2.7.6393453eeemWH0 阿里Serverless 工作流分布式多步骤事务
  
  - 对错误重试的描述
	```
	retry:  # 对FC.Unknown类型的错误最多指数退避重试3次，初始间隔1s，后续间隔=上次间隔*2。
    - errors:
      - FC.Unknown
      intervalSeconds: 1
      maxAttempts: 3
      multiplier: 2 
	```
  - 对错误处理的描述  
  ```
    catch:  # 捕获ReserveHotel task抛出的FC.Unknown错误，跳转到CancelFlight。
      - errors:
        - FC.Unknown
        goto: CancelFlight	  
  ```		
-	https://help.aliyun.com/document_detail/149828.html?spm=a2c4g.11186623.6.592.20ff73d33Olueq  Serverless工作流支持三种不同的集成模式	
	
	- 请求响应模式：调用第三方服务，在Serverless工作流获得HTTP响应后进入下一个步骤。默认模式是请求响应模式 
	
	- 同步模式：通常这类服务提供了异步执行接口，Serverless工作流调用异步接口成功后会等待，直到相关任务完成并获得了执行结果，Serverless工作流才会继续执行下一个步骤 
	
	- 等待回调模式：调用第三方服务并传入任务令牌，Serverless工作流将进入等待，直到您手动使用该令牌通知流程执行结果后才会继续执行下一个步骤 
- argo 
	- argo 的也是用 yaml 描述工作流，除了传统的 dag 模式，argo 也支持 workflow 模式。相比而言，dag 模式一般比较简单，大部分 ci/cd 场合也比较够用 
	
	- workflow 模式则是一个状态机, workflow 模式的实现更为复杂，也更灵活。用这种模式可以实现有环的任务 
- https://cloud.tencent.com/developer/article/1659175?from=3346 任务流引擎简介

## 前端
- https://www.infoq.cn/article/dsBDeLEohK3IHe8MblFB 前端跨端业务整合的探索与实践
  - 暗黑模式的适配（DarkMode）
```
    首先并不是白色都转换为统一的白色，明亮模式下白色卡片相互叠加因为有黑色边框或者黑色阴影的隔离，层级区分很自然明细；然而在暗黑模式下，自然黑色的边框和阴影并不能将黑色的卡片有效的区分开来，所以需要将所有白色做语义化区分，不同层级不同语义的白色转换为不同深浅的黑色。如此，一个 #FFF 白色，可以根据场景语义化区分为背景纯白 ThemeWhite，主要内容白色 PrimaryContentWhite，次要内容白色 SecondaryContentWhite 等，分别对应的暗黑模式色值为 #0D131A，#252B31，#333B46。



    其次，如上面提到的阴影和边框等拟物色，在暗黑模式下不能转换（自然界中未有过白色的阴影吧）。需要将这些拟物色剥离出来（如阴影的 ShadowBlack），在暗黑模式下不做转换。



    最后，所有的彩色在亮度更低的暗黑模式下需要转换为饱和度更低的对应颜色。例如警戒红色从 #EE3B28 映射为 #F37668，品牌蓝色从 #287DFA 映射为 #7EB0FC。

```


# 
- 在数据分析领域，社区有很多开源的数据交换工具，例如 Exchangis、DataX、DataX Web 和 Dbus 等；在数据开发探索分析工具上，有 Scriptis 、Apache Zeppelin 和 Hue 等；数据可视化工具上，有 Visualis、Davinci 和 Superset 等；开源调度工具有 Schedulis、DolphinScheduler 和 Airflow 等。

在数据治理领域，开源的数据质量校验工具有 Qualitis、pydqc、Deequ 和 GriFFin 等；元数据管理工具有 DataHub、Apache Atlas 等。

在机器学习领域，有 Prophecis、Kubeflow、MLFlow 和天枢人工智能开源平台等。
