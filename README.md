# Maximarine

A warm, earthy colorscheme with a single cool anchor, named in the spirit of [Hamlindigo Blue](https://en.wikipedia.org/wiki/Better_Call_Saul) from *Better Call Saul*.

---

## Palette

| Name       | Hex       | Role                               |
|------------|-----------|------------------------------------|
| light      | `#ede8e0` | Primary background (light theme)  |
| light-gray | `#d9d1c5` | Secondary background (light theme)|
| gray       | `#9a8f82` | Borders, flags, faint text        |
| dark-gray  | `#4a4238` | Muted text                        |
| dark       | `#3a2e28` | Primary text (light theme)        |
| secondary  | `#a67c6d` | Accent, cursor                    |
| tertiary   | `#8b7f73` | Subtle accent                     |
| rust       | `#b86b65` | Errors, keywords, dirty marker    |
| clay       | `#c98880` | Functions, separator              |
| ochre      | `#cc9e54` | Numbers, constants, separator     |
| sage       | `#869c7a` | Strings, commands, separator      |
| pine       | `#56706b` | Path, clean marker                |
| **slate**  | `#a8bef0` | types, git info                   |
| mauve      | `#9d868e` | Namespaces, preprocessor          |

---

## Terminal (Ghostty) — pine depth
The terminal layer sets background, foreground, cursor, and the 16 ANSI color slots. This is what gives `ls`, `git diff`, `grep --color`, and other tools their colors.

```
background = 1a1714       ← dark chocolate
foreground = ebe7e1       ← warm cream
cursor-color = c59b8d     ← dusty rose
```

ANSI slots:

```
 0  #2a2520  black          8  #4a4238  bright black
 1  #b86b65  red (rust)     9  #c98880  bright red (clay)
 2  #869c7a  green (sage)  10  #aebd9f  bright green
 3  #cc9e54  yellow        11  #e0bc7e  bright yellow
 4  #a8bef0  blue (slate)  12  #a8bef0  bright blue
 5  #9d868e  magenta       13  #c98880  bright magenta
 6  #56706b  cyan (pine)   14  #8daeb3  bright cyan
 7  #d4cec7  white         15  #ebe7e1  bright white
```

Drop the config snippet into `~/.config/ghostty/config`.

### What it looks like

**`ls -la`** — directories pick up ANSI blue (Maximarine), executables get green (sage):
```
drwxr-xr-x  projects/          ← #a8bef0
drwxr-xr-x  cake/              ← #a8bef0 
-rwxr-xr-x  build.sh           ← #869c7a
-rw-r--r--  CMakeLists.txt
```

**`git diff`** — additions in sage, deletions in rust:
```
- const auto old_value = get();    ← #b86b65 rust
+ const auto new_value = fetch();  ← #869c7a sage
```

**`grep --color`** — matches highlight in clay (bright red slot):
```
src/cake.cpp:  m_loop.run();     ← match in #c98880 clay
```

---

## Prompt (oh-my-zsh) — pine depth variant
The prompt uses pine for the working directory, a sage → ochre → clay separator cascade, and Maximarine exclusively for git info.

```zsh
~/projects/mike ❯❯❯       (main*)   ← dirty: rust * 
~               ❯❯❯       (main ✓)  ← clean: pine ✓
```

Color breakdown:

| Element         | Color              | Hex       |
|-----------------|--------------------|-----------|
| Working dir     | pine               | `#56706b` |
| Separator 1     | sage               | `#869c7a` |
| Separator 2     | ochre              | `#cc9e54` |
| Separator 3     | clay               | `#c98880` |
| Git text        | slate              | `#a8bef0` |
| Git parens      | slate              | `#a8bef0` |
| Dirty marker `*`| rust               | `#b86b65` |
| Clean marker `✓`| pine               | `#56706b` |

Install: copy `max.zsh-theme` to `~/.oh-my-zsh/themes/max.zsh-theme`, then set `ZSH_THEME="max"` in `.zshrc`.

---

## Syntax highlighting (zsh-syntax-highlighting)

Controls token coloring as you type. Paste the `zsh-highlight.zsh` contents into `.zshrc` after sourcing oh-my-zsh.

| Token                | Color   | Hex       |
|----------------------|---------|-----------|
| command / builtin    | sage    | `#869c7a` |
| string / path        | sage+   | `#aebd9f` |
| alias                | clay+   | `#d9a89a` |
| globbing / history   | ochre+  | `#e0bc7e` |
| flags (`-f`, `--flag`)| gray  | `#9a8f82` |
| separators / pipes   | rust+   | `#db8e88` |
| unknown token        | rust+   | `#db8e88` underline |
| comment              | dim     | `#6b6158` |
| default              | cream   | `#ebe7e1` |


---

## Neovim

Pure Lua, no dependencies. Requires Neovim 0.8+.

```lua
vim.cmd.colorscheme "maximarine"
```

Copy `maximarine.lua` to `~/.config/nvim/colors/maximarine.lua`.

---

## Obsidian

Drop `maximarine.css` into `.obsidian/snippets/` and enable it under **Appearance → CSS snippets**. Covers both `.theme-light` and `.theme-dark`.
