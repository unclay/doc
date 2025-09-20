# CICD 文档

## 什么是 CICD

**CICD**（Continuous Integration and Continuous Deployment/Delivery）即持续集成与持续部署/交付，是现代软件开发的核心实践。

### 持续集成 (CI)
- **定义**：开发人员频繁地将代码变更合并到主干分支（通常每天多次）
- **核心实践**：
  - 自动触发代码编译和构建
  - 运行自动化测试套件（单元测试、集成测试）
  - 进行代码质量检查（静态代码分析、安全扫描）
- **价值**：快速发现集成错误，保证代码质量

### 持续部署/交付 (CD)
- **持续交付**：确保代码变更能够随时安全地部署到生产环境
- **持续部署**：自动将通过测试的代码变更部署到生产环境
- **关键环节**：
  - 自动化部署流程
  - 环境管理（开发、测试、预生产、生产）
  - 回滚机制和版本管理

### CICD 工具链
- **代码托管**: GitHub, GitLab, Bitbucket
- **CI/CD 平台**: GitHub Actions, GitLab CI, Jenkins, CircleCI
- **构建工具**: Maven, Gradle, npm, pnpm, Webpack
- **测试框架**: Jest, Mocha, JUnit, Selenium
- **部署工具**: Docker, Kubernetes, Ansible, Terraform
- **监控工具**: Prometheus, Grafana, ELK Stack

## 触发方式

### 1. 代码变更触发

#### 事件触发

```yml
on:
  push:
    branches: [ main, develop ]
    tags: [ 'v*' ]
  pull_request:
    branches: [ main ]
```

#### 定时触发

```yml
on:
  schedule:
    - cron: '0 2 * * *'  # 每天UTC时间2:00运行
```
- ​​定期任务​​：夜间构建、定期安全扫描等

#### 工作流调用（可复用工作流）
```yml
on:
  workflow_call:
    inputs:
      environment:
        required: true
        type: string
```

#### 手动触发

```yml
on:
  workflow_dispatch:
    inputs:
      environment:
        description: '部署环境'
        required: true
        default: 'staging'
        type: choice
        options:
          - staging
          - production
```

#### 外部事件触发

```yml
on:
  repository_dispatch:
    types: [deploy-request]
```
