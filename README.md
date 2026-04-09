[English](README_EN.md) | 中文

# 逆向工程技能集 (Reverse Engineering Skills)

逆向工程分析技能，支持 40+ 种 AI 编程工具。

**专为 [IDA-NO-MCP](https://github.com/P4nda0s/IDA-NO-MCP) 设计** - 从 IDA 导出反编译结果，然后使用 AI 编程工具进行分析。

## 工作流程

1. **从 IDA 导出** - 使用 [IDA-NO-MCP](https://github.com/P4nda0s/IDA-NO-MCP) 插件 (`Ctrl-Shift-E`)
2. **打开导出目录** - 使用 AI 编程工具打开
3. **使用技能分析** - 分析符号和数据结构

### 导出目录结构 (由 IDA-NO-MCP 生成)

```
export_dir/
├── decompile/              # 反编译的 C 代码
│   ├── 0x401000.c          # 每个函数一个文件，以十六进制地址命名
│   ├── 0x401234.c
│   └── ...
├── decompile_failed.txt    # 反编译失败的函数列表
├── decompile_skipped.txt   # 跳过的函数列表
├── strings.txt             # 字符串表 (地址, 长度, 类型, 内容)
├── imports.txt             # 导入表 (地址:函数名)
├── exports.txt             # 导出表 (地址:函数名)
└── memory/                 # 内存十六进制转储 (1MB 分块)
```

## 包含的技能

| 技能 | 描述 |
|------|------|
| `rev-symbol` | 从导出表/导入表或反编译代码分析函数符号 |
| `rev-struct` | 从反编译函数重建数据结构 |
| `rev-frida` | 使用现代 Frida API 生成动态插桩脚本 |

## 安装

```bash
npx skills add P4nda0s/reverse-skills
```

### 安装选项

```bash
# 列出可用技能
npx skills add P4nda0s/reverse-skills --list

# 安装到全局（所有项目可用）
npx skills add P4nda0s/reverse-skills -g

# 安装到指定 agent
npx skills add P4nda0s/reverse-skills -a claude-code
npx skills add P4nda0s/reverse-skills -a cursor

# 安装指定技能
npx skills add P4nda0s/reverse-skills --skill rev-symbol

# 安装到所有 agent
npx skills add P4nda0s/reverse-skills --all
```

### 更新与卸载

```bash
# 检查更新
npx skills check

# 更新
npx skills update

# 卸载
npx skills remove rev-symbol rev-struct
```

## 使用方法

### 分析符号

```
/rev-symbol sub_401000
```

### 重建数据结构

```
/rev-struct sub_401000
```

## 目录结构

```
reverse-skills/
├── skills/
│   ├── rev-symbol/
│   │   └── SKILL.md      # 符号分析技能
│   └── rev-struct/
│       └── SKILL.md       # 结构重建技能
├── README.md
└── README_EN.md
```

## 许可证

MIT
