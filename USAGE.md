# 如何在项目中使用 flutter_reactive_ble

## 方式一：使用 Git 依赖（推荐）

**重要**：由于包在仓库的子目录中，必须指定 `path` 参数。

在你的 Flutter 项目的 `pubspec.yaml` 中添加：

```yaml
dependencies:
  flutter_reactive_ble:
    git:
      url: https://github.com/你的用户名/flutter_reactive_ble.git
      ref: master  # 使用分支名
      path: packages/flutter_reactive_ble  # 指定包所在的子目录
```

### 使用特定版本/标签

```yaml
dependencies:
  flutter_reactive_ble:
    git:
      url: https://github.com/你的用户名/flutter_reactive_ble.git
      ref: v5.4.0  # 使用标签
      path: packages/flutter_reactive_ble
```

### 使用特定提交

```yaml
dependencies:
  flutter_reactive_ble:
    git:
      url: https://github.com/你的用户名/flutter_reactive_ble.git
      ref: abc123def456  # 使用提交哈希
      path: packages/flutter_reactive_ble
```

## 方式二：使用本地路径依赖（开发时）

```yaml
dependencies:
  flutter_reactive_ble:
    path: ../flutter_reactive_ble/packages/flutter_reactive_ble
```

## 方式三：发布到 pub.dev（如果已发布）

```yaml
dependencies:
  flutter_reactive_ble: ^5.4.0
```

## 安装依赖

添加依赖后，运行：

```bash
flutter pub get
```

## 使用示例

```dart
import 'package:flutter_reactive_ble/flutter_reactive_ble.dart';

final flutterReactiveBle = FlutterReactiveBle();

// 扫描设备
flutterReactiveBle.scanForDevices(
  withServices: [],
  scanMode: ScanMode.lowLatency,
).listen((device) {
  print('发现设备: ${device.name}');
});
```

## 注意事项

1. **Git 仓库访问**：确保 GitHub 仓库是公开的，或者配置 SSH 密钥访问私有仓库
2. **版本管理**：建议在 GitHub 上创建 release 标签，便于版本管理
3. **依赖解析**：使用 Git 依赖时，子包（`reactive_ble_mobile` 和 `reactive_ble_platform_interface`）会自动解析
4. **Flutter 版本要求**：本项目需要 Flutter >= 3.29.2
