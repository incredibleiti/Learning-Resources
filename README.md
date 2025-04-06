================== Content from recent learning =====================

# CodeQL 101 – Find Vulnerabilities in Your Codebase

Welcome to **CodeQL** — a powerful static analysis tool that lets you query your codebase like a database. This README will help you get started with CodeQL using the CLI and GitHub Actions.

---

## What is CodeQL?

CodeQL allows you to:

- Query code as data
- Detect vulnerabilities (like SQL injection, buffer overflows)
- Enforce secure coding practices
- Understand and explore code structure

It works by converting source code into a database, which you can analyze with a custom query language called QL.

---

## Installation

Download the CodeQL CLI from:

👉 https://github.com/github/codeql-cli-binaries/releases

Unzip and add the binary to your PATH.

To verify:

```bash
codeql --version
```

---

## Creating a CodeQL Database

To analyze a C++ project, run:

```bash
codeql database create my-db --language=cpp --command="make"
```

Replace `make` with your project’s build command.

This command:
- Runs your build
- Monitors the process
- Creates a database `my-db` that CodeQL can analyze

---

## Writing and Running a Query

Create a file `find-strcpy.ql` with this content:

```ql
import cpp

from Function f
where f.getName() = "strcpy"
select f, "Avoid using unsafe function strcpy"
```

Run the query:

```bash
codeql query run find-strcpy.ql --database=my-db
```

This will return all places in the code where `strcpy` is used.

---

## GitHub Actions Setup

If your repo is hosted on GitHub, create a file at `.github/workflows/codeql.yml`:

```yaml
name: CodeQL Analysis

on: [push, pull_request]

jobs:
  analyze:
    name: Analyze code
    runs-on: ubuntu-latest
    permissions:
      security-events: write
    steps:
      - uses: actions/checkout@v3
      - uses: github/codeql-action/init@v2
        with:
          languages: cpp
      - uses: github/codeql-action/analyze@v2
```

This will automatically run CodeQL on every push and PR.

---

## Useful Tools

- [CodeQL VS Code Extension](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-codeql)
- [Standard Query Library](https://github.com/github/codeql)
- [CodeQL Docs](https://codeql.github.com/docs/)

---

## Final Notes

CodeQL is an excellent tool to improve your code's safety and quality. Start small with simple queries, and gradually build your own security rules.

Happy querying! 🧪
