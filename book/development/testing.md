# Testing

In this section we will discuss the variety of testing methods we used in this project. First, we will take a look at the frameworks we considered and ultimately chose to employ, as well as the methodology we decided on for testing UI elements in Automatic and Manual Testing. After that, we present the user test we held in the last weeks of the project.

## Automatic and Manual Testing

For testing, we looked at testing frameworks for TypeScript

*   [Jest](https://jestjs.io/ "Jest") - The most mature
*   [Mocha](https://mochajs.org "https://mochajs.org") - API inspired by Jest, more minimal
*   [Jasmine](https://jasmine.github.io/ "Jasmine") - API also inspired by Jest, support for browser testing
*   [Vitest](https://vitest.dev/ "Vitest") - API heavily inspired by Jest, support for browser testing and Typescript. Integrates with the Vite bundler

Out of these, only Vitest supports Typescript natively, because it integrates with Vite, the build tool we are using for our browser code. Vitest allows us to mock a browser environment, or to run tests in the browser.

We primarily use unit tests in our automated testing. We additionally use snapshot tests for the parser, myst-to-prosemirror and prosemirror-to-myst conversion. We have set up a command that runs vitest in 'watch mode'; it automatically reruns tests if a source file is written, to aid rapid development. We mostly rely on unit tests, because they are easy to write and quick to fix. They are stable and not flaky. This ensures we can maintain good progress without having to constantly fix flaky tests.

UI and integration tests are done manually, as UI testing is harder to do in an automated fashion. This can also be done by vitest, but requires integration tests using the browser, which are slow to run and flaky, meaning that they fail sporadically if not set up correctly, which is non-trivial. When we encounter a bug in the UI, we write a unit test to make sure that it doesn't happen again.

The automatic tests run in GitLab CI, as well as code linting and formatting. These are integrated with GitLab so failing tests show up in the GitLab UI. Test coverage is also collected and displayed line-by-line in merge requests, and a percentage total is displayed as a badge in the README of the repository.

## User Test

Early on in the project we decided that we should conduct a user test in order to better align with the primary stakeholders mentioned in the beginning of [Problem Analysis](../problem_analysis/overview.md "Problem Analysis"). The time frame for the user test was originally scheduled to be in the beginning of week 8, as by that point all of the must have features (see [Appendix A](../appendices/a.md "Appendix A")) were supposed to be implemented, however due to technical difficulties with the parser it had to be postponed until the end of week 8.

The user test itself consisted of sending the functionally complete product, already integrated in a GitHub repository, to the a select group, picked by the client. Along with the product, we sent out a questionnaire to filter out the responses we deemed less useful. The full response list can be found in [Appendix E](../appendices/e.md "Appendix E").

The responses were then used to refine the features of our product and fix issues and bugs we had missed prior to sending out the user test.