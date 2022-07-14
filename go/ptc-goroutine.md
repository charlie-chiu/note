# Processes, Threads, Coroutines and Goroutines

![](ptc.png)

goroutine 基本上就在 coroutine 的位置，同時也可以從命名看出它們的關聯。

goroutine 由 go runtime管理，當 blocking 時就會另起新的 thread 來處理其他 routine

# Process
* PID = Process ID
* 每個 processor ，也就是我們所說CPU 單核、雙核、多核的「核」，一次處理一個process
* process 是分配記憶體的對象
* 每個 process 是互相獨立的
* thread 的容器

# Thread
* 分配 CPU time 的對象，也是實際實行 program 的最小單位
* 有些程式語言可以直接處理 thread (PHP, Java)
* 同一個 process 上的 thread 可共享記憶體

# References
[進程 (Process)、線程 (Thread)、協程 (Coroutine) 的概念講解](https://blog.kennycoder.io/2020/05/16/%E9%80%B2%E7%A8%8B-Process-%E3%80%81%E7%B7%9A%E7%A8%8B-Thread-%E3%80%81%E5%8D%94%E7%A8%8B-Coroutine-%E7%9A%84%E6%A6%82%E5%BF%B5%E8%AC%9B%E8%A7%A3/)

[Effective Go](https://go.dev/doc/effective_go#goroutines)

[Golang | Goroutine vs Thread - GeeksforGeeks](https://www.geeksforgeeks.org/golang-goroutine-vs-thread/)