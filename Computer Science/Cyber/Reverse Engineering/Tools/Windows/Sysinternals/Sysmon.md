A windows service that will log a lot of events, like process creation or file creation.
Will log as windows event logs (`evtx`).
Not every syscall like [[Process Monitor]] so can be useful to get a view on more important events, and persists on reboot.