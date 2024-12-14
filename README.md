# tinted-lua

> See the [Tinted theming repository](https://github.com/tinted-theming/home) for more information.
> This theme was built with [Tinted Builder Rust](https://github.com/tinted-theming/tinted-builder-rust).

[Base24](https://github.com/tinted-theming/base24) and [base16](https://github.com/tinted-theming/home/blob/main/styling.md) color schemes for use in lua scripting.

## Example usage

**Modifying the [`cattpuccin`](https://github.com/catppuccin/nvim) color palette to be `base24` compatible.**

This assumes [`lazy.nvim`](https://github.com/folke/lazy.nvim) is used to manage plugin.

Copy over a [`base24` color scheme file](schemes/base24) to `~/.config/nvim/lua/config/colors-base24.lua`

In `~/.config/nvim/lua/plugins/cattpuccin.lua`:

```lua
return {
  {
    "catppuccin/nvim",
    name = "catppuccin",
    lazy = false,
    opts = function(_, opts)
      local base24 = require("config.colors-base24")
      local utils = require("catppuccin.utils.colors")

      local steps = 2
      local interpolated = {}
      for i = 1, steps do
        local t = i / (steps + 1)
        table.insert(interpolated, utils.blend(base24.base04, base24.base05, t))
      end

      opts.color_overrides = {
        mocha = {
          rosewater = base24.base14,
          flamingo = base24.base0F,
          pink = base24.base17,
          mauve = base24.base0E,
          red = base24.base08,
          maroon = base24.base12,
          peach = base24.base09,
          yellow = base24.base0A,
          green = base24.base0B,
          teal = base24.base0C,
          sky = base24.base15,
          sapphire = base24.base16,
          blue = base24.base0D,
          lavender = base24.base13,
          text = base24.base07,
          subtext1 = base24.base06,
          subtext0 = base24.base05,
          overlay2 = interpolated[1],
          overlay1 = interpolated[2],
          overlay0 = base24.base04,
          surface2 = base24.base03,
          surface1 = base24.base02,
          surface0 = base24.base01,
          base = base24.base00,
          mantle = base24.base10,
          crust = base24.base11,
        },
      }
    end,
  },
}
```
