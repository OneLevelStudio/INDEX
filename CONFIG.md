
# Plugins & Navbar

```space-lua
config.set {
  -- ================================================== --
  -- ================================================== --
  -- ================================================== --
  plugs = {
	  "github:OneLevelStudio/INDEX/treeview.plug.js",
  },
  -- ================================================== --
  -- ================================================== --
  -- ================================================== --
  -- The treeview plug configuration
  treeview = {
    position = "lhs", -- "lhs" / "rhs" / "bhs" / "modal"
    size=0.30,
    dragAndDrop = { enabled = false, confirmOnRename = true },
    exclusions = {
      { type = "regex", rule="^(?:CONFIG|Library).*$", negate= false },
      { type = "tags", tags = {"meta"}, negate = false }
    }
  },
  -- ================================================== --
  -- ================================================== --
  -- ================================================== --
  actionButtons = {
    {
      icon = "home", description = "Home",
      run = function() editor.invokeCommand("Navigate: Home") end
    },
    {
      icon = "folder", description = "Folder",
      run = function() editor.invokeCommand("Tree View: Toggle") end
    },
    {
      icon = "search", description = "Search",
      run = function() editor.invokeCommand("Navigate: Page Picker") end
    },
    {
      icon = "command", description = "Run command",
      run = function() editor.invokeCommand "Open Command Palette" end,
    },
    {
      icon = "settings", description = "Config",
      run = function() editor.navigate { page = "CONFIG" } end
    },
    {
      icon = "box", description = "One Level Studio",
      run = function() editor.openUrl "https://onelevel.studio" end
    },
  },
  -- ================================================== --
  -- ================================================== --
  -- ================================================== --
}
```

# Custom CSS

```space-style
/* priority: 1 */

@import url('https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=block');
@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&display=block');

:root {
    --bdrd: 8px;
}
html[data-theme=dark] {
    --root-background-color: hsl(0, 0%, 5%);
    --top-background-color: hsl(0, 0%, 5%);
    --top-border-color: hsla(0, 0%, 50%, 0.20);
    --subtle-background-color: hsla(0, 0%, 50%, 0.15);
    --meta-color: hsl(0, 25%, 70%);
    --link-color: hsl(0, 25%, 70%);
    --root-color: hsl(0, 0%, 80%);
}

*,
*::before,
*::after {
    font-family: "Inter", monospace;
    font-size: 16px;
    font-weight: 400;
    line-height: 1.5;
}

img {
    border-radius: var(--bdrd);
}

/* ---------- Disable TOS ---------- */
.sb-widget-array {
    display: none !important;
}

/* ---------- Header ---------- */
#sb-top .cm-line {
    font-family: "JetBrains Mono", monospace;
    font-size: 1.6rem !important;
    font-weight: 600 !important;
    text-transform: uppercase !important;
}
.sb-modal-box .sb-header label {
    margin: 0.1rem 0 0 0.5rem !important;
}
.sb-modal-box .sb-header .sb-mini-editor {
    margin: 0 0 0.5rem 0.5rem !important;
}
.sb-modal-box .sb-help-text,
.sb-modal-box .sb-help-text * {
    font-family: "JetBrains Mono", monospace;
    font-size: 0.7rem !important;
    font-weight: 300 !important;
}
.sb-hint {
    font-family: "JetBrains Mono", monospace;
}

/* ---------- Code ---------- */
.sb-line-fenced-code {
    padding-left: 1.8rem !important;
}
.sb-line-fenced-code *,
.sb-code {
    font-family: "JetBrains Mono", monospace;
    font-size: 0.95rem !important;
    font-weight: 300 !important;
}
.sb-code {
    color: var(--meta-color) !important;
    border-radius: 4px !important;
    padding: 0 0.3rem !important;
}
.sb-line-code-outside {
    border-radius: 0 0 var(--bdrd) var(--bdrd) !important;
}
.sb-line-code-outside:has(.sb-actions) {
    border-radius: var(--bdrd) var(--bdrd) 0 0 !important;
}
.sb-code-info {
    font-size: 0.8rem !important;
    margin: 0.7rem 0 0 0 !important;
}
.sb-code-copy-button {
    margin: 0.5rem 0.4rem 0 0 !important;
}

/* ---------- Headings ---------- */
.sb-h1 { font-size: 2.000rem; font-weight: 800; }
.sb-h2 { font-size: 1.666rem; font-weight: 700; }
.sb-h3 { font-size: 1.333rem; font-weight: 600; }
.sb-header-inside.sb-line-h1 { text-indent: -26.75px !important; }
.sb-header-inside.sb-line-h2 { text-indent: -39.5px !important; }
.sb-header-inside.sb-line-h3 { text-indent: -45.5px !important; }

/* ---------- List ---------- */
.sb-line-li {
    margin: 6px 0 !important;
}
.sb-line-li-1 {
    text-indent: -1.7rem !important;
    padding-left: 2.1rem !important;
}
.sb-line-li-2 {
    text-indent: -3.0rem !important;
    padding-left: 4.0rem !important;
}
.sb-line-li-3 {
    text-indent: -4.2rem !important;
    padding-left: 5.8rem !important;
}
.sb-line-li-4 {
    text-indent: -5.5rem !important;
    padding-left: 7.8rem !important;
}
.sb-line-li-5 {
    text-indent: -6.8rem !important;
    padding-left: 9.8rem !important;
}

/* ---------- Blockquote ---------- */
.sb-line-blockquote {
    text-indent: 1rem !important;
}
.sb-admonition,
.sb-admonition-title {
    text-indent: 0rem !important;
    padding: 0.5rem !important;
}
.sb-admonition {
    border-radius: 0 0 var(--bdrd) var(--bdrd) !important;
}
.sb-admonition-title {
    border-radius: var(--bdrd) var(--bdrd) 0 0 !important;
}
.sb-admonition-type::before {
    margin-bottom: 3px !important;
}

/* ---------- Scrollbar ---------- */
::-webkit-scrollbar {
    background: transparent;
    width: 10px;
    border-radius: 999px;
}

::-webkit-scrollbar-track {
    background: transparent;
    border-radius: 999px;
}

::-webkit-scrollbar-thumb {
    background: hsla(0, 0%, 50%, 0.5);
    border-radius: 999px;
}

::-webkit-scrollbar-thumb:hover {
    background: hsla(0, 0%, 50%, 0.7);
}

/* ---------- Plugin - TreeView ---------- */
html {
    --treeview-folder-color: hsla(0, 0%, 100%, 0.4);
    --treeview-page-color: hsla(0, 0%, 100%, 0.6);
    --treeview-current-page-color: hsla(0, 0%, 100%, 0.8);
}
#sb-main .sb-panel {
    position: fixed;
    height: 100%;
    z-index: 1;
}
#sb-main .sb-panel:first-child {
    border-right: none;
}
#sb-top .panel {
    display: none !important;
}
.tree__label > span {
    width: 100% !important;
    border: none !important;
    padding: 0.4rem 0.8rem !important;
    font-size: 1rem !important;
    text-transform: uppercase !important;
    transition: all ease 0.2s !important;
    background: hsla(0, 0%, 50%, 0.0) !important;
}
.tree__label > span:hover,
.tree__label > span[data-current-page="true"],
.tree__label > span[data-current-page="true"]:hover {
    background: hsla(0, 0%, 50%, 0.2) !important;
}
.treeview-actions {
    background: transparent;
    border: none;
}
.tree__collapse {
    color: hsla(0, 0%, 100%, 0.4);
    transition: all ease 0.2s;
}
.tree__collapse:hover {
    color: hsla(0, 0%, 100%, 0.6);
}
button[data-treeview-action="close-panel"] {
    display: none;
}
```
