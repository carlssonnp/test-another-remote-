What are the three requirements when naming an R package?
*  name can only consist of letters, numbers and periods; it must start with a letter; and it cannot end with a period.

Why is it a bad idea to name your package with a "."?
* it can become confused with S3 methods or file exensions

What is the difference between devtools::install_github and install.packages?
* install.packages downloads and installs binary packages built by CRAN while install_github downloads source package from github, builds it, and installs it.

What is the difference between Suggests and Imports?
* Imports are dependency packages that the package I'm building needs versus Suggests are packages that those are not dependencies but could be of good use.

What is the importance of dontrun?
Why do packages have versions?
What does moving from v1.0.1 to v2.0.0 mean? What does moving from v1.0.1 to v1.0.2 mean?
*Backward incompatible changes, backward compatible bug fixes.

What does v1.0.1.9000 mean?