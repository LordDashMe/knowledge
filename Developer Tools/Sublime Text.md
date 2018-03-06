# Sublime Text

#### Configuration for Sublime Text 3 Build 3143

##### PHP :bulb:

* Download Sublime Text 3 using below link:
    - General: https://www.sublimetext.com/3
    - Linux: https://www.sublimetext.com/docs/3/linux_repositories.html

* Use free license for Build 3143 by TwitterInc:
    ```
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

* Download the following packages:
    - phpfmt
    - SublimeLinter
    - SublimeLinter-php
    - PHPCompanion
    - GitGutter
    - A File Icon
    - Markdown Preview

* Configuration:
    - Set the User Settings of ```phpfmt``` - The default properties for PSR-2 Coding Style.
        ```
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
    - ```Ctrl + Shift + P``` 
        - To show the package installer for Sublime Text.
        - Also show the Packages that currently installed to the Sublime Instance.

* Usage:
    - Use ```F11``` to format the current PHP file using ```phpfmt``` configuration.