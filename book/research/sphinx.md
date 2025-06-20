+++
# Sphinx Extension

An important factor for the user-experience of a new product, is its 'Perceived Ease of Use': How much will using this product improve my productivity versus how easy is it to learn how to use this product \cite{fredDavisTAM}. Applying this principle for our target audience of teachers and students, who may have little to no programming experience, meant that we want the distribution and installation to be as easy as possible.&#x20;

## Selection of Distribution Method

To achieve a streamlined user experience, we have researched two alternative ways of distributing / installing the editor.

### Alternative 1: Stand-alone Web Application

When defining our solution, we started with the idea of a stand-alone web-application like Google Docs and Word Online but then for TeachBooks. Almost everyone has already worked with programs like these, so even for non-technical people it would be a streamlined and nice user experience. There is no installation needed, and distribution is as simple as sharing a single link to the website.

However, when researching this option, we came across two core problems. Firstly, hosting a web-application like this would mean that we would need a free or cheap provider to meet our client requirements (must haves) \ref{chap:requirements}. While in a previous section \ref{sec:github} we have defined that GitHub pages is such a platform, our second problem remained.&#x20;

The primary drawback of creating a stand-alone web application is that we would be reinventing the wheel as TeachBooks books are already hosted somewhere and they already have a simple user interface.&#x20;

### Alternative 2: Sphinx Extension

TeachBooks are built using Sphinx-books \cite{SphinxBook}, that means that you can install custom extensions which alter the way users interact with the books \cite{SphinxExtension}. Packaging our editor in such a Sphinx Extension would mean easy access to the TeachBook the user is working on, and its theme. So to leverage the existing infrastructure of TeachBooks and not reinvent the wheel, we chose to package our editor as such a Sphinx Extension.

Furthermore, creating a Sphinx Extension is also really straight forward. Using the Sphinx Python library \cite{SphinxExtensionLib}, a simple setup() function is enough to load in the JavaScript from the editor.

## Implementation of Sphinx Extension

We implemented the distribution of our editor by a Sphinx Extension using a custom JavaScript loader. While the final result is a simple and elegant solution, it introduced two main design challenges which we will explain in the following sections.

### Loading and Inserting the Editor

Our Sphinx Extension adds a navigation button to the header of the book next to the already existing buttons. When the user clicks that button, the actual editor is inserted. This way there is no long delay when opening the book as the editor is only loaded in when the user is actually going to use it.

To simplify the insertion process and avoid the complexity of linking multiple CSS and JavaScript files, we build the entire editor in a single HTML file using a Vite plugin \cite{SingleFilePlugin}. This way we get three components that are easily inserted in an already existing website:

*   An inline \<style> tag with all the editor's CSS.
*   The root \<div> element where the editor will be mounted to.
*   The actual JavaScript of the editor in an inline \<script> tag.

We insert these components in order to make sure the JavaScript will not run before the mounting point is added and has access to the different styling classes.&#x20;

### Theme Clashes and Future Theme Changes

When inserting the first versions of our editor we came across the issue that the drop-down buttons stopped working when embedded in the book. After debugging for some time, we found that the issue was that both the book as our editor were the using Bootstrap Framework \cite{BootstrapJS} for the handling of buttons and drop-down menus, but in different ways. We re-implemented the functions for the editor using vanilla JavaScript and the issues were resolved.

However, one issue could still arise. When inserting the navigation button and editor, we mount both to existing elements within the Sphinx-book theme. When this theme changes in the future, the names of these mounting points might change too and break the application. So in the future, that could be addressed by letting the user change these mounting points in the configuration file of the book.