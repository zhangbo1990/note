# java 

## Lock and Condition

1. synchronized 已经实现了管程为何java还要提供lock和condition来实现管程？
    1. 在打破死锁三个条件第二个不可抢占条件时，synchronized占有了部分资源后继续获取其他资源