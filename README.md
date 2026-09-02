# [Flexible COBOL](https://plugins.jetbrains.com/plugin/34037-flexible-cobol/)
JetBrains IDE support for IBM Enterprise COBOL and GnuCOBOL: a full native parser, copybook-aware navigation, a GnuCOBOL compile-run-debug toolchain, PIC-to-Java/JSON mapping, and an embedded MCP server for AI agents. Supports fixed and free source format with automatic detection, EXEC SQL/CICS blocks with SQL language injection, and per-project dialect settings for both IBM Enterprise COBOL and GnuCOBOL.

**Flexible COBOL is under active development. Please leave a review, open a GitHub issue, or drop us an email — your feedback shapes the roadmap.**

## Core Features

### Language Support
* **Two dialects** — IBM Enterprise COBOL and GnuCOBOL, selected per project
* **Fixed and free source format**, auto-detected or set with the `>>SOURCE FORMAT` directive
* **Full native parser** built with Grammar-Kit and JFlex, covering all four divisions
* **Complete DATA DIVISION clause grammar** — levels 01-88, REDEFINES, OCCURS DEPENDING ON, PICTURE, and every other clause
* **All verb families** across the PROCEDURE DIVISION
* **COPY with REPLACING**, including partial-word replacement
* **EXEC SQL and EXEC CICS blocks** with SQL language injection for embedded statements
* **Verified against the NIST COBOL-85 conformance suite**: 391 programs, zero parse errors, at roughly 10,000 lines per second

### Copybook Intelligence
* **COPY navigation and resolution** across configurable copybook paths
* **REPLACING-aware rename and completion** for copybook members
* **Unresolved-COPY quick fix** — offered wherever a copybook path can't be resolved
* **Copybook usage search** across the project

### Navigation & Intelligence
* **Go to Declaration** for programs, paragraphs, sections, data items, and copybooks
* **Find Usages** with read/write access distinction
* **Cross-program data-item where-used** search
* **Call hierarchy** across CALL, PERFORM, and CICS LINK/XCTL
* **Go to Symbol**, **Structure View**, breadcrumbs, and code folding

### Editing
* **Position-aware, dialect-filtered completion** — suggestions match the active division and dialect
* **Quick documentation** for 57 verbs, PIC symbols, and CICS commands
* **10 inspections** with quick fixes
* **4 intentions**, including extract paragraph and add COPY
* **48 live templates**, including `4div`, `ws`, `01grp`, `pic9`, `88cond`, `ifel`, `evw`, `prf`, `sel`, `rdlf`, `cics-link`, and `tstp`
* **3 file templates** — Program, Copybook, and Subprogram
* **Free-format formatter** — fixed format is deliberately left untouched to protect column alignment
* **Column-aware Enter handler** for fixed-format editing

### PIC-to-Java/JSON Mapping
* **Generate Java classes and JSON Schema** from COBOL data structures
* Available as an editor intention, from the Tools menu, and as an MCP tool
* Built for modernization work — bridging COBOL data layouts to modern services

### GnuCOBOL Toolchain
* **`cobc` auto-detection** on PATH and common install locations
* **Compile and run configurations** with gutter icons on the run line
* **Syntax-check annotator** shows `cobc` diagnostics inline as you type
* **COBOL Compiler tool window** with clickable console error links back to source

### Debugger
* **Line breakpoints** on GnuCOBOL builds compiled with `cobc -g`, driven over GDB/MI
* **Stepping, frames, and run-to-cursor**
* **C-level variable view** into compiled COBOL data items

### Optional Language Server
* **Bring-your-own server command** — point the plugin at any LSP-compatible server, such as the Eclipse Che4z COBOL Language Support jar with the `pipeEnabled` argument
* **Status bar widget** shows server state
* **Diagnostics and completion merge** with the native parser's results

### AI Assistant & MCP Server
* **AI chat tool window** — Claude Code, Codex, Gemini, Cursor, Windsurf, Antigravity, Aider, or your own Anthropic / OpenAI / Gemini key
* **Embedded MCP server** with 12 tools: programs, outline, data items, usages, call graph, copybook usages, project info, diagnostics, syntax check, compile, PIC mapping, and run
* **Discoverable via `~/.flexible-cobol/mcp`** for one-click setup in your agent CLI
* **Fully optional** — the plugin works completely without it

### New Project Wizard & File Templates
* **COBOL** appears in the New Project wizard with a directory generator and sample project scaffold
* **Copybook path auto-detection** for new and existing projects
* **File templates** available under File > New: Program, Copybook, and Subprogram

---

## Getting Started

### Quick Start
1. Install the plugin from the JetBrains Marketplace
2. Install GnuCOBOL via your system package manager, or use an Arnold Trembley build on Windows
3. Configure the `cobc` path under **Settings > Languages & Frameworks > COBOL** (auto-detected when GnuCOBOL is on PATH)
4. Open a `.cbl` file — syntax highlighting, folding, and structure view activate immediately
5. Click the run gutter icon on a program, or create a run configuration under **Run > Edit Configurations**
6. Set a breakpoint and click **Debug** to step through a `cobc -g` build

### Productivity Tips
* **Type `4div` + Tab** for an instant four-division program skeleton
* **Alt+Enter** on an unresolved COPY statement for a quick fix
* **Ctrl+Q** on a verb or PIC symbol for quick documentation
* **Alt+7** to open the Structure View for the current file
* **Ctrl+Click** on a data item to jump to its declaration, including across copybooks

### Troubleshooting
* **File not recognized?** Check Settings > Editor > File Types > Flexible COBOL — ensure `*.cbl`, `*.cob`, and `*.cobol` are listed
* **COPY not resolving?** Add the copybook directory under Settings > Languages & Frameworks > COBOL > Copybook Paths
* **`cobc` not found?** Verify GnuCOBOL is installed and on your system PATH, or set the path manually
* **Formatter did nothing?** That's expected on fixed-format files — the formatter is a deliberate no-op there
