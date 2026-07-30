PE Header can contain some useful data:
- `IMAGE_NT_HEADER -> IMAGE_FILE_HEADER -> TimeDateStamp` - Compile timestamp. May not be fully accurate, like Delphi programs always show June 19, 1992, and it can be easily modified.
- `IMAGE_OPTIONAL_HEADER -> Subsystem` - whether it's a console or GUI program (`IMAGE_SUBSYSTEM_WINDOWS_CUI` - console, `IMAGE_SUBSYSTEM_WINDOWS_GUI` - GUI)
- 