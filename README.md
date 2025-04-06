# Learning-Resources
This is the directory for Learning Resources. Feel free to forkence
================== Keep on extending with informations and blog post from  https://codingdummies.wordpress.com/ ========================

# CodeQL 101: Write Code to Find Vulnerabilities in Code

Welcome to **CodeQL** — a powerful static analysis tool that lets you write queries to explore your codebase like a database. Whether you're looking to spot vulnerabilities, enforce coding standards, or just understand your code better, CodeQL is your go-to toolkit.

---

## What Is CodeQL?

**CodeQL** allows you to query your code like data. It converts your code into a relational database and lets you write custom queries using a special language called QL.

Use cases include:

- Detecting security vulnerabilities (e.g., SQL injection, XSS)
- Enforcing architecture rules
- Detecting code smells or legacy patterns

---

## Getting Started

### 1. Install the CodeQL CLI

Download it from the [official release page](https://github.com/github/codeql-cli-binaries/releases), or use it through GitHub Actions if you're working in a public repo.

### 2. Create a CodeQL Database

For example, to analyze a C++ project:

```bash
codeql database create my-db --language=cpp --command="make"

