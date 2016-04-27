# How npm2 Works

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

Instead of attempting to resolve module B to a single version,
npm puts both versions of module B into the tree, each version
nested under the module that requires it.

![what npm does](/gitbook/images/deps4.png)


In the terminal, this looks like this:

![tree](/gitbook/images/tree.png)

You can list the dependencies and still see their relationships using
`npm ls`:

![npmls](/gitbook/images/npmls.png)

If you want to just see your primary dependencies, you can use:

```
npm ls --depth=0
```

![npmlsdepth0](/gitbook/images/npmlsdepth0.png)

## npm and the Node.js Module Loader

However, npm doing this is *not enough*. Despite the fact that
their nested locations allow for the coexistence of two versions
of the same module, most module loaders are unable to load two
different versions of the same module into memory. Luckily, the
Node.js module loader is written for exactly this situation, and
can easily load both versions of the module in a way that they do
not conflict with each other.

How is it that npm and the node module loader are so wonderfully 
symbiotic? They were both written in large part by the same person,
npm, Inc. CEO, Isaac Z. Schlueter. Like 2 sides of the same piece of 
paper, npm and the Node.js module loader are what make Node.js
a uniquely well-suited runtime for dependency management.
