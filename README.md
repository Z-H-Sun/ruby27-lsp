# Ruby27 LSP

This is a fork of the [Ruby LSP](https://github.com/Shopify/ruby-lsp) project.

As the original authors put, the original Ruby LSP won't support any Ruby versions that have reached its EOL.

However, this fork provides you a chance to **run it with a slightly lower Ruby version, namely 2.7.x**.

## Forked Version

This fork works on the current latest version of Ruby LSP, `v0.26.7`, which corresponds to a VS Code extension version of `0.10.0`.

Should any new versions be published in the future, I may or may not work on them. It can be as simple as a `git merge` which you can also try, but that can't be guaranteed.

## Getting Started

On the Ruby side:
- Download the source code
- `cd` to the folder
- run `gem build ruby-lsp.gemspec` to generate the local gem file first, and then
- run `gem install ruby-lsp -v 0.26.7` to install from it.

> [!note]
> If the Prism gem fails to install on Windows, it's likely due to some imcompatibility issues between the Ruby header files and the latest GCC 15. You can either temporarily downgrade GCC to 14.x, or run `gem install prism -- --with-cflags=-std=c99` as a workaround (See my comment in [this issue](https://github.com/ruby/prism/issues/3627#issuecomment-3958323897)).

On the VS Code (or Antigravity, whatever) side:
- Install the Ruby LSP extension
  - Note: the version that pairs with the current gem version is `v0.10.0`; newer versions may or may not work
- You will need to alter the extension `js` file. The easiest way is to go to `%UserProfile%` (or equivalent), and then open `/.vscode/extensions/shopify.ruby-lsp-0.10.0/out/extension.js`, and then
  - make edits to the file: find and delete the code ``if(e<3)throw new Error(`The Ruby LSP requires Ruby 3.0 or newer to run. This project is using ${this.rubyVersion}.         [See alternatives](https://github.com/Shopify/ruby-lsp/blob/main/vscode/README.md#ruby-version-requirement)`);``
