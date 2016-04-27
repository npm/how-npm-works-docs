# The Node Module Loader

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
