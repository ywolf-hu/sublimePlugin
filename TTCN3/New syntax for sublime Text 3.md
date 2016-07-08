#New syntax for sublime Text 3
[TOC]

##Introduction of Text mate language grammer

**match rule**:
```yaml
    - match: (\btype\b)\s+(\b[a-zA-Z0-9_]*\b)(.*)
      captures: 
        1: keyword.other.ttcn3
        2: storage.type.ttcn3
        3: entity.name.struct.ttcn3
```
This rule will styling 'type component Ue' with keyword.other.ttcn3/storage.type.ttcn3/entity.name.struct.ttcn3 based on corresponding theme

```yaml
    - match: function\s+([a-zA-Z][a-zA-Z0-9_]+)
      scope: keyword.function.ttcn3
      captures:
        1: entity.name.function.ttcn3
```
This rule will styling 'function' with keyword.function.ttcn3 and 'CellSetupWithUnavailableX2' with entity.name.function.ttcn3

```yaml
  main:
    - match: \/\*.*
      scope: comment.line.block.ttcn3
      set: mutilinecomment

  mutilinecomment:

    - match: .*\*\/
      scope: comment.line.block.ttcn3
      pop: true

    - match: .*
      scope: comment.line.block.ttcn3
```
This rule will styling block comments with comment.line.block.ttcn3 when meet '/*', and return main context after match */ which means main rules will be used for styling following lines

##Introduction of Theme
**scope selector** to styling language element according to scope name
Take **Monokai.tmTheme** for example(located in Packages\Color Scheme - Default.sublime-package)
```xml
        <dict>
            <key>name</key>
            <string>Storage type</string>
            <key>scope</key>
            <string>storage.type</string>
            <key>settings</key>
            <dict>
                <key>fontStyle</key>
                <string>italic</string>
                <key>foreground</key>
                <string>#66D9EF</string>
            </dict>
        </dict>
```
This means element of storage.type will be displayed in *italic* and #66D9EF(RRGGBB)

##How to install new syntax package
**Linux**: 
    - Drop <newLanguage>.sublime-syntax to ~/.config/sublime-text-3/Packages/User/
    - Drop <newLanguage>.theme to ~/.config/sublime-text-3/Packages/User/

##Reference
[Text mate language grammer support](http://manual.macromates.com/en/language_grammars)
[SublimeText3 Syntax](http://www.sublimetext.com/docs/3/syntax.html)