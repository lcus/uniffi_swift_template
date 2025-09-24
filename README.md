
# Rust iOS Framework 构建工具

这是一个用于将 Rust 库编译成 iOS Framework 的自动化工具。该工具会自动处理编译过程，生成 Swift 绑定，并创建可在 iOS 项目中使用的 XCFramework。
- iOS 开发工具链

## 使用方法

1. 将 `make_framework` 可执行文件复制到您的 Rust 项目根目录（包含 Cargo.toml 的目录）

2. 确保文件具有执行权限：
   ```bash
   chmod +x make_framework
   ```

3. 运行构建工具：
   ```bash
   ./make_framework
   ```

## 工具功能

该工具会自动执行以下操作：

1. 从 Cargo.toml 中读取项目名称
2. 构建 Rust 动态库
3. 生成 Swift 语言绑定
4. 为以下 iOS 目标平台编译：
   - aarch64-apple-ios（iOS 设备）
   - aarch64-apple-ios-sim（iOS 模拟器）
5. 创建 XCFramework
6. 整理项目文件结构

## 输出文件

构建完成后，您可以在项目目录下找到：

- `ios/[ProjectName].xcframework`：可直接集成到 iOS 项目中的框架
- `ios/[ProjectName].swift`：Swift API 定义文件

## 注意事项

1. 确保您的 Rust 项目配置正确：
   - Cargo.toml 中必须包含有效的项目名称
   - 项目必须包含 lib.rs 文件
   - 必须正确配置 uniffi 绑定

2. 运行环境要求：
   - 必须在 macOS 系统上运行
   - 需要安装 Xcode 和 iOS 开发工具链
   - 需要安装 Rust 和相关工具链

3. 如果遇到权限问题，请确保：
   - 文件具有执行权限
   - 当前用户对项目目录有写入权限

## 集成到 iOS 项目

1. 将生成的 XCFramework 拖入您的 Xcode 项目
2. 在 "Frameworks, Libraries, and Embedded Content" 中将其设置为 "Embed & Sign"
3. 将生成的 Swift 文件添加到您的项目中
4. 现在您可以在 Swift 代码中使用 Rust 函数了
