# ByteMsg233 Language Support

VS Code 语言支持插件，为 [ByteMsg233](https://github.com/neko233/bytemsg233) 的 `.bmsg` Schema 文件提供语法高亮和编辑支持。

## 功能特性

- 语法高亮：关键字、类型、注释、字符串、数字等
- 括号匹配与自动闭合：`{}`、`[]`、`()`、`<>`
- i18n 注释高亮：`// "中文" | "English"` 双语注释分别着色
- 自定义文件图标

## 支持的关键字

| 分类 | 关键字 |
|------|--------|
| 结构 | `schema`, `package`, `enum`, `message` |
| 基础类型 | `uint32`, `uint64`, `int32`, `int64`, `float32`, `float64`, `string`, `bool`, `bytes` |
| 泛型 | `list<T>`, `map<K, V>` |

## 文件示例

```bmsg
// "用户协议" | "User Protocol"
schema UserProtocol

package com.example.model

// "用户状态" | "User Status"
enum UserStatus {
    ACTIVE = 0
    INACTIVE = 1
    BANNED = 2
}

// "用户信息" | "User Info"
message User {
    uint64 id = 1
    string name = 2
    int32 age = 3
    list<string> tags = 4
    UserStatus status = 5
    map<string, string> metadata = 6
}
```

## 安装

### 从 VSIX 安装

```bash
vsce package
code --install-extension bytemsg233-0.1.0.vsix
```

### 从源码构建

```bash
npm install
npm run compile
```

## 开发

```bash
# 安装依赖
npm install

# 打包 VSIX
npx @vscode/vsce package
```

## 许可证

MIT License
