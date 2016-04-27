# Dependency Hell

Imagine there are three modules: A, B, and C. A requires
B at v1.0, and C also requires B, but at v2.0. We can
visualize this like so:

![2 modules need B](/gitbook/images/deps1.png)

Now, let's create an application that requires both module
A and module C.

![My app needs both A and C](/gitbook/images/deps2.png)

## Dependency Hell

A package manager would need to provide a version of
module B. In all other runtimes prior to Node.js, this is
what a package manager would try to do. This is dependency hell:

![Dependency Hell](/gitbook/images/deps3.png)
