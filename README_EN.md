English | [中文](README.md)

# Reverse Engineering Skills

Reverse engineering analysis skills, supporting 40+ AI coding agents.

**Designed to work with [IDA-NO-MCP](https://github.com/P4nda0s/IDA-NO-MCP)** - Export IDA decompilation results, then analyze with your AI coding agent.

## Workflow

1. **Export from IDA** using [IDA-NO-MCP](https://github.com/P4nda0s/IDA-NO-MCP) plugin (`Ctrl-Shift-E`)
2. **Open exported directory** with your AI coding agent
3. **Use skills** to analyze symbols and structures

### Exported Directory Structure (by IDA-NO-MCP)

```
export_dir/
├── decompile/              # Decompiled C code
│   ├── 0x401000.c          # One file per function, named by hex address
│   ├── 0x401234.c
│   └── ...
├── decompile_failed.txt    # Failed decompilation list
├── decompile_skipped.txt   # Skipped functions list
├── strings.txt             # String table (address, length, type, content)
├── imports.txt             # Import table (address:function_name)
├── exports.txt             # Export table (address:function_name)
└── memory/                 # Memory hexdump (1MB chunks)
```

### Function File Format (decompile/*.c)

```c
/*
 * func-name: sub_401000
 * func-address: 0x401000
 * callers: 0x402000, 0x403000    // Who calls this function
 * callees: 0x404000, 0x405000    // What this function calls
 */

int __fastcall sub_401000(int a1, int a2)
{
    // Decompiled code...
}
```

## Skills Included

| Skill | Description |
|-------|-------------|
| `rev-symbol` | Analyze function symbols from exports/imports or decompiled code |
| `rev-struct` | Reconstruct data structures from decompiled functions |
| `rev-frida` | Generate Frida hook scripts using modern Frida API |

## Installation

```bash
npx skills add P4nda0s/reverse-skills
```

### Options

```bash
# List available skills
npx skills add P4nda0s/reverse-skills --list

# Install globally (available across all projects)
npx skills add P4nda0s/reverse-skills -g

# Install to specific agents
npx skills add P4nda0s/reverse-skills -a claude-code
npx skills add P4nda0s/reverse-skills -a cursor

# Install a specific skill
npx skills add P4nda0s/reverse-skills --skill rev-symbol

# Install to all agents
npx skills add P4nda0s/reverse-skills --all
```

### Update & Remove

```bash
# Check for updates
npx skills check

# Update
npx skills update

# Remove
npx skills remove rev-symbol rev-struct
```

## Usage

### Analyze a Symbol

```
/rev-symbol sub_401000
```

### Reconstruct a Structure

```
/rev-struct sub_401000
```

## Directory Structure

```
reverse-skills/
├── skills/
│   ├── rev-symbol/
│   │   └── SKILL.md      # Symbol analysis skill
│   └── rev-struct/
│       └── SKILL.md       # Structure reconstruction skill
├── README.md
└── README_EN.md
```

## License

MIT
