# System debugging
- To know current cpu/disk status, the classic tools are `top` (or the better `htop`), `iostat`, and `iotop`. Use iostat `-mxz 15` for basic CPU and detailed per-partition disk stats and performance insight.  
- Press `Shift+O` to Sort field via field letter, for example press ‘a‘ letter to sort process with PID (Process ID).
- Display Specific User Process: `top -u tecmint`
- Highlight Running Process in Top: press `z`
- Shows Absolute Path of Processes: press `c`
- Save Top Command Results: Press `Shift+W` to save the running top command results under /root/.toprc.
- Getting Top Command Help: `h`

# Search
- search recursively (in all sub directories also) for all .cc OR .h files that contain "hello": `grep -nr --color "hello" .`