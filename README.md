# Flutter STU

[![CI](https://github.com/youth95/flutter_stu/actions/workflows/ci.yml/badge.svg)](https://github.com/youth95/flutter_stu/actions?query=workflow%3ACI)
[![Vercel](https://vercelbadge.vercel.app/api/youth95/flutter_stu)](https://vercel.com/youth95/flutter-stu)

用于学习 Flutter 各项特性的项目。在里面测试各种Flutter的【特技】。

# 国际化

https://flutter.cn/docs/development/accessibility-and-localization/internationalization

```bash
flutter pub add flutter_localizations --sdk=flutter
flutter pub add intl:any
```

# CICD

```yml
# This workflow uses actions that are not certified by GitHub.
# They are provided by a third-party and are governed by
# separate terms of service, privacy policy, and support
# documentation.

name: CI

on:
  push:
    branches: ['master']
  pull_request:
    branches: ['master']

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3
      - uses: subosito/flutter-action@v2
        with:
          flutter-version: '3.10.1'
          channel: 'stable'
      - run: flutter --version
      - run: flutter build web
      - run: ls build/web
      - uses: amondnet/vercel-action@v25
        continue-on-error: true
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          working-directory: build/web
          alias-domains: |
            flutter-stu.showcase.youth95.cn
```

# 媒体查询

- [ ] 通过媒体查询使用不同的布局

# 特性验证

- [ ] 长图文列表滚动
- [ ] 路由切换
- [ ] 下拉加载 / 刷新