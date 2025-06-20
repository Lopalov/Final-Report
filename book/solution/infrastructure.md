+++
# Component Infrastructure

We adopted a component-based architecture to promote code organization and reusability. All UI elements are defined in their own file located in the components directory. Take the toolbar for example: It is built by combining multiple small components such as formatting buttons, dropdown menus, and separators. These are defined in toolbar\\\_components.tsx, while the overall structure and layout logic of the toolbar is handled in toolbar.tsx. This structure ensures that each element has a well-defined responsibility and can be reused or modified independently.&#x20;

This separation of concerns is also applied to functionality: command functions that modify the editor state (toolbar\\\_commands.ts) are kept separate from utility functions that query it (toolbar\\\_utils.ts). The foundation for this is a custom schema (index.ts) that specifies the document's structure and supported nodes.&#x20;

Editor functionality such as toggling formatting styles (e.g., bold, italic), changing fonts, or inserting lists is implemented through a set of command functions located in toolbar\\\_commands.ts. These functions encapsulate how the editor state is manipulated through ProseMirror’s API. Related utility functions used to check formatting states like active marks or text alignment are stored separately in toolbar\\\_utils.ts to avoid mixing concerns.