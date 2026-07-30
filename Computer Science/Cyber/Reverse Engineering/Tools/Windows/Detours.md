Tutorial: https://github.com/SpartanX1/microsoft-detours-example
Binary instrumentation for windows api functions.
[[Frida]] is usually a better alternative.
## Usage
Make a VS cpp project.
### Configuring Project
In Project -> Properties -> C/C++ -> General -> Additional include directories: add the detours include subdirectory.
In Project -> Properties -> Linker -> General -> Additional library directories: add the detours lib.X64 subdirectory.
In Project -> Properties -> Linker -> Input -> Additional dependencies: add in the end ;detours.lib
In Project -> Properties -> General -> Configuration Type: set to dll.
### Source Code
```cpp
#include <windows.h>
#include <detours.h>
#include <iostream>

static VOID(WINAPI* TrueSleep)(DWORD dwMilliseconds) = Sleep;

VOID WINAPI TimedSleep(DWORD dwMilliseconds)
{
    std::cout << "Hooked\n";
}

__declspec(dllexport) BOOL WINAPI DllMain(HINSTANCE hinst, DWORD dwReason, LPVOID reserved)
{
    if (DetourIsHelperProcess()) {
        return TRUE;
    }

    if (dwReason == DLL_PROCESS_ATTACH) {
        DetourRestoreAfterWith();
        DetourTransactionBegin();
        DetourUpdateThread(GetCurrentThread());
        DetourAttach(&(PVOID&)TrueSleep, TimedSleep);
        DetourTransactionCommit();
    }
    else if (dwReason == DLL_PROCESS_DETACH) {
        DetourTransactionBegin();
        DetourUpdateThread(GetCurrentThread());
        DetourDetach(&(PVOID&)TrueSleep, TimedSleep);
        DetourTransactionCommit();
    }
    return TRUE;
}
```
### Injecting the dll
Build the project.
The dll will be saved in solution folder in `x64/Debug/name.dll`
To inject: `withdll -d <dll> <exe>` in cmd.