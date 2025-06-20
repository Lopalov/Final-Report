+++
# Feasability Study

There are a couple of questions we must answer in order to consider the project feasible. Otherwise, the scope of the project should be reduced, or one or multiple of the constraints should be lifted.

**Can we implement a WYSIWYG (What You See Is What You Get) editor in the browser?**

There are frameworks available to parse Markdown and to create a browser-based editor. An example of this is ProseMirror \cite{prosemirrorProseMirror}, an extensible JavaScript framework that allows developers to build WYSIWYG editors relatively easily. State management and user typing interactions are handled by ProseMirror. It is also possible to convert from Markdown to ProseMirror and vice versa. An example is already shown in the ProseMirror documentation \cite{prosemirrorProseMirrorMarkdown}. This only handles Commonmark, a subset of MyST, which is the Markdown dialect used by TeachBooks. Editing and rendering extended content from the browser, like embedded equations using LaTeX, is more challenging. However, these are not hard requirements for the client. An acceptable compromise is to just be able to the basic elements, like discussed in \ref{chap:requirements}

**Can we integrate such an editor into the Git/GitHub workflow in the browser, without resorting to a server-side solution (per the request of the client)?**

In order for the application to significantly enhance the workflow, users should not have to manually edit the files in GitHub for simple tasks. Therefore, the solution needs to integrate with GitHub to edit documents. This can be done using the GitHub API \cite{githubRESTPullRequests}, where the user authorizes the application to act on their behalf \cite{githubGeneratingUser}. Editing files is also supported \cite{githubRepositoryContents}.

**Can we complete the project in time?**

A WYSIWYG editor is a complex piece of software. This, combined with GitHub integration makes the project quite an undertaking, if we were required to implement it from scratch. Luckily there exists software that can help us to build such an editor without having to solve some of these hard technical challenges, as previously mentioned. Additionally, the GitHub API interaction and the WYSIWYG editor can be implemented in parallel, since they are mostly disjoint. Good software design principles, e.g. separation of concerns, can help us here. This requires that we consider the scope of the project carefully and plan the software architecture beforehand. We should also only use existing technologies when they are a good fit, and ensure they are reliable.

**How do we ensure we build an inclusive and accessible user experience?**

As Godwin-Jones \cite{godwinjones2001accessibility} notes, accessibility is important to make sure that everyone can contribute, no matter their abilities. This includes colorblind people, or screen reader users. Therefore, we need to consider whether the project is accessible to anyone who wants to contribute, so TeachBooks’ mission can reach as many people as possible. Technical considerations include accounting for contrast, being keyboard-navigable and screen reader friendly \cite\[Chapter~1~and~2]{yesilada2019web}.

**How do we ensure the interface is intuitive?**

An interface that is not intuitive can hinder adoption. As developers, we may consider certain actions to be obvious, because we designed them ourselves. To mitigate this, we can keep the client in the loop, taking notes of any critiques or ideas they might have. If time allows, we can also watch along with a user, as they are asked to perform certain tasks. This way, we can get a far more accurate view of how a novice user will interact with our solution.