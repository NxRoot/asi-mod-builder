# ASI-Mod-Builder for GTA V
Easy way to make ASI Mods for GTA V using [Script Hook V](http://www.dev-c.com/gtav/scripthookv/).

## Tutorial
[https://youtu.be/geviDD33smE](https://youtu.be/geviDD33smE)

[![TUTORIAL VIDEO](https://img.youtube.com/vi/geviDD33smE/0.jpg)](https://youtu.be/geviDD33smE)

## Features
* Automated ASI Builder
* Example Script Template
* No external dependencies

&nbsp;

## How to Use

| Exe    | Description | Releases |
| -------- | ------- | ------- |
| <a href="https://github.com/NxRoot/asi-mod-builder/releases"><img style="min-width: 40px;min-height: 40px; width: 40px; padding-top: 10px;" src="https://iili.io/38rfYOb.png"/></a> | Download the latest version   | [Download](https://github.com/NxRoot/asi-mod-builder/releases)    |

&nbsp;

## Your first mod script
`mod.cpp`
```cpp

#include "mod.h"

void Notify(char* msg) {
    UI::_SET_NOTIFICATION_TEXT_ENTRY("STRING");
    UI::_ADD_TEXT_COMPONENT_STRING(msg);
    UI::_DRAW_NOTIFICATION(false, false);
    AUDIO::PLAY_SOUND_FRONTEND(-1, "PICK_UP", "HUD_FRONTEND_DEFAULT_SOUNDSET", false);
}

void ScriptLoop(){
    if (CONTROLS::IS_CONTROL_JUST_PRESSED(0, ControlJump)) {
        Notify("~g~Message: \n~w~You pressed JUMP key...");
    }
}

void ScriptMain() {

    WAIT(500); // Delay to ensure game is ready
    Notify("~g~MOD LOADED: \n~w~Your mod was loaded!");
    
    while (true) {
        ScriptLoop();
        WAIT(0); // Yield to game loop
    }
}
```

&nbsp;

## How to Read INI Files
`mod.ini`
```.ini
[Settings]
yourNumber=369
yourString=futo
```

`mod.cpp`
```cpp
// Float values
int yourNumber = GetPrivateProfileIntA("Settings", "yourNumber", 369, "./mod.ini");

// String Values
char yourString[256];
GetPrivateProfileStringA("Settings", "yourString", "futo", yourString, sizeof(yourString), "./mod.ini");
```

&nbsp;

## Build specific folder

> By default we build the **mod** folder, but you can also drag folders to the executable or use it via terminal.

```
asi.exe .\\nitro
```
Output: `nitro.asi`

&nbsp;

## More Information

### Need to Know

<details>
<summary>What is ASI?</summary>

&nbsp;
> ASI is just a `renamed DLL` that is recognizable by **Script Hook V**.

&nbsp;

</details>

<details>
<summary>What is Script Hook V?</summary>
    
&nbsp;
> SHV is a `C++ Library` that contains **GTA** native methods.

&nbsp;

</details>

<details>
<summary>How does Script Hook V work?</summary>
    
&nbsp;
> SHV works as a `DLL injector` that loads **ASI or DLL** mods inside the game folder.

&nbsp;

</details>

<details>
<summary>How can we create new mods?</summary>
    
&nbsp;
> Mods are writen in `C++` and then **compiled** into a DLL or ASI file.

&nbsp;

</details>

<details>
<summary>Why do we need to compile mods?</summary>
    
&nbsp;
> Mods depend on `ScriptHookV.lib`, that means we **must** include it when compiling new code.

&nbsp;

</details>

### Frequently Asked Questions

<details>
<summary>Do we need to install Visual Studio?</summary>
    
&nbsp;
> No, Visual Studio is ***not*** required.

&nbsp;

</details>

<details>
<summary>Do we need to install MS Build Tools?</summary>
    
&nbsp;
> No, MS Build Tools is ***not*** required.

&nbsp;

</details>

    

## &nbsp;
⭐ If you find this useful!
