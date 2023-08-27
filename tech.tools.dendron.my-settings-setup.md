---
id: 5pgkbods9jp1qawta9tw6u5
title: My Settings/Setup
desc: ''
updated: 1673908269943
created: 1673907833988
---

## VSCode settings
### 'workbench.editor.enablePreview'  set to 'false'.
This is done to be able to use `"workbench.action.showAllEditorsByMostRecentlyUsed"` command, to navigate between recently used files with greater ease.

<details>
<summary>Screenshot </summary>

![img](/assets/images/Screen_Shot_2023-01-16_at_2.26.34_PM.png){max-width: 500px, display: block, margin: 0 auto}
</details>

## dendron.yml
### bubbleUpCreateNew set to false

```yml
commands:
    lookup:
        note:
            bubbleUpCreateNew: false
```

This is done to optimize for lookup rather than creation of notes. (Keep create new at the bottom).

### selectionMode set to none
```yml
commands:
    lookup:
        note:
            selectionMode: none
```
To avoid accidentally moving code out 