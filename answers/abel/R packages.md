
1. What are the three requirements when naming an R package?

the name can only consist of letters, numbers, and periods.

it must start with a letter.

it cannot end with a period.

2. Why is it a bad idea to name your package with a "."?

To avoind confusion with extensions, S3 methods, etc.

3. What is the difference between devtools::install_github and install.packages?

install.packages finds the package in CRAN, and devtools::install_github finds the package in github.


4. What is the difference between devtools::build and devtools::install?

devtools::build creates a bundle from source and then applies R CMD install to i. devtools::install gives the source directly to R CMD install.

5. What is the difference between devtools::load_all and library?

library() loads into memory packages that are already installed. devtools::load_all() loads packages from source directly into memory

6. What is the difference between Suggests and Imports?
If a user does not have a package listed in Imports, installing your package will cause the user to also install the listed package.

If a user does not have a package listed in Suggests, this will not happen. Hopefully you've written versions of functions that can be run without this package.




7. What is the importance of dontrun?

When writing examples of code that errors in dumentation, surrounding these examples with \dontrun{} ensures that the contained code doesn't run.




8. Why do packages have versions?

They are a quick way to communicate about the size of the changes in a package over time.


9. What does moving from v1.0.1 to v2.0.0 mean? What does moving from v1.0.1 to v1.0.2 mean?

v1.0.1 to v2.0.0 means a major release, likely not backwards compatible.

v1.0.1 to v1.0.0 means a patch, i.e. bug fixing that does not add significant new features.


10. What does v1.0.1.9000 mean?

a patch has been applied to v1.0.0, and the package is still in development.
