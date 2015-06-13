# vim-syntax-expand

This contains functions to expand a character to a string as long as your cursor isn't currently inside a string or comment syntax element. This essentially allows you to have single character abbreviations that only apply to actual syntax. Please check the doc directory for more information.

Here's how I use it with conceal in JavaScript to create a cute language on top of JavaScript that doesn't affect anyone else.

[![asciicast](https://asciinema.org/a/ag49t530108fu0qp2cuefondl.png)](https://asciinema.org/a/ag49t530108fu0qp2cuefondl)

## Installation

Use your favourite plugin manager, you know the drill. I like [vim-plug][], so here's how you'd install it with that.

```vim
Plug 'Wolfy87/vim-syntax-expand'
```

## Usage

Here's my example configuration for JavaScript. The conceal functionality is provided by [vim-javascript][] (which is fantastic).

```vim
" Map the conceal characters to their expanded forms.
inoremap <silent> @ <C-r>=syntax_expand#expand("@", "this")<CR>
inoremap <silent> # <C-r>=syntax_expand#expand("#", "prototype")<CR>
inoremap <silent> < <C-r>=syntax_expand#expand_head("<", "return")<CR>

" Keeps everything concealed at all times. Even when my cursor is on the word.
set conceallevel=1
set concealcursor=nvic

" JavaScript thanks to pangloss/vim-javascript
let g:javascript_conceal_function = "λ"
let g:javascript_conceal_this = "@"
let g:javascript_conceal_return = "<"
let g:javascript_conceal_prototype = "#"
```

So now when I type `@` it is actually expanded to `this` but I still see it as `@`. Cool, right? This will work for other languages too, you just need to set up your conceal rules (there's usually a plugin) and some expansion bindings.

## Author

[Oliver Caldwell][] / [@OliverCaldwell][]

## Unlicenced

Find the full [unlicense][] in the `UNLICENSE` file, but here's a snippet.

>This is free and unencumbered software released into the public domain.
>
>Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or as a compiled binary, for any purpose, commercial or non-commercial, and by any means.

Do what you want. Learn as much as you can. Unlicense more software.

[unlicense]: http://unlicense.org/
[vim-plug]: https://github.com/junegunn/vim-plug
[vim-javascript]: https://github.com/pangloss/vim-javascript
[Oliver Caldwell]: http://oli.me.uk/
[@OliverCaldwell]: https://twitter.com/OliverCaldwell
