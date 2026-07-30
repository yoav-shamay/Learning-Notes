Can be useful to run analysis on one specific partition, like `strings`.
This can be done easily using the [[dd Command|dd]] command:
`dd if=<disk file> of=<output file> skip=<offset> count=<partition length> [bs=<block size>]`
Use `bs=512` when taking sleuthkit outputs, drop when using in bytes.