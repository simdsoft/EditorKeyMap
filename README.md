# The x-studio365 EditorKeyMap template.

```lua
-- The x-studio365 KeyMap config file. 
-- Because x-studio365 use the powerful source editing component `scintilla`, so
-- we regard x-studio365 coding component abbv to: xs-sci

local SHIFT,CTRL,ALT,translateKeyMap = unpack(require('scicmds'))

-- Please edit this table to config custom shortcuts actions
-- The key & cmd is not Case Insensitive(不区分大小写)
-- For detail usage, see: https://docs.x-studio365.com/
-- Default KeyMap, see: https://github.com/x-studio365/scintilla/blob/master/src/KeyMap.cxx
-- The supported commands by xs-sci, see:
-- https://github.com/x-studio365/x-studio365/blob/master/tools/scicmds_autogen/scicmds.lua
local KeyMap = {
    -- {mods = SHIFT | CTRL, key = 'L', cmd = 'line_delete'},
    -- {mods = SHIFT | CTRL, key = 'E', cmd = 'duplicate_line'},
    -- {mods = CTRL, key = 'D', cmd = 'quick_add_next'},
    -- {mods = CTRL, key = 'T', cmd = 'swap_line_up'},
}

-- Translate human readable or sublime's cmd to xs-sci's
local sk2scik = {
    ['line_transpose'] = 'SCI_LINETRANSPOSE',
    ['swap_line_up'] = 'SCI_MOVESELECTEDLINESUP',
    ['swap_line_down'] = 'SCI_MOVESELECTEDLINESDOWN',
    ['line_delete'] = 'SCI_LINEDELETE',
    ['duplicate_line'] = 'SCI_LINEDUPLICATE',
    ['lower_case'] = 'SCI_LOWERCASE',
    ['upper_case'] = 'SCI_UPPERCASE',
    ['quick_add_next'] = 'SCI_QUICKADDNEXT',
}
for _,v in ipairs(KeyMap) do
    local scicmd = sk2scik[v.cmd]
    if scicmd then
        v.cmd = scicmd
    end
end

-- Translate human readable keys to xs-sci's
translateKeyMap(KeyMap)
package.loaded['scicmds'] = nil

return KeyMap
```
