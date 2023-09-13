```golang
+-------------------+
|   Pointer (指针)   | --> 指向底层数组的起始位置
+-------------------+
|    Length (长度)    | --> 切片中当前存储的元素数量
+-------------------+
|   Capacity (容量)   | --> 切片从起始位置到底层数组末尾的可用元素数量
+-------------------+


mySlice := make([]int, 0, 10) // 创建一个整数切片，初始长度为0，容量为10



var myMap = make(map[string]int)
var mutex = sync.Mutex{}

// 写操作
mutex.Lock()
myMap["key"] = 123
mutex.Unlock()

// 读操作
mutex.Lock()
value := myMap["key"]
mutex.Unlock()

var myMap = sync.Map{}

// 写操作
myMap.Store("key", 123)

// 读操作
value, found := myMap.Load("key")
if found {
    // 处理 value
}



import (
    "context"
    "fmt"
    "time"
)

func main() {
    // 创建一个带有超时的 context，超时时间为 2 秒
    ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
    defer cancel() // 确保在函数退出时取消 context

    // 在一个 goroutine 中执行耗时的操作，检查 context 是否被取消
    go func() {
        select {
        case <-time.After(3 * time.Second):
            fmt.Println("Operation completed")
        case <-ctx.Done():
            fmt.Println("Operation canceled or timed out")
        }
    }()

    // 阻塞等待操作完成或超时
    <-ctx.Done()
}


ch := make(chan int)
go func() {
    ch <- 12 // 向channel发送数据
}()

data := <-ch // 从channel接收数据



ch := make(chan bool)
go func() {
    // 执行一些操作
    // ...

    ch <- true // 操作完成后发送信号
}()

// 等待操作完成
<-ch


ch := make(chan bool, 10) // 带缓冲的channel，容量为10

for i := 0; i < 20; i++ {
    go func(id int) {
        // 执行一些操作
        // ...

        ch <- true // 发送信号
    }(i)
}

// 等待所有操作完成
for i := 0; i < 20; i++ {
    <-ch
}



+-------------------------+
|   Go 调度器 (Scheduler)   |
+-------------------------+
        |
        |  负责调度和管理 Goroutines
        |
+-------|-------|-------|-------+
|   P   |   P   |   P   |   P   |
|   +---|---+   |   +---|---+   |
|   | G | G |   |   | G | G |   |
|   +---|---+   |   +---|---+   |
|       |       |       |       |
+-------|-------|-------|-------+
        |
        |  与 M 相关联
        |
+-------------------------+
|     Machines (M)        |
+-------------------------+
        |
        |  实际执行线程管理
        |
+-------|-------|-------|-------+
|   M   |   M   |   M   |   M   |
|       |       |       |       |
|       |       |       |       |
|       |       |       |       |
+-------|-------|-------|-------+

```
