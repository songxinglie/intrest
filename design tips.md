## job\task\workflow\pipeline
- https://help.aliyun.com/document_detail/122482.html?spm=a2c4g.11186623.2.7.6393453eeemWH0 阿里Serverless 工作流分布式多步骤事务
    对错误重试的描述
	retry:  # 对FC.Unknown类型的错误最多指数退避重试3次，初始间隔1s，后续间隔=上次间隔*2。
    - errors:
      - FC.Unknown
      intervalSeconds: 1
      maxAttempts: 3
      multiplier: 2
	对错误处理的描述  
    catch:  # 捕获ReserveHotel task抛出的FC.Unknown错误，跳转到CancelFlight。
      - errors:
        - FC.Unknown
        goto: CancelFlight	  
		
	https://help.aliyun.com/document_detail/149828.html?spm=a2c4g.11186623.6.592.20ff73d33Olueq  Serverless工作流支持三种不同的集成模式	
	请求响应模式：调用第三方服务，在Serverless工作流获得HTTP响应后进入下一个步骤。默认模式是请求响应模式
	同步模式：通常这类服务提供了异步执行接口，Serverless工作流调用异步接口成功后会等待，直到相关任务完成并获得了执行结果，Serverless工作流才会继续执行下一个步骤
	等待回调模式：调用第三方服务并传入任务令牌，Serverless工作流将进入等待，直到您手动使用该令牌通知流程执行结果后才会继续执行下一个步骤
- argo
	argo 的也是用 yaml 描述工作流，除了传统的 dag 模式，argo 也支持 workflow 模式。相比而言，dag 模式一般比较简单，大部分 ci/cd 场合也比较够用
	workflow 模式则是一个状态机, workflow 模式的实现更为复杂，也更灵活。用这种模式可以实现有环的任务
- https://cloud.tencent.com/developer/article/1659175?from=3346 任务流引擎简介 