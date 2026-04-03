# MGILT Website 项目进度

## 项目信息
- **项目路径**: `g:/claude code/MGILT_Website - 副本/`
- **主文件**: `index.html` (单文件网站，含所有 HTML/CSS/JS)
- **编辑器文件**: `js/editor-3d.js` (Three.js ES6 module)
- **本地服务器**: http://localhost:8806

---

## 已完成功能

### 导航结构
- 左侧：搜索图标 + MGILT logo（居中对称）
- 中间：首页 | 模块系统 | 空间灵感 | 设计你的MGILT | 关于MGILT | 合作伙伴
- 右侧：用户图标

### 首页 Hero 动画
- 六边形图片切片组合：三张本地图片（首页01/02/03）
- 动画三轮切换：每轮六边形数量和布局变化
- 左下角显示北京时间日期（格式 MM/DD）
- 导航栏在动画期间隐藏，动画结束后显示

### 空间灵感页面
- 左右交替图文布局：图片 75% 宽，文字 25% 宽
- 图片黑白 → hover 彩色效果
- 玻璃态半透明左右箭头切换图片
- 底部 dots 指示器
- 5 个真实项目数据
- 标签筛选功能：全部/商业空间/居住空间/教育空间/公共空间
- 文字区域背景为毛玻璃效果

### 模块系统页面
- Hero 区域：The System / 六边形模块化系统
- 对比表格：传统搭建 vs MGILT
- 六大核心模块展示
- 四步构建流程：步骤和图片高度统一，图片淡入淡出切换
- 六边形动画区域延伸至页面左右边缘
- 技术规格三列参数列表居中显示

### 编辑器 (MGILT 空间设计台)

#### 基础功能
- 标题：MGILT 空间设计台
- 六大基础模块可放置在六边形网格上
- 左键点击放置模块，右键点击移除模块
- Ctrl+Z 撤销功能
- 日光/夜景切换

#### 推荐组合
- 下拉菜单提供6种预设场景：咖啡店、餐厅外摆、办公交流、学校庭院、休闲 lounge、零售店铺
- 选择后自动生成对应模块布局

#### 场景元素功能
- 独立的面板区域，支持展开/收起
- 7种场景元素类型：
  - 阳伞（models/阳伞2.glb）
  - 四人桌椅组合（models/四人桌椅组合.glb）
  - 单人高座椅组合（models/单人高座椅组合.glb）
  - 小圆桌（models/小圆桌.glb）
  - 商务人01（models/商务人01.glb）
  - 商务人02（models/商务人02.glb）
  - 商务人03（models/商务人03.glb）
- 支持：放置、选择、拖拽移动、右键删除、旋转（R键或↻按钮）
- 元素可放置在地面或模块表面上

#### 鼠标操作
- 中键按住：旋转视图
- 右键按住：平移视图
- 滚轮：放大/缩小
- ESC：退出当前选中状态和预览

#### 交互逻辑
- 默认情况：不显示模块预览
- 选择模块后：显示模块预览
- 选择场景元素类型后：显示元素预览
- 放置模式：左键点击放置
- 选择模式：左键点击选中，右键删除，拖拽移动

### 用户中心 (我的设计页面)
- 头像：默认显示用户名首字母，点击可上传自定义图片
- 用户名：点击可编辑，回车保存
- 设计卡片：显示截图预览或六边形模块图标
- 删除：右上角悬停显示 ×，二次确认后删除

### 设计管理
- 保存：弹出居中的模态框输入方案名称
- 更新：从"我的设计"点击编辑后，可点击"更新"按钮保存修改
- 删除：卡片右上角悬停显示 × 按钮，二次确认后删除

### 登录系统
- 手机验证码登录（mock code: 1234）
- 手机快速注册
- localStorage 存储：session、users、designs

### 合作伙伴页面
- Hero 区域：flat-topped 六边形网格背景
- 六边形从中心向外扩散的光效（边框变亮）
- 市场机会、产品优势、盈利模式、品牌支持等模块
- 合作伙伴申请表单

---

## 技术备注

### ES6 模块函数暴露
由于 `editor-3d.js` 是 ES6 模块，需要将函数暴露到 window 对象才能在 HTML 中调用：
```javascript
window.navigateTo = navigateTo;           // 路由跳转
window.loadDesignToEditor = loadDesignToEditor;  // 加载设计
window.showSaveModal = showSaveModal;     // 显示保存弹窗
window.showUpdateModal = showUpdateModal; // 显示更新弹窗
window.doSaveDesign = doSaveDesign;       // 执行保存/更新
window.initCasesNew = initCasesNew;       // 空间灵感初始化
window.filterCasesNew = filterCasesNew;   // 空间灵感筛选
window.switchCaseImg = switchCaseImg;     // 图片切换
window.applyRecommend = applyRecommend;   // 应用推荐组合
window.toggleModulePalette = toggleModulePalette;       // 展开/收起模块面板
window.toggleSceneElementPalette = toggleSceneElementPalette; // 展开/收起场景元素面板
window.selectSceneElementType = selectSceneElementType; // 选择场景元素类型
window.rotateSelectedSceneElement = rotateSelectedSceneElement; // 旋转选中元素
window.clearAllSceneElements = clearAllSceneElements; // 清空所有场景元素
window.selectModule3D = selectModule3D; // 选择模块
```

### localStorage 数据结构
- `mgilt_session`: 当前用户会话
- `mgilt_users`: 所有注册用户
- `mgilt_designs`: 用户保存的设计方案（含 modules、screenshot）

### 图片本地化
- 首页 Hero 图片：`images/首页01.png`、`images/首页02.png`、`images/首页03.JPG`
- 空间灵感案例图片：`images/project1.jpg` ~ `images/project4-2.jpg`
- 模块系统模块图片：`images/module-*.jpg/png`

### Three.js 模型加载
- 使用 CDN 加载 Three.js 及 GLTFLoader
- 场景元素模型放在 `models/` 目录下

---

## 下一步计划

### 1. 头像上传功能（测试中）
- **问题**：点击头像后文件选择器无法弹出
- **位置**：`index.html` 第 1234 行
- **相关函数**：`handleDashAvatarChange`

### 2. 用户名编辑优化
- 确保点击用户名能正常变成输入框并保存

### 3. 更新功能测试
- 确认从"我的设计"编辑后能正确更新
- `completeDesignLoad` 后 `pendingDesignLoad` 被设为 null 已用 `window.currentEditingDesignId` 修复

### 4. 清理调试代码
- 移除所有 `console.log` 调试语句

### 5. 浏览器兼容性测试
- 确保功能在各浏览器（Chrome、Firefox、Safari、Edge）正常工作

### 6. 性能优化
- 优化3D渲染性能
- 考虑添加模块实例化

### 7. 移动端适配
- 编辑器在移动端的操作体验优化

---

## 最近修改记录

### 2026-04-03
- 移除右侧场景元素区块，保留左侧面板
- 添加场景元素拖拽移动功能（可拾取网格面和模块表面）
- 修改鼠标操作：中键旋转、右键平移
- 选择模式下隐藏模块预览
- ESC 退出当前选中状态和预览
- 缩放调整：所有场景元素缩放改为 2
- 添加商务人01/02/03 模型
- 模块面板缩略图改为对应颜色的正六边形

### 2026-04-02
- 修复首页 Hero 动画照片（替换为本地图片 images/首页01~03）
- 首页左下角改为显示北京实时日期
- 合作伙伴页面：flat-topped 六边形网格居中显示
- 合作伙伴页面：添加从中心向外扩散的边框光效
- 实现场景元素功能：阳伞模型的加载、放置、选择、旋转、删除
- 重构左侧边栏：模块面板和场景元素面板均改为可折叠的下拉样式
- 将6个模块选择改为下拉选择式
- 添加多种场景元素类型定义（桌椅组合、小圆桌、长椅、景观灯、绿植）
