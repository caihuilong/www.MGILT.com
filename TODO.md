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
- 六大核心模块展示（vanilla JS）
- 四步构建流程：步骤和图片高度统一，图片淡入淡出切换
- 六边形动画区域延伸至页面左右边缘
- 技术规格三列参数列表居中显示

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

### 编辑器 (设计你的MGILT)
- 标题：MGILT 空间设计台
- 已移除：橡皮擦按钮、填充按钮、对称按钮
- 新增"推荐组合"下拉菜单
- 保存/更新功能：自定义模态框（居中显示）

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
```

### localStorage 数据结构
- `mgilt_session`: 当前用户会话
- `mgilt_users`: 所有注册用户
- `mgilt_designs`: 用户保存的设计方案（含 modules、screenshot）

### 图片本地化
- 首页 Hero 图片：`images/首页01.png`、`images/首页02.png`、`images/首页03.JPG`
- 空间灵感案例图片：`images/project1.jpg` ~ `images/project4-2.jpg`
- 模块系统模块图片：`images/module-*.jpg/png`

---

## 下一步计划

### 1. 清理调试代码
- 移除所有 `console.log` 调试语句

### 2. 浏览器兼容性测试
- 确保功能在各浏览器（Chrome、Firefox、Safari、Edge）正常工作

### 3. 合作伙伴页面光效优化（如需）
- 当前光效：从中心向外扩散的边框变亮效果（8秒一轮）
- 可调整项：扩散速度、光效亮度、光效颜色

### 4. 其他可能的需求
- 性能优化
- SEO 优化
- 移动端适配优化

---

## 最近修改记录

### 2026-04-02 (本次会话)
- 修复首页 Hero 动画照片（替换为本地图片 images/首页01~03）
- 首页左下角改为显示北京实时日期
- 合作伙伴页面：flat-topped 六边形网格居中显示
- 合作伙伴页面：添加从中心向外扩散的边框光效

### 2026-04-01
- 完成空间灵感页面新设计（参考 mgilt-showcase）
- 下载 6 张真实图片到本地 images/ 文件夹
- 实现标签筛选功能（按 Category 过滤）
- 修复模块系统六边形动画（逐批显现效果）
- 空间灵感页面文字区域改为毛玻璃效果
