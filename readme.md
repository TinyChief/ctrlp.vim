#**This project is unmaintained** 
**You should use [this fork](https://github.com/ctrlpvim/ctrlp.vim) instead.**

# ctrlp.vim
Full path fuzzy __file__, __buffer__, __mru__, __tag__, __...__ finder for Vim.

* Written in pure Vimscript for MacVim, gVim and Vim 7.0+.
* Full support for Vim's regexp as search patterns.
* Built-in Most Recently Used (MRU) files monitoring.
* Built-in project's root finder.
* Open multiple files at once.
* Create new files and directories.
* [Extensible][2].

![ctrlp][1]

## Basic Usage
* Run `:CtrlP` or `:CtrlP [starting-directory]` to invoke CtrlP in find file mode.
* Run `:CtrlPBuffer` or `:CtrlPMRU` to invoke CtrlP in find buffer or find MRU file mode.
* Run `:CtrlPMixed` to search in Files, Buffers and MRU files at the same time.

Check `:help ctrlp-commands` and `:help ctrlp-extensions` for other commands.

##### Once CtrlP is open:
* Press `<F5>` to purge the cache for the current directory to get new files, remove deleted files and apply new ignore options.
* Press `<c-f>` and `<c-b>` to cycle between modes.
* Press `<c-d>` to switch to filename only search instead of full path.
* Press `<c-r>` to switch to regexp mode.
* Use `<c-j>`, `<c-k>` or the arrow keys to navigate the result list.
* Use `<c-t>` or `<c-v>`, `<c-x>` to open the selected entry in a new tab or in a new split.
* Use `<c-n>`, `<c-p>` to select the next/previous string in the prompt's history.
* Use `<c-y>` to create a new file and its parent directories.
* Use `<c-z>` to mark/unmark multiple files and `<c-o>` to open them.

Run `:help ctrlp-mappings` or submit `?` in CtrlP for more mapping help.

* Submit two or more dots `..` to go up the directory tree by one or multiple levels.
* End the input string with a colon `:` followed by a command to execute it on the opening file(s):  
Use `:25` to jump to line 25.  
Use `:diffthis` when opening multiple files to run `:diffthis` on the first 4 files.

## Basic Options
* Change the default mapping and the default command to invoke CtrlP:

    ```vim
    let g:ctrlp_map = '<c-p>'
    let g:ctrlp_cmd = 'CtrlP'
    ```

* When invoked, unless a starting directory is specified, CtrlP will set its local working directory according to this variable:

    ```vim
    let g:ctrlp_working_path_mode = 'ra'
    ```

    `'c'` - the directory of the current file.  
    `'r'` - the nearest ancestor that contains one of these directories or files: `.git` `.hg` `.svn` `.bzr` `_darcs`  
    `'a'` - like c, but only if the current working directory outside of CtrlP is not a direct ancestor of the directory of the current file.  
    `0` or `''` (empty string) - disable this feature.

    Define additional root markers with the `g:ctrlp_root_markers` option.

* Exclude files and directories using Vim's `wildignore` and CtrlP's own `g:ctrlp_custom_ignore`:

    ```vim
    set wildignore+=*/tmp/*,*.so,*.swp,*.zip     " MacOSX/Linux
    set wildignore+=*\\tmp\\*,*.swp,*.zip,*.exe  " Windows

    let g:ctrlp_custom_ignore = '\v[\/](node_modules|target|dist)|(\.(swp|ico|git|svn))$'
    let g:ctrlp_custom_ignore = {
      \ 'dir':  '\v[\/]\.(git|hg|svn)$',
      \ 'file': '\v\.(exe|so|dll)$',
      \ 'link': 'some_bad_symbolic_links',
      \ }
    ```

* Use a custom file listing command:

    ```vim
    let g:ctrlp_user_command = 'find %s -type f'        " MacOSX/Linux
    let g:ctrlp_user_command = 'dir %s /-n /b /s /a-d'  " Windows
    ```

Check `:help ctrlp-options` for other options.

## Installation
Use your favorite method or check the homepage for a [quick installation guide][3].

[1]: http://i.imgur.com/yIynr.png
[2]: https://github.com/kien/ctrlp.vim/tree/extensions
[3]: http://kien.github.com/ctrlp.vim#installation
