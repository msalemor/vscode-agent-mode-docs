# VSCode Agent Mode For Technical Document Generation

Demonstrates a technique to generate technical documents using Visual Studio Code Agent mode.

## Summary of the technique

This technique leverages VSCode's Agent mode capabilities combined with GitHub Copilot to automatically generate comprehensive technical documentation. By defining structured instructions in a `.vscode/copilot-instructions.md` file, developers can establish consistent documentation standards including security requirements (TLS/SSL, managed identities, EntraID authentication) and predefined document sections. 

The workflow involves:
1. Creating a standardized instruction template that specifies document structure and security patterns
2. Preparing a requirements document containing project-specific details
3. Using Agent mode to reference the requirements file as context
4. Executing a simple prompt to trigger automated document generation based on the predefined rules and requirements

This approach ensures consistent, security-compliant technical documentation across projects while significantly reducing manual documentation effort.


## Copilot Intructions

The [.vscode/copilot-instructions.md](.github/copilot-instructions.md) file serves as a configuration template that defines:

- **Documentation standards**: Establishes consistent structure across all generated technical documents
- **Security patterns**: Enforces security requirements like TLS/SSL, managed identities, and EntraID authentication
- **Document sections**: Predefines which sections to include (Introduction, Architecture, Security, etc.)
- **Conditional rules**: Specifies logic for different document types (e.g., excluding certain sections for low-code solutions)
- **Azure best practices**: Ensures generated content follows Azure development guidelines

This file acts as a blueprint that GitHub Copilot references when generating technical documentation, ensuring consistency and compliance across all project documents.


## Requirements document

The [document-generation-requirements.md](./document-generation-requirements.md) file contains the document generation requirements that specify which technical documents to create. It serves as a manifest that lists each document to be generated along with metadata that guides the generation process. 

The requirements file includes:
- **Document ID**: Unique identifier for tracking
- **Type**: Classification (e.g., "Low code", "High code") that triggers specific generation rules
- **Use Case**: Brief description of the solution being documented
- **Document Name**: Output filename for the generated documentation
- **Additional Instructions**: Any special requirements for that specific document

The document type is particularly important as it works in conjunction with the copilot instructions to determine which sections to include or exclude. For example, documents marked as "Low code" or "No code" will automatically exclude technical architecture sections while including detailed configuration instructions, as specified in the copilot instructions rules.

```
# Project requirement document

The following document outlines the detail instructions.

## Documents

| ID | Type | Use Case | Document Name | Additional Instructions |
| -- | ---- | -------- | ------------- | ----------------------- |
| DOC01 | Low code | Chat with your data using Copilot Studio | chat-with-your-data-copilot-studio.md | |

```

## The Agent Mode prompt and file in context


File in context: `document-generation-requirements.md`

Prompt:
```
Generate the technical documents according to the instructions in this document.
```

## Sample generated documents

- [chat-with-your-data-copilot-studio.md](./docs/chat-with-your-data-copilot-studio.md)
- [chat-with-your-data-foundry-agent.md](./docs/chat-with-your-data-foundry-agent.md)
- [chat-with-a-document-m365.md](./docs/chat-with-a-document-m365.md)
- [chat-with-data-m365.md](./docs/chat-with-data-m365.md)