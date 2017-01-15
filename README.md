# syscall-hexdump

Convert strace output to hexdump format.

```
$ strace -s9999 -f -xx -y -o serial.strace -e read,write screen /dev/ttyUSB0 115200 8N21
$ hexdump-strace serial.strace --fd /dev/ttyUSB0
                                ---=== WRITE ===---
000000  0d                                                     |.               |

                                ---=== READ ===---
000000  0d 0a 4c 6f 67 69 6e 3a  20                            |..Login:        |

                                ---=== WRITE ===---
000000  61 64 6d 69 6e 0d                                      |admin.          |

                                ---=== READ ===---
000000  0d 0a 50 61 73 73 77 6f  72 64 3a 20                   |..Password:     |
```

This tool was created for capturing bytes over a serial line *(to catch pesky 0d 0a issues, it's always line ending!)* but should be more widely useful given minor tweaks.
