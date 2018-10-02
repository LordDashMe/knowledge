# Sublime Text

## Custom Side Bar

- To add custom size of the sidebar apply the below code in the Default Theme used.

```json
{
    "class": "icon_folder",
    "layer0.texture": "Theme - Default/common/light/folder_closed.png",
    "layer0.opacity": 0.3,
    "content_margin": [8, 7]
},
{
    "class": "icon_folder",
    "parents": [{"class": "tree_row", "attributes": ["expanded"]}],
    "layer0.texture": "Theme - Default/common/light/folder_open.png",
    "layer0.opacity": 0.3,
    "content_margin": [8, 7]
},
{
    "class": "sidebar_label",
    "font.size": 12,
},

```

## :wrench: Refresh

- To enable the refresh project using a keyboard key for example using ```F5``` follow the steps below:

  - Preferences > Key Bindings - User

  - Add the code below:

    ```json
    {
        "keys"    : ["f5"],
        "command" : "refresh_folder_list"
    }
    ```

---

## Configuration for Sublime Text 3 Build 3176

- Download Sublime Text 3 using below link:

  - General: <https://www.sublimetext.com/3>

  - Linux: <https://www.sublimetext.com/docs/3/linux_repositories.html>

- Use free license for Build 3176 sgbteam:

    ```text
    ----- BEGIN LICENSE -----
    sgbteam
    Single User License
    EA7E-1153259
    8891CBB9 F1513E4F 1A3405C1 A865D53F
    115F202E 7B91AB2D 0D2A40ED 352B269B
    76E84F0B CD69BFC7 59F2DFEF E267328F
    215652A3 E88F9D8F 4C38E3BA 5B2DAAE4
    969624E7 DC9CD4D5 717FB40C 1B9738CF
    20B3C4F1 E917B5B3 87C38D9C ACCE7DD8
    5F7EF854 86B9743C FADC04AA FB0DA5C0
    F913BE58 42FEA319 F954EFDD AE881E0B
    ------ END LICENSE ------
    ```

## Configuration for Sublime Text 3 Build 3143

- Download Sublime Text 3 using below link:

  - General: <https://www.sublimetext.com/3>

  - Linux: <https://www.sublimetext.com/docs/3/linux_repositories.html>

- Use free license for Build 3143 by TwitterInc:

    ```text
    —– BEGIN LICENSE —–
    TwitterInc
    200 User License
    EA7E-890007
    1D77F72E 390CDD93 4DCBA022 FAF60790
    61AA12C0 A37081C5 D0316412 4584D136
    94D7F7D4 95BC8C1C 527DA828 560BB037
    D1EDDD8C AE7B379F 50C9D69D B35179EF
    2FE898C4 8E4277A8 555CE714 E1FB0E43
    D5D52613 C3D12E98 BC49967F 7652EED2
    9D2D2E61 67610860 6D338B72 5CF95C69
    E36B85CC 84991F19 7575D828 470A92AB
    —— END LICENSE ——
    ```

## :bulb: PHP Stack

- Download the following packages:

  - phpfmt

  - SublimeLinter

  - SublimeLinter-php

  - PHPCompanion

  - GitGutter

  - A File Icon

  - Markdown Preview

- Configuration:

  - Set the User Settings of ```phpfmt``` - The default properties for PSR-2 Coding Style.

    ```json
    {
        "autocomplete": false,
        "autoimport": false,
        "excludes":
        [
            "OnlyOrderUseClauses",
            "OrderAndRemoveUseClauses",
            "OrderMethod"
        ],
        "format_on_save": false,
        "indent_with_space": 4,
        "passes":
        [
            "GeneratePHPDoc",
            "StripNewlineWithinClassBody",
            "AutoSemicolon",
            "SortUseNameSpace"
        ],
        "psr1": false,
        "psr1_naming": false,
        "psr2": true,
        "readini": false,
        "version": 1
    }
    ```

  - Ctrl + Shift + P

    - To show the package installer for Sublime Text.

    - Also show the Packages that currently installed to the Sublime Instance.

- Usage:

- Use ```F11``` to format the current PHP file using ```phpfmt``` configuration.