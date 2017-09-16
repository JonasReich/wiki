# Welcome
This wiki is supposed to be a personal notebook and knowledge-base for anything related to gamedev that isn't properly documented elsewhere.

## Engines
### [Unreal Engine 4](unreal/readme.md)
[_Official Documentation_](https://docs.unrealengine.com/latest/INT/)
### [Unity3D](unity/readme.md)

## Windows
[_Creating Shortcut Menu Handlers (MSDN)_](https://msdn.microsoft.com/en-us/library/cc144171(v=VS.85).aspx#custom_verbs_desktop) allows defining custom behaviour for file types/folder context menus in Windows

## Languages
### C++
### C#
### Markdown

This wiki is written in Markdown and processed by [_Jekyll_](https://jekyllrb.com/).
Here are some links to get you started:

* [_Markdown Cheat Sheet_](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
* [_Markdown Table Generator_](http://www.tablesgenerator.com/markdown_tables)

Please make all [_links to external pages_](google.com) _italic_, so we can differentiate them more easily from [links to other wiki pages](git.md).

## Algorithms
[_Roguelike Vision Algorithms (Tile Based)_](http://www.adammil.net/blog/v125_Roguelike_Vision_Algorithms.html)

## [Git](git.md)

## Powershell
Windows 10 abandoned the cmd as default CLI, so it might be useful to get familiar with its main CLI: The Powershell

### Default startup script
Located under ```C:\Users\[username]\Documents\WindowsPowershell\profile.ps1```, which can be shortened to ```$home\Documents\WindowsPowershell\profile.ps1```

### Aliases

single word commands:
```powershell
Set-Alias AliasName AliasCommand
```
if you want to create an alias for use multi word commands, you'll have to wrap it in a function (which is a perfectly fine way to define alias in the first place btw)
```powershell
function DoSomething {
    multi word command --with arguments
}

Set-Alias AliasName DoSomething
```

## Tools
### TreeSize
View Directory Size
[Official Site](https://www.jam-software.com/treesize_free/)
