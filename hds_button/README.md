# hds_button

基于 HarmonyOS HdsTabs 的浮动迷你栏按钮组件，提供沉浸光感材质效果。

## 功能特性

- 基于 HdsTabs + barFloatingStyle 的浮动按钮
- 沉浸光感材质效果（Immersive / Adaptive）
- 可自定义图标、尺寸、材质、边距等参数
- 支持完全自定义按钮内容（@BuilderParam）
- 兼容 @ComponentV2 状态管理

## 安装

```bash
ohpm install hds_button
```

## 快速开始

### 基础用法

```typescript
import { HdsMiniBarButton } from 'hds_button'

HdsMiniBarButton({
  onButtonClick: () => {
    // 处理点击事件
  }
})
```

### 自定义图标和点击事件

```typescript
HdsMiniBarButton({
  iconResource: $r('sys.symbol.settings'),
  iconColor: [Color.Blue],
  iconSize: 24,
  onButtonClick: () => {
    console.info('设置按钮被点击')
  }
})
```

### 自定义尺寸

```typescript
HdsMiniBarButton({
  barWidth: 60,
  barHeight: 60,
  contentPadding: 10,
  // containerSize 自动计算: 60 + 10*4 = 100
})
```

### 自定义材质效果

```typescript
import { hdsMaterial } from '@kit.UIDesignKit'

HdsMiniBarButton({
  materialType: hdsMaterial.MaterialType.TRANSLUCENT,
  materialLevel: hdsMaterial.MaterialLevel.LIGHT,
  maskColor: '#20FFFFFF',
  barBottomMargin: 12,
})
```

### 完全自定义按钮内容

```typescript
HdsMiniBarButton({
  onButtonClick: () => { /* ... */ }
}) {
  // 尾随闭包替换默认图标
  Image($r('app.media.my_icon'))
    .width(24)
    .height(24)
    .fillColor(Color.White)
}
```

## API 参考

### 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| barWidth | number | 50 | 按钮宽度 |
| barHeight | number | 50 | 按钮高度 |
| contentPadding | number | 8 | 内边距（防止光效裁切） |
| containerSize | SizeOptions | undefined | 容器大小（默认自动: barSize + padding*4） |
| iconResource | ResourceStr | $r('sys.symbol.plus') | 图标资源 |
| iconSize | number | 27 | 图标大小 |
| iconColor | ResourceColor[] | [Color.Gray] | 图标颜色数组 |
| maskColor | ResourceColor | Color.Transparent | 渐变遮罩颜色 |
| barBottomMargin | number | 8 | 按钮底部边距 |
| materialType | hdsMaterial.MaterialType | IMMERSIVE | 材质类型 |
| materialLevel | hdsMaterial.MaterialLevel | ADAPTIVE | 材质等级 |
| barPosition | BarPosition | BarPosition.End | 栏位置 |
| barOverlap | boolean | true | 栏是否重叠内容 |
| onButtonClick | (() => void) | undefined | 点击回调 |
| buttonContent | @BuilderParam | 默认图标 | 自定义按钮内容 |

## 系统要求

- HarmonyOS SDK: 6.1.0(23) 及以上
- DevEco Studio: 5.0 及以上

## 许可证

Apache-2.0
