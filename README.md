# addRedisScript
High Performance Add Redis Key Script

## 设计目标
配套addRedisScript脚本，增加数据   
 [delRedisScript](https://github.com/iooikaak/delRedisScript)

### Features
- 高性能，bechmark测试
- 支持开10W协程并发删除redis

#	依赖
## 硬件平台
- X86 服务器

## 软件平台
- Ubuntu 18.04 LTS
- Go1.14

## bechmark测试
- 测试机器
hp latebook pro 2核 8G内存 

### 开200个协程，插入10W条数据
![image](https://github.com/iooikaak/addRedisScript/blob/master/pic/01.png)
```
vagrant@ubuntu-bionic:~/Dev/code/go/src/addRedisScript$ go run main.go -readRedisHost "127.0.0.1:6379" -readRedisPassword "" -writeRedisHost "127.0.0.1:6379" -writeRedisPassword "" -userIDMinNum 1 -userIDMaxNum 100000 -goRoutineCount 200
2020/03/18 09:11:06 Add Redis Key Script Has Done!!!
2020/03/18 09:11:06 Start Unix Time:1584522662768333733, End Unix Time:1584522666312347490, Run time:3544013757
```
QPS：100000/3.544013757= 28216
### 开1W个协程，插入1000W条数据
![image](https://github.com/iooikaak/addRedisScript/blob/master/pic/02.png)
```
vagrant@ubuntu-bionic:~/Dev/code/go/src/addRedisScript$ go run main.go -readRedisHost "127.0.0.1:6379" -readRedisPassword "" -writeRedisHost "127.0.0.1:6379" -writeRedisPassword "" -userIDMinNum 1 -userIDMaxNum 10000000 -goRoutineCount 10000
2020/03/18 09:14:57 Add Redis Key Script Has Done!!!
2020/03/18 09:14:57 Start Unix Time:1584522876367528615, End Unix Time:1584522897856514205, Run time:21488985590 
```
QPS: 10000000/21.488985590=465354
### 开5W个协程，插入1000W条数据
![image](https://github.com/iooikaak/addRedisScript/blob/master/pic/03.png)
```
vagrant@ubuntu-bionic:~/Dev/code/go/src/addRedisScript$ go run main.go -readRedisHost "127.0.0.1:6379" -readRedisPassword "" -writeRedisHost "127.0.0.1:6379" -writeRedisPassword "" -userIDMinNum 1 -userIDMaxNum 10000000 -goRoutineCount 50000
2020/03/18 09:17:42 Add Redis Key Script Has Done!!!
2020/03/18 09:17:42 Start Unix Time:1584523051427090298, End Unix Time:1584523062245214941, Run time:10818124643 
```
QPS: 10000000/10.818124643=924374
### 开10W个协程，插入1000W条数据
![image](https://github.com/iooikaak/addRedisScript/blob/master/pic/04.png)
```
vagrant@ubuntu-bionic:~/Dev/code/go/src/addRedisScript$ go run main.go -readRedisHost "127.0.0.1:6379" -readRedisPassword "" -writeRedisHost "127.0.0.1:6379" -writeRedisPassword "" -userIDMinNum 1 -userIDMaxNum 10000000 -goRoutineCount 100000
2020/03/18 09:19:56 Add Redis Key Script Has Done!!!
2020/03/18 09:19:56 Start Unix Time:1584523186976773055, End Unix Time:1584523196774139671, Run time:9797366616 
```

QPS:10000000/9.797366616=1020682
