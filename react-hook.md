1. Overview

 - List State in Component Tree
 - 反直觉的时间上复用
 - 强制状态化时序(useAsync)
 - use

2. conf

- RenderProps/Hoc/Hook优势
- 自带状态管理机制useContext
- 阻止了class相关的骚操作
  - 保存状态
  
3. sucks

 - 极大的放大的过渲染的可能
 - useEffect依赖极度容易出错
  
4. 建议

- always useMemo
- React.useContext
- useCallback