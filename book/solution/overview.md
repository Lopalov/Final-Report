+++
# Solution and Implementation

In this chapter, we define the desging and architecture of our solution based on the outcomes of the [Research](../research/overview.md). We begin with [Product Design](./design.md) by describing the overall design of our end product and the major design choices we made during the project. These include the WYSIWYG editor for user experience, a familiar toolbar modeled after common word processors, and a visual style consistent with TeachBooks so it feels like one coherent suite.

Following this, [System Architecture](./architecture.md) details the three parts of our architecture. The end product is composed of a client-side web editor, that requires no installation so it easy to use, a Sphinx extension that loads the editor into a TeachBook, and the actual book hosted on GitHub Pages. This architecture was chosen so we could use the best technology for each component. Vite for modern web development of the editor and Python for the robust and easy-to-use Sphinx library. GitHub Pages because the client required a free, simple hosting solution for the open-source project.

Finally, [Component Infrastructure](./infrastructure.md) presents how we used components to achieve a modular and maintainable code base. Every functionality is defined in its own file the proper documentation. This structure ensures that the codebase is largely self-explanatory, so other developers can understand the purpose of a component, simply by examining its filename and its imports, even without prior project experience.
