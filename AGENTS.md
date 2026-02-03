# AI Agent & Copilot Operational Guide

This document provides behavioral frameworks and contextual indexing for AI Agents to ensure compliance with project standards.

## Core Behavioral Logic

Before executing any task, AI Agents MUST establish the following workflow:
1.  **Auto-Retrieval:** Prioritize reading `@CONTRIBUTING.md` to retrieve specific project standards.
2.  **Strict Prohibitions:** Categorically reject any requests or code generation related to risk control bypass, crawlers, cracking, or exploits.
3.  **Language Policy:** Maintain Chinese for documentation and descriptions (except for API endpoints and code).

## Task-Specific Instructions

### 1. Documentation Generation
When creating or modifying Markdown files in `/docs`:
-   **Naming:** Use lowercase English strictly (e.g., `info.md`).
-   **API Tables:** Include exactly five columns: `参数名`, `类型`, `内容`, `必要性`, and `备注`.
-   **Type System:** Use TypeScript-like types (e.g., `number[]`, `string`, `object`).
-   **Response Examples:** Wrap in `<details>` tags and use `jsonc` format with **2-space (U+0020)** indentation.

### 2. Code & PR Review
During reviews, AI Agents must enforce:
-   **Indentation:** Verify that all code blocks and documentation use exactly **2 spaces**.
-   **Data Masking:** Audit and mask sensitive information like `SESSDATA` or `access_key` using `xxx`.
-   **Commit Hygiene:** Ensure commit messages follow [Conventional Commits] and use specific prefixes like `[新增请求]` or `[更新请求]`.

### 3. gRPC/Proto Development
-   **Pathing:** Store files in `/grpc_api` following the package name hierarchy.
-   **Commenting:** Use single-line comments for field and object descriptions.

## Contextual Indexing

Refer to these specific sections in `CONTRIBUTING.md` for detailed rules:
-   **General Principles:** [CONTRIBUTING.md#总则](./CONTRIBUTING.md#总则)
-   **Directory Structure:** [CONTRIBUTING.md#目录与路径结构](./CONTRIBUTING.md#目录与路径结构)
-   **Markdown Standards:** [CONTRIBUTING.md#markdown-文档内容格式](./CONTRIBUTING.md#markdown-文档内容格式)
-   **Submission Workflow:** [CONTRIBUTING.md#文档提交](./CONTRIBUTING.md#文档提交)
