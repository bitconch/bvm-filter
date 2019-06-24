# bvm_filter

![](misc/rbpf_256.png)

Bitconch Virutl Machine, 用Rust编写的eBPF解释器（用户空间）。

BVM虚拟机

## Description

此包含用于执行eBPF程序的虚拟机。 与_Berkeley Packet Filter_中一样，BPF是一种最初为BSD系统开发的类似汇编的语言，用于使用tcpdump等工具过滤内核中的数据包，以避免无用的副本到用户空间。 它后来移植到Linux，在那里它演变成eBPF（_extended_ BPF）。 eBPF运行速度更快，功能更多。 虽然BPF程序最初打算在内核中运行，但此crate的虚拟机允许在用户空间应用程序中运行它;它包含一个解释器，一个用于eBPF程序的x86_64 JIT编译器，以及一个反汇编程序。

该软件基于Rich Lane的[uBPF软件]（https://github.com/iovisor/ubpf/），的功能基本相同，但用C语言编写。

该软件包应该在Linux，MacOS X上编译和运行，并将在以后支持Windows。

## Link to the crate

这个包可以从[crates.io]（https://crates.io/crates/bvm_filter）获得，所以它应该开箱即用，只需将它作为依赖项添加到你的`Cargo.toml`文件中。

```toml
[dependencies]
bvm_filter = "1.0.0"
```

您还可以使用此GitHub存储库中的开发版本。 这应该就像把它放在你的`Cargo.toml`中一样简单。

```toml
[dependencies]
bvm_filter = { git = "https://github.com/bitconch/bvm_filter" }
```

当然，如果您愿意，可以在本地克隆它，可能会破坏板条箱，
然后在`Cargo.toml`中指出本地版本的路径。

```toml
[dependencies]
bvm_filter = { path = "path/to/bvm_filter" }
```

然后在源代码中指出您要使用包：

```rust,ignore
extern crate bvm_filter;
```

