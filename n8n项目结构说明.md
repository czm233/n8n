# n8n 项目结构说明

## 项目概述
n8n 是一个工作流自动化平台，采用 monorepo 架构，使用 pnpm workspace 管理多个包。

## 根目录结构

```
n8n/
├── 📁 packages/                    # 核心包目录
├── 📁 cypress/                     # E2E测试框架
├── 📁 docker/                      # Docker相关配置
├── 📁 scripts/                     # 构建和部署脚本
├── 📁 test-workflows/              # 工作流测试数据
├── 📁 assets/                      # 静态资源文件
├── 📁 patches/                     # 第三方包补丁
├── 📁 .github/                     # GitHub Actions配置
├── 📁 .devcontainer/               # 开发容器配置
└── 📄 配置文件                      # 各种配置文件
```

## 详细目录结构

### 📁 packages/ - 核心包目录

#### 📁 @n8n/ - 共享工具包
```
@n8n/
├── ai-workflow-builder/            # AI工作流构建器
├── api-types/                      # API类型定义
├── backend-common/                 # 后端通用工具
├── backend-test-utils/             # 后端测试工具
├── benchmark/                      # 性能基准测试
├── client-oauth2/                  # OAuth2客户端
├── codemirror-lang/               # CodeMirror语言支持
├── config/                         # 配置管理
├── constants/                      # 常量定义
├── db/                            # 数据库相关
├── decorators/                    # 装饰器
├── di/                            # 依赖注入
├── errors/                        # 错误处理
├── eslint-config/                 # ESLint配置
├── extension-sdk/                 # 扩展SDK
├── imap/                          # IMAP协议支持
├── json-schema-to-zod/           # JSON Schema转Zod
├── nodes-langchain/              # LangChain节点
├── permissions/                   # 权限管理
├── storybook/                     # Storybook配置
├── task-runner/                   # 任务运行器
├── typescript-config/             # TypeScript配置
├── utils/                         # 通用工具
└── vitest-config/                 # Vitest配置
```

#### 📁 core/ - 核心引擎
```
core/
├── src/
│   ├── binary-data/               # 二进制数据处理
│   ├── encryption/                # 加密功能
│   ├── errors/                    # 错误处理
│   ├── execution-engine/          # 执行引擎
│   ├── instance-settings/         # 实例设置
│   ├── nodes-loader/              # 节点加载器
│   └── utils/                     # 核心工具
└── test/                          # 测试文件
```

#### 📁 cli/ - 命令行接口
```
cli/
├── src/
│   ├── auth/                      # 认证模块
│   ├── commands/                  # CLI命令
│   ├── controllers/               # 控制器
│   ├── credentials/               # 凭据管理
│   ├── databases/                 # 数据库
│   ├── executions/                # 执行管理
│   ├── middlewares/               # 中间件
│   ├── modules/                   # 模块
│   ├── services/                  # 服务
│   ├── user-management/           # 用户管理
│   └── webhooks/                  # Webhook处理
└── bin/                           # 可执行文件
```

#### 📁 nodes-base/ - 基础节点包
```
nodes-base/
├── credentials/                   # 凭据定义 (400+个)
│   ├── icons/                     # 凭据图标
│   └── test/                      # 凭据测试
├── nodes/                         # 节点定义 (300+个)
│   ├── Airtable/                  # Airtable集成
│   ├── Slack/                     # Slack集成
│   ├── Google/                    # Google服务
│   ├── Microsoft/                 # Microsoft服务
│   ├── Transform/                 # 数据转换
│   ├── Webhook/                   # Webhook节点
│   └── ...                        # 其他300+个节点
├── utils/                         # 节点工具
└── types/                         # 类型定义
```

#### 📁 frontend/ - 前端应用
```
frontend/
├── editor-ui/                     # 主编辑器UI
│   ├── src/
│   │   ├── components/            # Vue组件
│   │   ├── views/                 # 页面视图
│   │   ├── stores/                # Pinia状态管理
│   │   ├── composables/           # Vue组合式API
│   │   ├── plugins/               # Vue插件
│   │   ├── styles/                # 样式文件
│   │   └── utils/                 # 工具函数
│   └── public/                    # 静态资源
└── @n8n/                         # 前端共享包
    ├── design-system/             # 设计系统
    ├── composables/               # 组合式API
    ├── stores/                    # 状态管理
    ├── i18n/                      # 国际化
    ├── rest-api-client/           # REST API客户端
    └── chat/                      # 聊天功能
```

#### 📁 workflow/ - 工作流引擎
```
workflow/
├── src/
│   ├── execution/                 # 执行逻辑
│   ├── expressions/               # 表达式处理
│   ├── nodes/                     # 节点处理
│   └── utils/                     # 工作流工具
└── test/                          # 测试文件
```

#### 📁 extensions/ - 扩展功能
```
extensions/
└── insights/                      # 洞察功能
```

#### 📁 testing/ - 测试框架
```
testing/
├── containers/                    # 测试容器
└── playwright/                    # Playwright测试
```

#### 📁 node-dev/ - 节点开发工具
```
node-dev/
├── src/                           # 源代码
├── templates/                     # 模板文件
└── commands/                      # 开发命令
```

### 📁 cypress/ - E2E测试
```
cypress/
├── e2e/                          # E2E测试用例
├── fixtures/                      # 测试数据
├── pages/                         # 页面对象
├── support/                       # 测试支持
├── utils/                         # 测试工具
├── composables/                   # 测试组合函数
└── scripts/                       # 测试脚本
```

### 📁 docker/ - Docker配置
```
docker/
└── images/
    ├── n8n/                       # n8n应用镜像
    └── n8n-base/                  # 基础镜像
```

### 📁 scripts/ - 构建脚本
```
scripts/
├── build-n8n.mjs                  # 构建脚本
├── dockerize-n8n.mjs              # Docker化脚本
├── format.mjs                      # 格式化脚本
├── reset.mjs                       # 重置脚本
└── scan-n8n-image.mjs             # 镜像扫描
```

### 📁 test-workflows/ - 工作流测试
```
test-workflows/
├── workflows/                      # 测试工作流 (200+个)
├── snapshots/                      # 测试快照
├── testData/                       # 测试数据
└── skipList.json                   # 跳过列表
```

### 📁 assets/ - 静态资源
```
assets/
├── n8n-logo.png                   # n8n Logo
├── n8n-screenshot.png             # 应用截图
└── n8n-screenshot-readme.png      # README截图
```

### 📁 patches/ - 第三方包补丁
```
patches/
├── bull@4.16.4.patch              # Bull队列补丁
├── element-plus@2.4.3.patch       # Element Plus补丁
├── pdfjs-dist@5.3.31.patch        # PDF.js补丁
└── ...                            # 其他补丁文件
```

### 📁 .github/ - GitHub配置
```
.github/
├── workflows/                      # GitHub Actions
├── ISSUE_TEMPLATE/                 # Issue模板
├── actions/                        # 自定义Actions
└── scripts/                        # GitHub脚本
```

### 📁 .devcontainer/ - 开发容器
```
.devcontainer/
├── Dockerfile                      # 容器Dockerfile
├── devcontainer.json               # 容器配置
└── docker-compose.yml              # 容器编排
```

## 主要配置文件

- `package.json` - 项目配置和脚本
- `turbo.json` - Turbo构建配置
- `pnpm-workspace.yaml` - pnpm工作区配置
- `biome.jsonc` - Biome代码格式化配置
- `tsconfig.json` - TypeScript配置
- `jest.config.js` - Jest测试配置

## 项目特点

1. **Monorepo架构**: 使用pnpm workspace管理多个包
2. **模块化设计**: 核心功能分离到不同包中
3. **丰富的集成**: 400+个节点和凭据
4. **完整的测试**: 单元测试、E2E测试、性能测试
5. **现代化工具链**: TypeScript、Vue 3、Turbo、Biome
6. **容器化支持**: Docker镜像和开发容器
7. **扩展性**: 支持自定义节点和凭据开发

## 开发工作流

1. **开发环境**: 使用 `pnpm dev` 启动开发服务器
2. **构建**: 使用 `pnpm build` 构建所有包
3. **测试**: 使用 `pnpm test` 运行测试
4. **格式化**: 使用 `pnpm format` 格式化代码
5. **Docker**: 使用 `pnpm build:docker` 构建Docker镜像
