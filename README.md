# mapx

一个清晰的通用的支持并发安全与非安全的map (Go)

1. ### 安装方式

   ```go
   go get -u github.com/byteweap/mapx
   ```

2. ### 使用方式

   > 注：此map封装支持范型，Key为comparable类型即可比较类型，Value为any类型即interface{}类型

   #### 新建map：

   ```go
   // 新建一个并发安全的map(使用互斥锁实现，有一定性能开销)
   m := mapx.New[int, string](true)
   // 新建一个非并发安全的map
   m := mapx.New[int, string](false)
   ```

   #### 内置方法：
   > 具体请查看源码mapx.go的定义， [safemapx.go](safemapx.go) 为并发安全的实现， [unsafemapx.go](unsafemapx.go) 为非并发安全的实现

   - **Get(key Key)：** 获取key的值
   - **Set(key Key, value Value)：** 设置key、value
   - **Delete(key Key):** 删除key
   - **Len():** 获取map长度
   - **Range(fn func(Key, Value)):** 遍历map，已避免死锁问题
   - **Keys() []Key:** 获取所有key
