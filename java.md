## java

### 多线程

#### 线程池 handler 拒绝策略

1. CallerRunsPolicy

   > 该策略下，在调用者线程中直接执行被拒绝任务的run方法，除非线程池已经shutdown，则直接抛弃任务。

2. AbortPolicy

   > 该策略下，直接丢弃任务，并抛出RejectedExecutionException异常。

3. DiscardPolicy

   > 该策略下，直接丢弃任务，什么都不做。

4. DiscardOldestPolicy

   > 该策略下，抛弃进入队列最早的那个任务，然后尝试把这次拒绝的任务放入队列

   