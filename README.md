# vim-lsp

Async [Language Server Protocol](https://github.com/Microsoft/language-server-protocol) plugin for vim8 and neovim.
Internally vim-lsp uses [async.vim](https://github.com/prabirshrestha/async.vim).

# Installing

```viml
Plug 'prabirshrestha/async.vim'
Plug 'prabirshrestha/vim-lsp'
```

_Note: [async.vim](https://github.com/prabirshrestha/async.vim) is required to normalize jobs between vim8 and neovim._

## Registering servers

```viml
if executable('pyls')
    " pip install python-language-server
    au User lsp_setup call lsp#register_server({
        \ 'name': 'pyls',
        \ 'cmd': {server_info->['pyls']},
        \ 'whitelist': ['python'],
        \ })
endif
```

**For other languages please refer to the [wiki](https://github.com/prabirshrestha/vim-lsp/wiki/Servers).**

## auto-complete

`vim-lsp` by default doesn't support any auto complete plugins. You need to install additional plugins to enable auto complete.

### asyncomplete.vim

[asyncomplete.vim](https://github.com/prabirshrestha/asyncomplete.vim) is a async auto complete plugin for vim8 and neovim written in pure vim script without any python dependencies.

```viml
Plug 'prabirshrestha/asyncomplete.vim'
Plug 'prabirshrestha/asyncomplete-lsp.vim'
```

## Supported commands

**Note:**
* Some servers may not only support all commands.
* While it is possible to register multiple servers for the same filetype, some commands will pick only pick the first server that supports it. For example, it doesn't make sense for rename and format commands to be sent to multiple servers.

| Command | Description|
|--|--|
|`:LspDefinition`| Go to definition |
|`:LspDocumentFormat`| Format entire document |
|`:LspDocumentRangeFormat`| Format document selection |
|`:LspDocumentSymbol`| Show document symbols |
|`:LspHover`| Show hover information |
|`:LspReferences`| Find references |
|`:LspRename`| Rename symbol |
|`:LspWorkspaceSymbol`| Search/Show workspace symbol |
