# IntelliJ-VSCode-keymap

A dirty version of VS Code (Visual Studio Code) keymap for IntelliJ IDEA.

All key bindings included are default ones of VS Code offered by the editor itself or its extensions.

Valid theoretically for other JetBrains IDEs (PyCharm, WebStorm, etc.).

## Install

The keymap config files are in the `keymaps` directory.

### Windows

Copy `VS Code for Windows.xml` to `%USERPROFILE%\.IntelliJIdea<xxx>\config\keymaps`.

### Linux

Copy `VS Code for Linux.xml` to `/home/<user>/.IntelliJIdea<xxx>/config/keymaps`.

## Note

### Install

If there is no `keymaps` directory in the IDE’s `config` directory, manually create it.

To actually change the keymap, open settings (`Ctrl+Alt+S`), select the Keymap page and choose "Visual Studio Code" in the dropdown menu. You will need to restart the IDE for it to show up.

Besides, if you have enabled Settings Sync, customized keymaps may won’t show up in the dropdown menu.

### About content

Key bindings that meet at least one of the following conditions are not included:

- Same in IntelliJ IDEA and VS Code;
- Not assigned with default values in VS Code;
- The `action id` in IntelliJ IDEA is unknown.

### Use

Some key bindings are conflicting between IntelliJ IDEA and VS Code, that is, some keyboard shortcuts in them are mapped to different operations. For instance, `Ctrl+Y` means **Redo** in VS Code, while it means **Delete line** in IntelliJ IDEA.

For this reason, my solution is to unassign the conflicting operations in IntelliJ IDEA with their keyboard shortcuts. So you can see some code like:

```xml
<action id="MethodDown"/>
<action id="MoveLineDown">        <!-- Move line down -->
    <keyboard-shortcut first-keystroke="alt DOWN"/>
</action>
```

where the operation in the first line of the example above is not assigned with any keyboard shortcut. That usually means **Method down** (from IntelliJ IDEA) and **Move line down** (from VS Code) had the same mapped keyboard shortcut `Alt+↓`. And now, **Method down** is not assigned with any keyboard shortcut, and `Alt+↓` means **Move line down**.

Of course, you can also reserve the default operations in IntelliJ IDEA of conflicted keyboard shortcuts. Just modify the keymap config file like:

```xml
<!-- <action id="MethodDown"/> -->
<action id="MoveLineDown">        <!-- Move line down -->
    <!-- <keyboard-shortcut first-keystroke="alt DOWN"/> -->
</action>
```

which means that **Method down** continues to retain its mapped default keyboard shortcut in IntelliJ IDEA and **Move line down** is unassigned with the keyboard shortcut `Alt+↓`.

You can also choose to delete the code commented or all of it in the example above.

## Reference

### Official documents

- [IntelliJ IDEA default keymap](https://resources.jetbrains.com/storage/products/intellij-idea/docs/IntelliJIDEA_ReferenceCard.pdf)
- [IntelliJ IDEA keymaps](https://github.com/JetBrains/intellij-community/tree/master/platform/platform-resources/src/keymaps)
- [Visual Studio Code keyboard shortcuts for Windows](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
- [Visual Studio Code keyboard shortcuts for Linux](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-linux.pdf)

### Open-source repositories

- [ekaragodin/idea-sublime-keymap](https://github.com/ekaragodin/idea-sublime-keymap)
- [gretro/intellij-vscode-keymap](https://github.com/gretro/intellij-vscode-keymap)