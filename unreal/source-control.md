# Source Control
[Wiki](../index.md)/[Unreal](unreal.md)/Source Control

## Editor Integration
Unreal has a neat editor integration that lets you automatically check out assets and commit/submit/check them in again once you've finished working on them.
I've only really seen it work with SVN and Perforce - the git integration seems to be a semi-functional beta only.

[_Unreal Documentation_](https://docs.unrealengine.com/latest/INT/Engine/Basics/SourceControl/InEditor/)

## Ignore files
There are many files in an Unreal project that you don't want to check into source control, because they can easily be regenerated on the fly.
The only exception are built DLLs that are required for artists/level designers to open the project without rebuilding from source.

{% highlight sh %}
# Visual Studio user specific files
.vs/

# Visual Studio database file
*.VC.db
*.VC.VC.opendb

# Project files in the root
*.sln
*.suo
*.opensdf
*.sdf
/*.xcodeproj
/Makefile
/CMakeLists.txt
/.ue4dependencies
*.upack

# Compiled source files for the engine to use
Intermediate/

# Config files and logs
Saved/

# Assets in engine/target platform formats (source stored in .uasset files)
DerivedDataCache/

/Build/**/FileOpenOrder/**

# Executable files or other files created during compiling 
/Binaries/**/*.pdb
/Binaries/**/*.target
/Binaries/**/*.exe
/Binaries/**/*.lib
/Binaries/**/*.exp
/Binaries/**/*-DebugGame.*

# Plugin executable files or other files created during compiling 
/Plugins/**/Binaries/**/*.pdb
/Plugins/**/Binaries/**/*.target
/Plugins/**/Binaries/**/*.exe
/Plugins/**/Binaries/**/*.lib
/Plugins/**/Binaries/**/*.exp
/Plugins/**/Binaries/**/*-DebugGame.*
{% endhighlight %}

You could also add ```*.dll``` to the ignores and unignore the specific dlls you want to track.
This might be useful, because building while the Editor is still opened creates a new dll with a new integer suffix that isn't covered by the ignores above. However you have to modify this ignore list for every single game.
