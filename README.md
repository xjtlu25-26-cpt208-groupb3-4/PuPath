# PuPath（智游西浦）

PuPath 是一个面向西交利物浦大学（XJTLU）SIP 校区的移动端优先校园导览 Web 应用，聚焦“地图 + 导览 + 推荐 + 打卡 + 故事卡”的一体化体验。

- 目标用户：新生、在校生、访客、教职工
- 形态：PWA（可安装到桌面）
- 部署方式：GitHub Pages

---

## 核心功能

### 1. 地图与导航
- 高德地图（AMap）底图与定位
- 校园 POI 分层展示（学习空间 / 服务点 / 休闲点 / 猫咪点 / 花卉点）
- 点击地图点位可直接发起站内导航
- 跨校区导航优先地下通道策略（含南出口接驳段）
- 浏览器内置语音导航播报（Web Speech API）

### 2. 导览（Tours）
- 基础导览、主题导览、自定义导览
- 路线详情、进度跟踪、手动到站打点
- 地图与导览页联动

### 3. 推荐与详情
- 推荐分类浏览（如美食、摄影、校园猫咪、花卉、博物馆等）
- 点位详情页（图片、开放时间、标签、关联路线）
- 点位故事卡（地点叙事 + 推荐建议）

### 4. 打卡与收藏玩法
- 定位打卡（每日 1 次）
- 宝藏收集（Captain Bird / XJTLU Bear，蓝/紫/金稀有度）
- 徽章系统与自动解锁逻辑

### 5. 我的与无障碍
- 收藏、想去、去过、最近浏览
- 无障碍设置（字体档位、高对比度、读屏辅助）
- 清除本地记录（全局本地数据重置）

---

## 技术栈

- **前端框架**：React 19 + TypeScript
- **构建工具**：Vite 7
- **路由**：React Router 7
- **状态管理**：Zustand
- **国际化**：i18next + react-i18next
- **地图能力**：AMap JS API（主）+ MapLibre（回退渲染）
- **样式**：Tailwind CSS
- **PWA**：vite-plugin-pwa
- **测试**：Vitest、Playwright

---

## 项目结构

```text
PuPath/
├─ src/
│  ├─ app/                 # 应用入口与全局壳层
│  ├─ components/          # 组件（地图、UI、布局、通用）
│  ├─ config/              # 运行时配置、校园中心坐标
│  ├─ data/                # 本地数据源（pois/routes/recommendations/...）
│  ├─ hooks/               # 业务 hooks（天气、徽章自动解锁等）
│  ├─ locales/             # 中英文语言包
│  ├─ pages/               # 页面（Home/Map/Tours/Discover/My/...）
│  ├─ router/              # 路由定义
│  ├─ services/            # 地图与天气服务
│  ├─ stores/              # Zustand stores
│  ├─ types/               # TS 类型定义
│  └─ utils/               # 工具函数（坐标、存储、进度计算等）
├─ public/                 # 静态资源（图标、图片等）
├─ .github/workflows/      # GitHub Pages 自动部署工作流
└─ dist/                   # 构建产物
```

---

## 本地开发

### 1. 环境要求
- Node.js 20+
- npm 10+

### 2. 安装依赖
```bash
npm install
```

### 3. 配置环境变量
复制 `.env.example` 为 `.env`：

```env
VITE_MAP_PROVIDER=amap
VITE_AMAP_KEY=
VITE_AMAP_SECURITY_JS_CODE=
VITE_MAPTILER_KEY=
VITE_WEATHER_PROVIDER=openmeteo
```

说明：
- 当前推荐使用 `VITE_MAP_PROVIDER=amap`
- 坐标体系按 **GCJ-02** 维护（与高德一致）
- `openmeteo` 天气接口默认无需 key

### 4. 启动开发服务器
```bash
npm run dev
```

### 5. 生产构建与预览
```bash
npm run build
npm run preview
```

---

## npm 脚本

```bash
npm run dev        # 本地开发
npm run build      # TypeCheck + 生产构建
npm run preview    # 预览构建产物
npm run typecheck  # 仅类型检查
npm run lint       # ESLint
npm run test       # Vitest 监听模式
npm run test:run   # Vitest 单次执行
npm run e2e        # Playwright E2E
```

---

## 部署（GitHub Pages）

本仓库已内置自动部署工作流：
- 文件：`.github/workflows/deploy.yml`
- 触发：push 到 `main`
- 发布目录：`dist/`

### 首次启用步骤
1. 打开仓库 `Settings` → `Pages`
2. Source 选择 `GitHub Actions`
3. 推送 `main` 分支后，等待 `Deploy PuPath to GitHub Pages` 完成

### 手动应急发布（可选）
若 Actions 网络受限，可本地 `npm run build` 后，将 `dist` 内容手动上传到发布分支/发布目录。

---

## 性能说明

已做首屏优化：
- 地图样式改为按需加载（仅进入地图相关页面才加载）
- PWA 预缓存排除地图大包，降低首次安装与首开体积

---

## 发布前建议检查

- 地图定位、回到当前位置、跨校区地下通道导航
- 中英文切换（含点位标签、故事卡、推荐文案）
- 定位打卡（日限 1 次）与宝藏/徽章联动
- 微信内置浏览器（iOS/Android）兼容性
- GitHub Pages 线上资源与缓存更新

---

## 声明

本项目用于课程/演示场景，地图数据、路线策略与点位信息会持续迭代优化。
