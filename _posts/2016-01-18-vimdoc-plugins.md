---
layout: post
title: vimdoc project
---

I've decided to make everything right and reduce the mess under my [vim
configuration](https://github.com/Valiev/config/blob/master/.vimrc). First of
ideas came into my head was to start with documentation.

Easy say than done, I always hated to compose documentation lines. But this time
I've managed to combine tools I like: markdown inside vim configuration.

Let me give you example here how it looks like:

```
" ### Filetypes
"
" - [vim-nagios](https://github.com/tejr/vim-nagios) plugin provides syntax
"   highlight for [Nagios](https://www.nagios.org/) monitoring configuration
"   files. `Plug 'tejr/vim-nagios', { 'for': 'nagios' }` line is used to provide
"   this plugin to be enabled only for `nagios` files. Could be enabled by
"   setting filetype explicitly with `:set filetype=nagios`.
  Plug 'tejr/vim-nagios', { 'for': 'nagios' }

" - [wting/rust.vim](https://github.com/wting/rust.vim) plugin brings `rust`
"   support to vim.
  Plug 'wting/rust.vim', { 'for': 'rust' }
```

Here's the script which takes documentation out of `.vimrc` files:

```
#!/usr/bin/env sh

FILENAME=$1
cat $FILENAME | grep '^\s*"' | sed -e 's/^[[:space:]]*" //' | sed -e 's/^"//'
```

The whole `plugin` section is finished and available
[here](https://github.com/Valiev/config/blob/master/docs/vimrc.md#plugins)
