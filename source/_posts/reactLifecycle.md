---
title: react生命周期
date: 2024-07-18 15:51:51
tags: [react]
cover: https://cdn.jsdelivr.net/gh/darkside7h/cdn-repo@v1.0.2/dreams_dont_work_unless_you_do_2-wallpaper-1280x720.jpg
---

## react 生命周期图示

![](./images/react16before.webp)

![](./images/react16after.webp)

React 类组件有几个重要的生命周期方法，可以分为三个主要阶段：**挂载（Mounting）**、**更新（Updating）** 和 **卸载（Unmounting）**。在每个阶段，React 都提供了一些特定的方法来控制组件的行为。

### **1. 挂载阶段（Mounting）**

这是组件第一次被创建和插入到 DOM 中时的过程。关键的生命周期方法有：

- **constructor(props)**：构造函数，初始化状态（state），绑定方法，以及通过 props 传入父组件的数据。这个阶段不能进行副作用操作。
- **static getDerivedStateFromProps(nextProps, prevState)**：在渲染前根据新的 props 修改状态（state）。它很少用，因为它会在每次重新渲染时被调用。
- **render()**：渲染组件的 UI。
- **componentDidMount()**：组件挂载完成后调用，可以进行副作用操作，比如网络请求、DOM 操作或订阅事件。这个方法只执行一次。

### **2. 更新阶段（Updating）**

- 组件的 props 或 state 发生变化时会触发更新。关键的生命周期方法有：  
  **static getDerivedStateFromProps(nextProps, prevState)**：和挂载阶段一样，这个方法在更新阶段也会被调用，用于根据新的 props 更新 state。
- **shouldComponentUpdate(nextProps, nextState)**：在组件重新渲染之前调用，用于决定是否允许组件更新。通过返回 false，可以阻止重新渲染。通常用于优化性能。
- **render()**：每次更新都会触发 render 方法，重新渲染组件的 UI。
- **getSnapshotBeforeUpdate(prevProps, prevState)**：在 DOM 更新前调用，用于捕获一些信息，比如滚动位置等，返回的值会作为 componentDidUpdate 的参数之一。
- **componentDidUpdate(prevProps, prevState, snapshot)**：组件更新后调用，可以进行 DOM 操作或网络请求等副作用。注意这里可以拿到上一次的 props 和 state，以及 getSnapshotBeforeUpdate 的返回值。

### 3. 卸载阶段（Unmounting）

当组件从 DOM 中被移除时触发。关键的生命周期方法有：

- **componentWillUnmount()**：组件卸载之前调用，用于执行清理工作，比如取消订阅、清理计时器、取消网络请求等。

### 总结

- **挂载阶段**：constructor()、getDerivedStateFromProps()、render()、componentDidMount()
- **更新阶段**：getDerivedStateFromProps()、shouldComponentUpdate()、render()、getSnapshotBeforeUpdate()、componentDidUpdate()
- **卸载阶段**：componentWillUnmount()

从 React 16.3 开始，有一些旧的生命周期方法被弃用，比如 componentWillMount() 和 componentWillReceiveProps()，新的生命周期方法更加可靠和直观，避免了很多潜在的错误。
