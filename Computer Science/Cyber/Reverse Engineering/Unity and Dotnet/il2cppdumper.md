Helps reversing il2cpp unity games, will give symbols.
Use in case there's no `Assembly-CSharp.dll`, but there's `GameAssembly.dll` or `GameAssembly.so`.
The metadata file is in `Game_Data/il2cpp_data/Metadata/global-metadata.dat`.
Use it on the GameAssembly.dll (or .so) instead of the executable.

For v39 use https://github.com/roytu/Il2CppDumper/tree/v39 instead of the normal one, until it gets merged.
Try a different build if provided if it says it failed / output isn't satisfactory.

The output includes a dummy `GameAssembly.dll`, which contains only signatures (no implementations), and can be opened using ILSpy.
There's also python scripts for IDA and Ghidra symbols.
To use in IDA:
Load the `GameAssembly.dll`, and run `ida_with_struct_py3.py` with `File -> Script File`. 
Then select `script.json` and then `il2cpp.h` from the output folder. 
Can also be done with Ghidra.