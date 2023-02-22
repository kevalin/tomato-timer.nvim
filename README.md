# tomato-timer.nvim
Focus tomato timer 🍅🕗🎯

## Usage

To add configuration to lualine, you can edit the require'lualine'.setup function in your init.lua file.

For example, to add a new section to lualine that displays the current git branch, you can add the following code to the require'lualine'.setup function:

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
      require('kevalin.tomato').message
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
