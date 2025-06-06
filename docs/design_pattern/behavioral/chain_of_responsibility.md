# 责任链模式 (Chain of Responsibility Pattern)

## 概述
责任链模式是一种行为设计模式，它允许你将请求沿着处理者链进行发送。收到请求后，每个处理者均可对请求进行处理，或将它传递给链中的下一个处理者。

## 主要角色
1. Handler（抽象处理者）
2. ConcreteHandler（具体处理者）
3. Client（客户端）

## 实现示例
```java
// 抽象处理者
abstract class Handler {
    protected Handler successor;
    
    public void setSuccessor(Handler successor) {
        this.successor = successor;
    }
    
    public abstract void handleRequest(int request);
}

// 具体处理者A
class ConcreteHandlerA extends Handler {
    @Override
    public void handleRequest(int request) {
        if (request > 0 && request <= 10) {
            System.out.println("处理者A处理请求: " + request);
        } else if (successor != null) {
            successor.handleRequest(request);
        }
    }
}

// 具体处理者B
class ConcreteHandlerB extends Handler {
    @Override
    public void handleRequest(int request) {
        if (request > 10 && request <= 20) {
            System.out.println("处理者B处理请求: " + request);
        } else if (successor != null) {
            successor.handleRequest(request);
        }
    }
}
```

## 使用场景
1. 日志记录系统
2. 异常处理机制
3. 请求审批流程
4. 事件处理系统
5. 过滤器链

## 优缺点
### 优点
- 降低耦合度
- 增强了给对象指派职责的灵活性
- 可以动态地改变链内的成员或调动它们的次序

### 缺点
- 请求可能未被处理
- 性能会受到影响
- 不易观察运行时特征

## 实际应用
1. Servlet过滤器链
2. Spring Security的过滤器链
3. Apache Commons Chain
4. 日志框架中的日志级别处理

## 相关设计模式
- 装饰器模式
- 组合模式

## 参考资料
1. [设计模式：可复用面向对象软件的基础](https://book.douban.com/subject/1052241/)
2. [Head First设计模式](https://book.douban.com/subject/2243615/)
3. [Spring Security过滤器链](https://docs.spring.io/spring-security/reference/servlet/architecture.html)