# Idea

See https://github.com/microsoft/vscode/issues/166631
<details>
  <summary>keybindings.json</summary>

```jsonc
// # keybindings.json
[
    {
        "key": "ctrl+i",
        "command": "toggle"
        "when": "editorTextFocus"
        "args": {
                "id": "Zen", // id must be unique
                "values": [
                        // Must have 2 settings objects with the same schema
                        {
                                "workbench.statusBar.visible": true,
                                "workbench.activityBar.visible": true,
                                "workbench.editor.showTabs": false,
                                "editor.minimap.enabled": true,
                        },
                        {
                                "workbench.statusBar.visible": false,
                                "workbench.activityBar.visible": false,
                                "workbench.editor.showTabs": true,
                                "editor.minimap.enabled": false,
                        }
                ]
        }, 
    },
    {
        "key": "ctrl+shift+i",
        "command": "cycle"
        "when": "editorTextFocus"
        "args": {
                "id": "Theme and Font", // id must be unique
                "values": [
                        // As many settings objects as desired, with the same schema
                        {
                                "workbench.colorTheme": "Default Light+",
                                "editor.fontFamily": "Consolas, monospace",
                        },
                        {
                                "workbench.colorTheme": "Default Dark+",
                                "editor.fontFamily": "'Cascadia Code', monospace",
                        },
                        {
                                "workbench.colorTheme": "Default High Contrast",
                                "editor.fontFamily": "'Fira Code', monospace",
                        }
                ]
        }, 
    }
]
```

</details>

# Toggle VS Code
Toggle any VS Code setting by your favorite keybindings.

## How To

Add below sample keybinding entry to your personal keybinding file and make changes accordingly.

```
{
	"key": "F3",
	"command": "toggle",
	"when": "editorTextFocus",
	"args": {
		"id": "minimap",
		"value": [
			{
				"editor.minimap.enabled": true
			},
			{
				"editor.minimap.enabled": false
			}
		]
	}
},
{
	"key": "F4",
	"command": "toggle",
	"when": "editorTextFocus",
	"args": {
		"id": "zen",
		"value": [
			{
				"editor.minimap.enabled": true,
				"workbench.statusBar.visible": true
			},
			{
				"editor.minimap.enabled": false,
				"workbench.statusBar.visible": false
			}
		]
	}
}
```

**key**
The shortcut you want to use

**command**
Command should always be `toggle`. You can create multiple keybindings and use the same `command` name.

**args**
arguments for the settings you want to toggle.

**args.id**
This is the **unique** id/name for the set of settings you want to toggle.

**args.value**
This is an array for settings you want to toggle. Every item in this array is a simple JavaScript dictionary, the format is like

```
{
	"<SettingName>": <SettingValue>,
	"<SettingName>": <SettingValue>,
	...
}
```

## Credit

<div>Icons made by <a href="http://www.flaticon.com/authors/bryn-taylor" title="Bryn Taylor">Bryn Taylor</a> from <a href="http://www.flaticon.com" title="Flaticon">www.flaticon.com</a> is licensed by <a href="http://creativecommons.org/licenses/by/3.0/" title="Creative Commons BY 3.0" target="_blank">CC 3.0 BY</a></div>
