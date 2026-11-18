## 安装
1. 需要 Android 8.0（API 26）及以上，常见 64 位手机下载 arm64 APK；x86_64 设备或模拟器用 x64 包。
2. 从 GitHub Releases 或官网下载页获取 APK，允许该安装来源后安装。
3. 首次启动选择在本机安装运行环境（预留约 1 GB 空间），或选择远程连接主机。
4. 为所选主机配置模型和凭据，然后开始对话。仅远程连接不需要安装本机运行环境。

## 最小可用示例
安装后进入「使用指南」逐项配置；本地引擎默认 PRoot 兼容启动。远程连接可填写 SSH 或 DSHarness Remote 地址，并确保主机侧已配置好模型渠道。

## 从源码构建（Linux x86_64）
```bash
git clone https://github.com/ccch1mneyyy/dsh-go.git
cd dsh-go

bash tooling/setup-toolchain.sh
source tooling/env.sh
flutter --version
java -version

bash runtime/build-runtime.sh arm64-v8a
DSH_BETA_TOKEN_FILE= bash tooling/build-apk.sh -f arm64 --keep-daemon
```
产物为 `app/build/app/outputs/flutter-apk/app-arm64-release.apk`。脚本默认安装 JDK 17、Flutter 3.47.7 和 Android SDK/NDK。依赖：Bash、Git、curl、tar、unzip、xz、Python 3、zstd、file、gpgv 等。