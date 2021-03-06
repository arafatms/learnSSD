# 运行 MQSim/fast18/data-cache-contention/ 实例
## 执行仿真
 >MQSim.exe -i ssd_config.xml -w WorkLoad.xml
 ssd_config.xml是所仿真的ssd配置文件，WorkLoad.xml是运行参数文件，具体参数在 [GitHub/MQsim/ReadMe](https://github.com/CMU-SAFARI/MQSim/blob/master/README.md)说明 

## 仿真结果
仿真结果在以上文件里

## 仿真结果处理

- **Flow1_alone**

| Average_No_of_Reqs_in_Queue |Device_Response_Time |
| :-------- | --------:|
| 8  | 21 |
| 8  | 21 |
| 8  | 21 |
| 8  | 21 |
| 8  | 21 |
| 8  | 21 |

- **Flow2_alone**

| Average_No_of_Reqs_in_Queue |Device_Response_Time |
| :-------- | --------:|
| 8  | 21 |
| 16  | 43 |
| 32  | 2490 |
| 64  | 5510 |
| 128  | 11089 |
| 256  | 21491 |

- **Share**

Average_No_of_Reqs_in_Queue_Flow1 = 8

| Average_No_of_Reqs_in_Queue_Flow2 |Device_Response_Time_Flow1 | Device_Response_Time_Flow2 |
| :-------- | :--------: | :-------: |
| 8  | 24 | 24 |
| 16  | 24 | 49| 
| 32  | 745 | 2984 |
| 64  | 760 | 6080 |
| 128  | 778 | 12454 |
| 256  | 771 | 24681 |


![Alt text](https://github.com/arafatms/learnSSD/blob/master/文档/运行%20MQSimfast18data-cache-contention%20实例/SlowDown_Flow1.JPG)             ![Alt text](https://github.com/arafatms/learnSSD/blob/master/文档/运行%20MQSimfast18data-cache-contention%20实例/SlowDown_Flow2.JPG) 
![Alt text](https://github.com/arafatms/learnSSD/blob/master/文档/运行%20MQSimfast18data-cache-contention%20实例/Fairness.JPG)                 ![Alt text](https://github.com/arafatms/learnSSD/blob/master/文档/运行%20MQSimfast18data-cache-contention%20实例/Weighted_Speedup.JPG) 

## 总结
我们得出结论，当一个流具有高写入强度时，写入高速缓存争用会导致同时运行流的不公平性和整体性能下降。 在这些情况下，高写入强度流不受写缓存的影响; 防止其他较低写入强度的流量利用写入缓存，即使其他流量从缓存中获益也是如此。 这促使需要公平的写高速缓存管理算法，以便考虑到间隔干扰和流写入强度。
