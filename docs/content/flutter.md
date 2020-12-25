**flutter开发原则：**
1. 上层 widget 向下层 widget 传递约束条件；
1. 下层 widget 向上层 widget 传递大小信息。
1. 上层 widget 决定下层 widget 的位置。
https://flutter.cn/docs/development/ui/layout/constraints

**状态管理**
1. 如果状态是用户数据，如复选框的选中状态、滑块的位置，则该状态最好由父Widget管理。
1. 如果状态是有关界面外观效果的，例如颜色、动画，那么状态最好由Widget本身来管理。
1. 如果某一个状态是不同Widget共享的则最好由它们共同的父Widget管理。
1. ps: 如果不确定到底该怎么管理状态，那么推荐的首选是在父widget中管理（灵活会显得更重要一些）

**建议1**

建议读者在需要制定一些精确的偏移时应优先使用FractionalOffset，因为它的坐标原点和布局系统相同，能更容易算出实际偏移

**一个很重要的widget： InheritedWidget**