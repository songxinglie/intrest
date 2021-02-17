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
-
