# Codex AGENTS.md Template

一个面向中文用户的 Codex `AGENTS.md` 模板，用来约束 Codex 在项目中的沟通方式、工作方法、代码修改边界、调试流程、验证标准和高风险操作处理方式。

这个模板默认偏向 **中文沟通、Windows 环境和 Python 项目**，但并不强绑定这些技术栈。你可以根据自己的操作系统、主要语言、项目类型和团队规范修改对应章节。

## 适合谁使用

- 希望 Codex 默认用中文沟通的用户。
- 主要在 Windows 环境下开发，并希望命令示例优先使用 PowerShell 的用户。
- 经常处理 Python 项目，希望 Codex 先识别虚拟环境、依赖管理方式和测试命令的用户。
- 希望 Codex 在修改代码前先理解上下文，避免大范围无关重构的用户。
- 希望 Codex 明确区分“已验证通过”和“理论上应该可行”的用户。
- 希望对删除文件、强制覆盖、改写 Git 历史、修改配置等高风险操作设置更严格边界的用户。

## 设计目标

这个模板的目标不是提供唯一正确的 Codex 工作方式，而是提供一个更稳、更可审查、更安全的协作起点。

它强调：

- 先理解需求和上下文，再修改。
- 优先做最小必要改动。
- 遵循项目已有风格和约定。
- Python 项目中优先确认解释器和虚拟环境。
- 修 bug 时先确认复现路径和可能根因。
- 修改完成后尽量运行相关验证命令。
- 对高风险操作保持显式确认。
- 汇报时区分完成情况、改动内容、验证结果和剩余风险。

## 使用方式

### 全局使用

把 `AGENTS.md` 放到 Codex 配置目录下：

```powershell
Copy-Item -LiteralPath ".\AGENTS.md" -Destination "$env:USERPROFILE\.codex\AGENTS.md" -Force
```

然后重启 Codex，让全局规则生效。

### 项目内使用

也可以把 `AGENTS.md` 放到某个项目根目录下：

```powershell
Copy-Item -LiteralPath ".\AGENTS.md" -Destination "D:\your-project\AGENTS.md" -Force
```

项目内的 `AGENTS.md` 只影响该目录及其子目录。更深层目录如果还有自己的 `AGENTS.md`，通常会优先使用更靠近当前文件的规则。

## 建议先修改的地方

使用前建议至少检查这些章节：

- `Default language`：是否希望 Codex 默认使用中文。
- `Platform and language preference`：是否仍然以 Windows 和 Python 为主。
- `Python environment rules`：是否符合你的虚拟环境和依赖管理习惯。
- `Validation rules`：是否需要补充你的项目常用测试、lint、type check 或 build 命令。
- `Safety rules`：是否需要加入你自己的高风险操作边界。
- `Response format`：是否符合你希望 Codex 汇报工作的方式。

如果你主要使用前端、Go、Java、Rust、C++、Linux 或 macOS，可以保留整体工作方法，然后替换技术栈相关规则。

## 局限性

- 这个模板不是 OpenAI 官方模板。
- 默认偏向中文、Windows 和 Python 项目，其他技术栈需要调整。
- 它不会自动保证 Codex 的所有行为都符合预期，仍然需要用户 review 关键改动。
- 不同 Codex 版本或不同运行环境对 `AGENTS.md` 的解析细节可能存在差异。
- 对团队项目来说，建议结合项目 README、贡献指南、CI 配置和团队 code review 规范进一步修改。

## 仓库内容

```text
.
├── AGENTS.md
├── README.md
├── LICENSE
└── .gitignore
```

## 贡献

欢迎通过 Issue 或 Pull Request 交流改进建议，尤其是不同技术栈、不同操作系统、不同团队协作场景下的 `AGENTS.md` 实践。

## License

MIT License
