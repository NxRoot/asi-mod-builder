# ASI-Mod-Builder for GTA V
Easy way to make ASI Mods for GTA V.

[https://youtu.be/geviDD33smE](https://youtu.be/geviDD33smE)

[![TUTORIAL VIDEO](https://img.youtube.com/vi/geviDD33smE/0.jpg)](https://youtu.be/geviDD33smE)

## How to Use

| Exe    | Description | Releases |
| -------- | ------- | ------- |
| <a href="https://github.com/NxRoot/asi-mod-builder/releases"><img style="min-width: 40px;min-height: 40px; width: 40px; padding-top: 10px;" src="https://iili.io/38rfYOb.png"/></a> | Download the latest version   | [Download](https://github.com/NxRoot/asi-mod-builder/releases)    |

## Your first mod script
`mod.cpp`
```c++

// AUTHOR: NxRoot
// CONTROLS: https://docs.fivem.net/docs/game-references/controls/
// NATIVES: https://nativedb.dotindustries.dev/gta5/natives
// TIP: Use VS Code for code auto-complete.

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

## &nbsp;
⭐ If you find this useful!
