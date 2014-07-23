FastFold
========

Automatic folds (that is, folds generated by a fold method different
from `manual`), bog down VIM considerably in insert mode and are often
reevaluated prematurely (for example, when inserting an opening fold marker
whose closing counterpart has yet to be added to complete the fold.)

See http://vim.wikia.com/wiki/Keep_folds_closed_while_inserting_text
for a discussion.

With this plug-in, the folds in the currently edited buffer are updated by an
automatic fold method only when saving the buffer (or typing `zuz` in normal
mode), and are kept as is otherwise (by keeping the fold method set to `manual`).

For example, by adding
```
set foldmethod=syntax

let g:tex_fold_enabled=1
let g:vimsyn_folding='af'
let g:xml_syntax_folding = 1
```
to your .vimrc, the folds in your TeX, Vim or XML file are updated by the
`syntax` fold method when saving (or typing `zuz` in normal mode) and are kept as is
otherwise.

==

The normal mode mapping `zuz` to force an update of folds can be disabled by
`let g:fastfold_no_mappings = 1` or remapped to your liking by `<Plug>FastFoldUpdate`.

==

This plug-in will overwrite your manual folds when saving the currently edited
buffer, unless you either

- explicitly tell this plug-in to refrain from it via `g:fastfold_skipfiles`, or
- the local and global `fold method` is set to `manual` since entering the buffer
window and in the meanwhile you did not switch either of these and saved the buffer
(or typed `zuz` in normal mode).

===

`FastFold.vim` integrates with version 1.2 and above of the `restore_view.vim`
plug-in that stores and restores the last folds by the `:mkview` and `:loadview`
if `restore_view.vim` is loaded *AFTER* `FastFold.vim`. (To ensure the correct
autocmd execution order.)

You can find a recent fork of it at

http://www.github.com/Konfekt/restore_view

