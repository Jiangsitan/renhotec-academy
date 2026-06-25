# Renhotec Academy - 企业员工培训与考试系统

## 项目概述

Renhotec Academy 是一个企业员工培训与考试系统，旨在帮助企业高效管理员工培训流程，提升员工技能水平。

### 核心功能

- 📚 **在线学习**：支持视频、文档（PPT/PDF）等多种课程形式
- 📝 **考试测评**：自动评分 + 导师批改的混合阅卷模式
- 📊 **进度追踪**：实时监控员工学习进度
- 👥 **角色管理**：管理员、导师、学员三级权限体系
- 🔔 **消息通知**：考试结果、课程完成等自动通知
- 📦 **批量导入**：支持 CSV 批量导入用户、课程和考试

---

## 功能说明

### 学员端

| 功能 | 说明 |
|------|------|
| 培训中心 | 按分类和系列浏览所有课程 |
| 视频学习 | 在线观看视频课程，自动记录学习进度 |
| 文档学习 | 阅读 PPT、PDF 等文档，达到最低学习时长后标记完成 |
| 课后考试 | 完成课程后参加考试，支持单选、多选、判断、填空、简答 |
| 考试记录 | 查看历史考试成绩和错题详情 |
| 错题复习 | 针对错题关联的课程进行复习 |
| 互动评论 | 对课程进行评论和讨论 |
| 个人中心 | 查看学习进度、考试成绩 |

### 导师端

| 功能 | 说明 |
|------|------|
| 待批改列表 | 查看分配给自己的待批改试卷 |
| 在线批改 | 对简答题和填空题进行人工评分 |
| 一键通过 | 批量审核通过所有客观题满分的试卷 |
| 学员管理 | 查看绑定学员的学习进度 |

### 管理端

| 功能 | 说明 |
|------|------|
| 课程管理 | 创建、编辑、删除课程（支持视频、文档） |
| 分类管理 | 管理课程分类（支持多级分类） |
| 系列管理 | 管理课程系列（培训主题） |
| 考试管理 | 创建考试、管理题目、设置及格分数 |
| 批量导入 | 支持 CSV 批量导入课程和考试 |
| 用户管理 | 管理学员、导师账户 |
| 导师绑定 | 配置导师-学员关系 |
| 学习进度 | 查看所有学员的学习进度统计 |
| 考试批改 | 审核待批改试卷 |
| 评论管理 | 管理课程评论 |
| 系统设置 | 配置系统名称、Logo 等 |
| 审计日志 | 查看系统操作记录 |

---

## 考试系统

### 题型支持

| 题型代码 | 题型名称 | 说明 |
|----------|----------|------|
| 1 | 单选题 | 单选，自动评分 |
| 2 | 多选题 | 多选，自动评分 |
| 3 | 判断题 | 判断对错，自动评分 |
| 4 | 简答题 | 主观题，需导师批改 |
| 5 | 填空题 | 按空位填写，需导师批改 |

### 考试特性

- **自动评分**：客观题（单选、多选、判断）自动评分
- **人工批改**：简答题和填空题由导师手动批改
- **防作弊**：全屏模式、页面切换检测、自动提交
- **多课程关联**：一个考试可关联多个课程，学员需全部完成才能考试
- **错题复习**：考试后可查看错题及关联课程
- **批量导入**：支持 CSV 批量导入考试和题目

---

## 技术栈

| 组件 | 技术 | 版本 |
|------|------|------|
| 后端框架 | Laravel | 13.x |
| PHP | PHP | 8.3 |
| 前端框架 | Nuxt | 3.x |
| UI 组件库 | Nuxt UI | 2.x |
| 数据库 | MySQL | 8.0 |
| 缓存 | Redis | 7.x |
| 对象存储 | 阿里云 OSS | - |
| 容器化 | Docker | 24.x |

---

## 项目结构

```
renhotec-academy/
├── academy_api/          # 后端 API（Laravel）
│   ├── app/
│   │   ├── Http/Controllers/Api/  # API 控制器
│   │   ├── Models/                # 数据模型
│   │   ├── Services/              # 业务服务
│   │   └── Jobs/                  # 异步任务
│   ├── database/
│   │   ├── migrations/            # 数据库迁移
│   │   └── seeders/               # 数据填充
│   ├── routes/
│   │   └── api.php                # API 路由
│   └── docker-compose.yml         # Docker 配置
├── academy_nuxt/         # 前端应用（Nuxt）
│   ├── components/                # 组件
│   │   ├── exam/                  # 考试相关组件
│   │   └── course/                # 课程相关组件
│   ├── pages/                     # 页面
│   │   ├── admin/                 # 管理后台
│   │   ├── exam/                  # 考试页面
│   │   └── course/                # 课程页面
│   ├── composables/               # 组合式函数
│   └── utils/                     # 工具函数
├── docker-compose.yml    # 整体 Docker 配置
└── README.md             # 项目文档
```

---

## 本地开发环境搭建

### 1. 克隆代码

```bash
git clone https://github.com/your-org/renhotec-academy.git
cd renhotec-academy
```

### 2. 后端启动

```bash
cd academy_api

# 安装依赖
composer install

# 配置环境
cp .env.example .env
# 编辑 .env 配置数据库连接

# 生成密钥
php artisan key:generate

# 运行迁移
php artisan migrate

# 填充初始数据
php artisan db:seed

# 创建存储链接
php artisan storage:link

# 启动服务
php artisan serve --host 0.0.0.0 --port 9000
```

### 3. 前端启动

```bash
cd academy_nuxt

# 安装依赖
npm install

# 配置环境
echo "NUXT_PUBLIC_API_BASE=http://localhost:9000/api" > .env

# 启动服务
npm run dev -- --host 0.0.0.0 --port 3000
```

---

## Docker 部署

### 1. 后端部署

```bash
cd academy_api

# 创建环境变量
cp .env.docker .env

# 启动服务
docker compose up -d

# 初始化数据库
docker compose exec api php artisan migrate --force
docker compose exec api php artisan db:seed --force
docker compose exec api php artisan storage:link
```

### 2. 前端部署

```bash
cd academy_nuxt

# 创建环境变量
cp .env.docker .env

# 启动服务
docker compose up -d
```

### 3. 服务地址

| 服务 | 地址 | 说明 |
|------|------|------|
| 后端 API | http://localhost:9000 | Nginx 反向代理 |
| 前端应用 | http://localhost:3000 | Nuxt 应用 |
| MySQL | localhost:3306 | 数据库 |
| Redis | localhost:6379 | 缓存 |

---

## API 文档

API 文档已生成为 OpenAPI 3.0 格式，文件位置：`academy_api/openapi.json`

### 导入到 Apifox

1. 打开 Apifox，创建新项目
2. 点击 "导入数据" -> "OpenAPI/Swagger"
3. 选择 `academy_api/openapi.json` 文件
4. 配置导入选项后点击 "导入"

### API 模块

| 模块 | 说明 |
|------|------|
| 认证 | 登录、登出、获取用户信息 |
| 课程系列 | 系列列表、系列详情 |
| 课程 | 课程列表、课程详情 |
| 学习进度 | 同步进度、完成文档、获取进度 |
| 考试 | 考试列表、考试详情、提交答卷 |
| 考试记录 | 考试记录、错题列表 |
| 管理后台 | 用户、分类、系列、课程、考试管理 |

---

## 更新日志

### 2026-06-24

#### 后端

- **题目类型字段改为数字**：1=单选, 2=多选, 3=判断, 4=简答, 5=填空
- **文件转换后更新文件大小**：PDF 转换完成后自动更新数据库中的 file_size 字段
- **填空题和简答题改为手动批改**：不再自动评分，由导师手动批改

#### 前端

- **填空题支持英文括号**：正则表达式同时支持中文括号（）和英文括号()
- **填空题输入框样式优化**：输入框大小与简答题一致（100% 宽度）
- **题目编辑弹窗优化**：关联课程下拉只显示当前考试关联系列的课程
- **修复删除题目问题**：修复删除题目未调用后端 API 的问题

### 2026-06-20

- **批量导入模板优化**：CSV 模板更新为 HTML 图片格式
- **移除 DOCX 导入功能**：简化导入流程

### 2026-06-15

- **PDF 预览性能优化**：使用 Range 请求按页加载
- **填空题内联渲染改进**：优化填空题的显示效果
- **考试未通过显示关联课程**：引导学员重新学习

---

## 常用命令

```bash
# 查看服务状态
docker compose ps

# 重启服务
docker compose restart

# 查看日志
docker compose logs -f api
docker compose logs -f web

# 数据库备份
docker exec renhotec-mysql mysqldump -u root -p renhotec_academy > backup_$(date +%Y%m%d).sql

# 数据库恢复
docker exec -i renhotec-mysql mysql -u root -p renhotec_academy < backup.sql

# 清理 Docker 缓存
docker system prune -a
```

---

## 相关链接

| 仓库 | 地址 | 说明 |
|------|------|------|
| 后端 API | https://github.com/Jiangsitan/renhotec-academy-api | Laravel 13 后端接口 |
| 前端应用 | https://github.com/Jiangsitan/renhotec-academy-nuxt | Nuxt 3 前端应用 |
| 主仓库 | https://github.com/Jiangsitan/renhotec-academy | 项目文档和部署配置 |

---

## 联系方式

| 项目 | 信息 |
|------|------|
| 项目负责人 | Lucas Jay |
| 邮箱 | 2434624535@qq.com |
| 文档更新日期 | 2026-06-24 |

---

## 许可证

本项目为私有项目，未经授权不得复制或分发。
