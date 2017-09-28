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
### Resharper
[_Speeding Up Resharper_](https://www.jetbrains.com/help/resharper/2016.2/Speeding_Up_ReSharper.html)
### TreeSize
View Directory Size
[Official Site](https://www.jam-software.com/treesize_free/)

## Gamasutra Dump
* [_Prototyping a Dynamic Camera System_](https://www.gamasutra.com/blogs/SamanthaStahlke/20170919/305840/Prototyping_a_Dynamic_Camera_System.php)
* [_Unity debuts open-source beta of a new machine learning AI toolkit_](https://www.gamasutra.com/view/news/306061/Unity_debuts_opensource_beta_of_a_new_machine_learning_AI_toolkit.php)
* [_Creating a Dynamic Tile System_](https://www.gamasutra.com/blogs/RyanMiller/20170915/305738/Creating_a_Dynamic_Tile_System.php)
* [_Lessons from Suzy Cube: The Camera System, Part 1_](https://www.gamasutra.com/blogs/LouisNicolasDozois/20170907/305251/Lessons_from_Suzy_Cube_The_Camera_System_Part_1.php)
* [_Lessons from Suzy Cube: The Camera System, Part 2_](https://www.gamasutra.com/blogs/LouisNicolasDozois/20170908/305311/Lessons_from_Suzy_Cube_The_Camera_System_Part_2.php)
* [_Lessons from Suzy Cube: Mobile Controls That Feel Great_](https://www.gamasutra.com/blogs/LouisNicolasDozois/20170831/304790/Lessons_from_Suzy_Cube_Mobile_Controls_That_Feel_Great.php)
* [_Lessons From Suzy Cube: Improved Mobile Performance Through a Custom Culling Solution_](https://www.gamasutra.com/blogs/LouisNicolasDozois/20170901/304941/Lessons_From_Suzy_Cube_Improved_Mobile_Performance_Through_a_Custom_Culling_Solution.php)
* [_An Interesting Journey in Creating a 2D Isometric Platformer_](https://www.gamasutra.com/blogs/SvenDuval/20170919/305894/An_Interesting_Journey_in_Creating_a_2D_Isometric_Platformer.php)
* [_One Draw Call UI_](https://www.gamasutra.com/blogs/NiklasGray/20170719/301963/One_Draw_Call_UI.php)
* [_Keyboard Focus and Event Trickling in Immediate Mode GUIs_](https://www.gamasutra.com/blogs/NiklasGray/20170926/306444/Keyboard_Focus_and_Event_Trickling_in_Immediate_Mode_GUIs.php)

* [_Tricks of the trade: Devs reveal how their games fool players_](https://www.gamasutra.com/view/news/305018/Tricks_of_the_trade_Devs_reveal_how_their_games_fool_players.php)
