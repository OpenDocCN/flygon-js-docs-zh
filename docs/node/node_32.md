# V8

### 稳定度: 2 - 稳定

这个模块暴露了`node.js`内建的指定版本的 V8 的事件和接口。这些接口受上游（upstream）变化的影响，所以没有被稳定索引（stability index）所覆盖。

#### getHeapStatistics()

返回一个包含以下属性的对象。

```js
{
  total_heap_size: 7326976,
  total_heap_size_executable: 4194304,
  total_physical_size: 7326976,
  used_heap_size: 3476208,
  heap_size_limit: 1535115264
} 
```

#### setFlagsFromString(string)

设置额外的 V8 命令行标识。请谨慎使用；在虚拟机启动后改变设定可能会产生不可预测的行为，包括程序崩溃或数据丢失。或者它也可能什么都没有做。

当前`node.js`可用的 V8 选项，在运行`iojs --v8-options`命令的输出中显示。一个非官方，社区维护的配置列表：`https://github.com/thlorenz/v8-flags/blob/master/flags-0.11.md`。

用处：

```js
// Print GC events to stdout for one minute.
var v8 = require('v8');
v8.setFlagsFromString('--trace_gc');
setTimeout(function() { v8.setFlagsFromString('--notrace_gc'); }, 60e3); 
```