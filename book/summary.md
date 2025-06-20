+++
# Summary

Interactive textbooks are used in many courses at TU Delft and across various other institutions to improve comprehension of, and ease engagement with, study materials. These textbooks can come in many forms and be created using various tools. Our client, the TeachBooks team, has an existing workflow for making interactive textbooks; their books are created using MySTMD - a form of Markdown syntax.

The mission statement and vision of the TeachBooks team emphasises the importance of making the process of creating and maintaining these books as easy as possible, to allow educators to focus on the creation of educational content instead of worrying about technical details.

We have successfully delivered a browser-based visual editor that allows educators to edit TeachBooks in their rendered form. This dramatically lowers the barrier to entry for non-technical users.

The requirements of the editor were established by our client and our own research. We outlined the design of our solution quickly after that and started researching the options we had for the implementation. We also sent out a survey via the TeachBooks newsletter, with questions aimed at further refining our requirements and understanding the needs of our stakeholders.

We developed the editor as an extension that can be added to any new or existing TeachBook. The editor itself is written in Typescript, using ProseMirror to display rendered content, and integrated with GitHub for saving and loading actions. The extension is a Sphinx extension written in python, which loads the editor into the TeachBook with the press of a button.

Throughout the entire project, we held weekly meetings with our client and TA, and multiple internal meetings to coordinate, help, and plan various tasks.

In this report we will present our work on designing and implementing the aforementioned editor. We will provide a full overview of the project, including the problem analysis, functional requirements, technology selection, editor design and implementation, GitHub integration, and ethical considerations. The report concludes with recommendations for future development.