+++
# Scope of the problem

This project focuses exclusively on simplifying the content editing and version control aspects of TeachBooks. It is not intended to replace or replicate all functionality of the GitHub infrastructure, nor does it include server-side components such as deployment pipelines, PDF generation, or advanced theming.

Key limitations, based on the wishes of our client and the duration of the project, include:

*   No back-end server; all operations must be performed on the client side or via GitHub’s public APIs.
*   Limited support for advanced Markdown directives and Sphinx extensions that cannot be rendered client-side.
*   Users must have a GitHub account to authenticate and make changes.
*   The application must operate entirely within the browser, with no backend component.
*   GitHub integration must use secure, client-compatible authentication methods.
*   The editor must be compatible with the existing TeachBooks repository structure and Markdown format.
*   It is assumed that users have basic computer literacy but no prior knowledge of Git or GitHub workflows.