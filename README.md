# ByteMsg233 Legacy Language Support

VS Code language support for legacy ByteMsg233 `.bmsg` schema files.

New ByteMsg233 projects should use `.bmsg.json`. JSON is the default DSL because message-heavy protocols stay easier to scan when top-level keys are message names. YAML remains supported, and this plugin remains useful for older `.bmsg` files and custom editor tooling experiments.

## Features

- Syntax highlighting for legacy `.bmsg` files
- Bracket matching and auto closing for `{}`, `[]`, `()`, `<>`
- i18n inline comment highlighting for `// "中文" | "English"`
- Custom file icon

## Recommended Schema Format

Use JSON for new files:

```json
{
  "schema": "bymsg/v1",
  "package": "com.example.model",
  "User": {
    "id": { "type": "uint64", "tag": 1 },
    "name": { "type": "string", "tag": 2 }
  }
}
```

Compile it with:

```bash
bytemsg233 compile user.bmsg.json -l typescript,csharp,go -o ./gen
```

## 支持的关键字

| 分类 | 关键字 |
|------|--------|
| 结构 | `schema`, `package`, `enum`, `message` |
| 基础类型 | `uint32`, `uint64`, `int32`, `int64`, `float32`, `float64`, `string`, `bool`, `bytes` |
| 泛型 | `list<T>`, `map<K, V>` |

## Legacy File Example

```bmsg
schema: bymsg/v1
package com.example.model

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
