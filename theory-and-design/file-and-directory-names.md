# File and Directory Names

- So, why is it the `node_modules` folder, but `package.json` file?
- Why not `node_packages` or `module.json`?

The `package.json` file defines the package.  (See 
["What is a `package`?"](#what-is-a-packae), above.)

The `node_modules` folder is the place Node.js looks for modules.
(See ["What is a `module`?"](#what-is-a-module), above.)

For example, if you create a file at `node_modules/foo.js` and then
had a program that did `var f = require('foo.js')`, it would load
the module.  However, `foo.js` is not a "package" in this case,
because it does not have a package.json.

Alternatively, if you create a package which does not have an
`index.js` or a `"main"` field in the `package.json` file, then it is
not a module.  Even if it's installed in `node_modules`, it can't be
an argument to `require()`.
