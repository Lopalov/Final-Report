+++
# Risk Analysis

There are some risks to the project that should be considered.&#x20;

Firstly, because of the requirement that our application has to be browser-only, we have to use the MystMD parser, written in typescript. However, it is still in beta right now{cite}\`githubGitHubJupyterbookmystmd\`, which is a risk for the project, since it might break things in the future. Since the dependencies can be held at a specific version for the application and the syntax of MyST itself is stable, this is a medium-level risk.

Secondly, the application might need to be adapted to Jupyter Book 2.0 in the future. Right now, migrating to Jupyter Book 2.0 is not on the roadmap yet for TeachBooks, but it might be in the future. Luckily, we already use MystMD, the parser that is also used in Jupyter Book 2.0. Jupyter Book 2.0 also has support for adding plugins{cite}\`jupyterbookCreatePlugins\`, and allows injecting content into the rendered document. This is all we really need to be able to integrate our plugin, as we can inject a script element to load the JavaScript code of the editor. Therefore, we consider this to be of low risk to the long-term maintainability of the project.