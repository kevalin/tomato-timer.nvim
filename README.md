# tomato-timer.nvim
Focus tomato timer 🍅 🕗 🎯

## Install

### Packer

```lua
use { 'Kevalin/tomato-timer.nvim', requires = 'rcarriga/nvim-notify' }
```

## Configuration

You can setup four variables:

- `chunk`, it means a long break after running how many rounds. Default value is 4 times.
- `round`, it means the time of each focus. Default value is 25 minutes.
- `short_break`, it means the time of each short break, and after every focus there is a short break. Default value is 5 minutes.
- `long_break`, it means the time of each long break, and after 4 times focus there is a long break. Default value is 15 minutes.

```lua
local ok, tomato = pcall(require, 'tomato')
if not ok then return end

tomato.setup({
  chunk = 4,
  round = 25,
  short_break = 5,
  long_break = 15,
})
```

## Usage

To add configuration to lualine, you can edit the `require'lualine'.setup` function in your init.lua file.

For example, to add a new section to lualine that displays the current git branch, you can add the following code to the `require'lualine'.setup` function:

```lua
lualine.setup {
  options = {
    icons_enabled = true,
    theme = "tokyonight",
    component_separators = { left = "", right = "" },
    section_separators = { left = "", right = "" },
    disabled_filetypes = {},
    always_divide_middle = true,
  },
  sections = {
    lualine_a = { "mode" },
    lualine_b = { "branch", "diff", "diagnostics" },
    lualine_c = {
      { "filename" },
      require('tomato').message
    },
    lualine_x = { "encoding", "fileformat", "filetype" },
    lualine_y = { "progress" },
    lualine_z = { "location" },
  },
  inactive_sections = {
    lualine_a = {},
    lualine_b = {},
    lualine_c = { "filename" },
    lualine_x = { "location" },
    lualine_y = {},
    lualine_z = {},
  },
  tabline = {},
  extensions = {},
}
```
You can get a timer on your lualine. Like this:

![图片](https://user-images.githubusercontent.com/3123807/221552993-536d51f9-b4cb-4332-876b-2ac7687886d1.png)

![图片](https://user-images.githubusercontent.com/3123807/221553083-a28a6e35-95fd-4531-8cd0-c6146e00373c.png)

![图片](https://user-images.githubusercontent.com/3123807/221553276-eb157d3c-3e43-4b88-9f09-634c519399ba.png)

![图片](https://user-images.githubusercontent.com/3123807/221553621-09871332-2ea5-48be-95b0-66d24554fedd.png)

### start timer

```lua
lua require('tomato').start_round()
```

Next, It will automatically start the timer in a loop.

### reset timer

```lua
lua require('tomato').reset()
```

### keymaps

You You can also set some shortcut keys, such as my current configuration:

```lua
local map = vim.api.nvim_set_keymap
local opts = { noremap = true, silent = true }

map('n', '<C-t>', "<cmd>lua require('tomato').start_round()<CR>", opts)
map('n', '<C-r>', "<cmd>lua require('tomato').reset()<CR>", opts)
```

## TODO

- [ ] a control float window
- [ ] a stats html about focus detail data


