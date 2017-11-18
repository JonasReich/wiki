# Welcome
This wiki is supposed to be a personal notebook and knowledge-base for anything related to gamedev that isn't properly documented elsewhere.

## Engines
### [Unreal Engine 4](unreal/readme.md)
[_Official Documentation_](https://docs.unrealengine.com/latest/INT/)
### [Unity3D](unity/readme.md)

## Windows
[_Creating Shortcut Menu Handlers (MSDN)_](https://msdn.microsoft.com/en-us/library/cc144171(v=VS.85).aspx#custom_verbs_desktop) allows defining custom behaviour for file types/folder context menus in Windows

## Programming Languages
### C++
### C#
### Markdown

This wiki is written in Markdown and processed by [_Jekyll_](https://jekyllrb.com/).
Here are some links to get you started:

* [_Markdown Cheat Sheet_](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
* [_Markdown Table Generator_](http://www.tablesgenerator.com/markdown_tables)

Please make all [_links to external pages_](google.com) _italic_, so we can differentiate them more easily from [links to other wiki pages](git.md).

## Algorithms
* [_Roguelike Vision Algorithms (Tile Based)_](http://www.adammil.net/blog/v125_Roguelike_Vision_Algorithms.html)
* [_Red Blob Games_](https://www.redblobgames.com/): Amit Patel's extensive collection of programming tutorials (e.g. on pathfinding) and resources
* [_Fernando Bevilacqua: Steering_](https://tutsplus.com/authors/fernando-bevilacqua): Tutorial series on flocking, steering and similar simple AI movement

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
### Resharper
[_Speeding Up Resharper_](https://www.jetbrains.com/help/resharper/2016.2/Speeding_Up_ReSharper.html)
### TreeSize
[_TreeSize_](https://www.jam-software.com/treesize_free/) allows to get an overview of directory contents and sort by size.
### Piskel
[_http://www.piskelapp.com/_] is a browser based pixel art sprite editor. Great for programmers that need quick WIP sprites without the need to download dedicated tools. Even allows simple animation!

## External Sites
### News + Blogs
* [_Gamasutra_](http://www.gamasutra.com/): News, postmortems, interviews and opinion pieces from community members. Every once in a while there are more detailed process descriptions/how-to's. See my [Gamasutra link dump](gamasutra.md).
* [_Extra Credits (YouTube)_](https://www.youtube.com/user/ExtraCreditz): Various illustrated video blogs/essays. The vlogs mostly cover gamedesign and the state of the industry
* [_Game Makers Tooltip (YouTube)_](https://www.youtube.com/user/McBacon1337): Game journalist Dan Brown's video essays on game/level design 

### Stats
* [_Steam Hardware Survey_](http://store.steampowered.com/hwsurvey/): useful for gathering hardware related stats, e.g. when setting min specs for a game
* [_Videogame Chartz_](http://www.vgchartz.com/): Known game sales data from several platforms (mostly consoles)
* [_Steam Spy_](http://steamspy.com/): _Estimated_ sales from Steam, gathered by automated steam user profile scans
