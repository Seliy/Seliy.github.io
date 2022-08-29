## 盒子模型

### 盒子模型的组成
* 盒子模型由content(内容),padding(内边距),margin(外边距),border(边框)组成
#### 边距
* border
* 属性值
| value              | explain                                        |
| ------------------ | ---------------------------------------------- |
| none               | 不会被显示                                       |
| hidden             | 隐藏边框，IE不支持                               |
| dotted             | 点线                                            |
| dashed             | 虚线                                           |
| solid              | 实线                                           |
| double              | 双线                                          |
| groove              | 3D凹槽                                         |
| ridge              | 3D凸槽                                          |
| inset              | 3D凹边                                         |
| outset              | 3D凸边                                        |

#### 内边距
* padding-top
* padding-bottom
* padding-left
* padding-right

#### 外边距
* margin-top
* margin-bottom
* margin-left
* margin-right
### 有几种模型
* W3C盒子模型，又称'标准盒子模型'，元素所占总宽/高 = content(width/height) + padding + border + margin
* IE盒子模型，又称'怪异盒子模型'，元素所占总宽/高 = content(包含 width/height + padding + border) + margin
