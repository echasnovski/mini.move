<img src="https://github.com/echasnovski/media/blob/main/mini.nvim/logo/logo_move.png" style="width: 100%">

<!-- badges: start -->
[![GitHub license](https://badgen.net/github/license/echasnovski/mini.nvim)](https://github.com/echasnovski/mini.nvim/blob/main/LICENSE)
<!-- badges: end -->

### Move any selection in any direction

See more details in [Features](#features) and [help file](doc/mini-move.txt).

---

⦿ This is a part of [mini.nvim](https://github.com/echasnovski/mini.nvim) library. Please use [this link](https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-move.md) if you want to mention this module.

⦿ All contributions (issues, pull requests, discussions, etc.) are done inside of 'mini.nvim'.

⦿ See the repository page to learn about common design principles and configuration recipes.

---

If you want to help this project grow but don't know where to start, check out [contributing guides of 'mini.nvim'](https://github.com/echasnovski/mini.nvim/blob/main/CONTRIBUTING.md) or leave a Github star for 'mini.nvim' project and/or any its standalone Git repositories.

## Demo

https://user-images.githubusercontent.com/24854248/212487956-5c25df54-f754-40b8-84a1-1a9b15ab03d3.mp4

## Features

- Works in two modes:
    - Visual mode. Select text (charwise with `v`, linewise with `V`, and blockwise with `CTRL-V`) and press customizable mapping to move in all four directions (left, right, down, up). It keeps Visual mode.
    - Normal mode. Press customizable mapping to move current line in all four directions (left, right, down, up).
    - Special handling of linewise movement:
        - Vertical movement gets reindented with `=`.
        - Horizontal movement is improved indent/dedent with `>` / `<`.
        - Cursor moves along with selection.
- Provides both mappings and Lua functions for motions. See `:h MiniMove.move_selection()` and `:h MiniMove.move_line()`.
- Respects `v:count`. Movement mappings can be preceded by a number which multiplies command effect.
- All consecutive moves (regardless of direction) can be undone by a single `u`.
- Respects preferred column for vertical movement. It will vertically move selection as how cursor is moving (not strictly vertically if target column is not present in target line).

## Installation

This plugin can be installed as part of 'mini.nvim' library (**recommended**) or as a standalone Git repository.

<!-- TODO: Uncomment use of `stable` branch before 0.7.0 release -->

<!-- There are two branches to install from: -->

During beta-testing phase there is only one branch to install from:

- `main` (default, **recommended**) will have latest development version of plugin. All changes since last stable release should be perceived as being in beta testing phase (meaning they already passed alpha-testing and are moderately settled).
<!-- - `stable` will be updated only upon releases with code tested during public beta-testing phase in `main` branch. -->

Here are code snippets for some common installation methods (use only one):

- Using [wbthomason/packer.nvim](https://github.com/wbthomason/packer.nvim):

<table>
    <thead>
        <tr>
            <th>Github repo</th>
            <th>Branch</th> <th>Code snippet</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <!-- <td rowspan=2>'mini.nvim' library</td> -->
            <td rowspan=1>'mini.nvim' library</td>
            <td>Main</td> <td><code>use 'echasnovski/mini.nvim'</code></td>
        </tr>
        <!-- <tr> -->
        <!--     <td>Stable</td> <td><code>use { 'echasnovski/mini.nvim', branch = 'stable' }</code></td> -->
        <!-- </tr> -->
        <tr>
            <!-- <td rowspan=2>Standalone plugin</td> <td>Main</td> <td><code>use 'echasnovski/mini.move'</code></td> -->
            <td rowspan=1>Standalone plugin</td> <td>Main</td> <td><code>use 'echasnovski/mini.move'</code></td>
        </tr>
        <!-- <tr> -->
        <!--     <td>Stable</td> <td><code>use { 'echasnovski/mini.move', branch = 'stable' }</code></td> -->
        <!-- </tr> -->
    </tbody>
</table>

- Using [junegunn/vim-plug](https://github.com/junegunn/vim-plug):

<table>
    <thead>
        <tr>
            <th>Github repo</th>
            <th>Branch</th> <th>Code snippet</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <!-- <td rowspan=2>'mini.nvim' library</td> -->
            <td rowspan=1>'mini.nvim' library</td>
            <td>Main</td> <td><code>Plug 'echasnovski/mini.nvim'</code></td>
        </tr>
        <!-- <tr> -->
        <!--     <td>Stable</td> <td><code>Plug 'echasnovski/mini.nvim', { 'branch': 'stable' }</code></td> -->
        <!-- </tr> -->
        <tr>
            <!-- <td rowspan=2>Standalone plugin</td> <td>Main</td> <td><code>Plug 'echasnovski/mini.move'</code></td> -->
            <td rowspan=1>Standalone plugin</td> <td>Main</td> <td><code>Plug 'echasnovski/mini.move'</code></td>
        </tr>
        <!-- <tr> -->
        <!--     <td>Stable</td> <td><code>Plug 'echasnovski/mini.move', { 'branch': 'stable' }</code></td> -->
        <!-- </tr> -->
    </tbody>
</table>

**Important**: don't forget to call `require('mini.move').setup()` to enable its functionality.

**Note**: if you are on Windows, there might be problems with too long file paths (like `error: unable to create file <some file name>: Filename too long`). Try doing one of the following:
- Enable corresponding git global config value: `git config --system core.longpaths true`. Then try to reinstall.
- Install plugin in other place with shorter path.

## Default config

```lua
-- No need to copy this inside `setup()`. Will be used automatically.
{
  -- Module mappings. Use `''` (empty string) to disable one.
  mappings = {
    -- Move visual selection in Visual mode. Defaults are Alt (Meta) + hjkl.
    left = '<M-h>',
    right = '<M-l>',
    down = '<M-j>',
    up = '<M-k>',

    -- Move current line in Normal mode
    line_left = '<M-h>',
    line_right = '<M-l>',
    line_down = '<M-j>',
    line_up = '<M-k>',
  },
}
```

## Similar plugins

- [matze/vim-move](https://github.com/matze/vim-move)
- [booperlv/nvim-gomove](https://github.com/booperlv/nvim-gomove)
