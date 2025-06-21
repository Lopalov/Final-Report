+++
# Conclusion

The primary goal of this project was to make creating and editing TeachBooks more accessible for people with little to no programming experience. We successfully addressed this challenge by designing and implementing a completely browser-based, client-side editor, packaged as an easy-to-install Sphinx Extension. The final product provides an intuitive interface that significantly lowers the technical barrier for content creation.

During the development we came across some significant technical difficulties. Despite these challenges we managed to develop a working end product that satisfies our client's needs. However, there still are a few well-defined limitations in the current implementation.

1.  **User Experience in Authentication** - Because of GitHub's client-side security policies, the user has to create Personal Access Tokens for authentication, which are secure but less user-friendly than the automated approach and may be difficult for the target audience.
2.  **Technical Robustness** - The method for injecting the editor is tightly coupled to the specific HTML structure of the current Sphinx theme. This creates a dependency that could break if the theme is updated in the future.
3.  **Functional Scope** - The editor's functionality is currently limited to the basic building blocks of a TeachBook. It does not yet incorporate the full range of features available, requiring users to fall back on manual editing for more advanced content.

Based on these outcomes, we provide the following concrete recommendations for the project's future development, each designed to address a specific limitation identified above:

1.  **Use GitHub authentication instead of personal access tokens.** Implement a simple, secure back-end server to act as a proxy for GitHub's OAuth service. This would enable a seamless, one-click authentication flow for the user, removing the need for manually generated personal access tokens. Such a back-end can be implemented cost-effectively and might even be free of charge for open source projects like these.
2.  **Configurations for editor mounting points.** In the future we would recommend letting the user define the editors mounting points in the configuration of their book. Now these points are hard-coded in the custom JavaScript loader. So, when the Sphinx theme might change in the future, we run the risk of breaking the inserting of the editor.
3.  **Expand the capabilities of the editor.** Systematically implement the remaining TeachBook features within the WYSIWYG interface. Right now only the basic building blocks are implemented. The next logical step is to expand these capabilities to the point where users can access the whole feature set of TeachBooks in the editor.