|Command | Description | Example |
| -----------| ------------|----------|
| .hh | opens the help window | |
|.reload /f | force reload of symbols| |
| g          | continue running the program | |
| u         | unassemble from memory | u kernel32!GetCurrentThread |
| db | display bytes | db esp, db 00faf974, db kernel32!WriteFile |
| dw | display size WORDs (two bytes) | dw esp |
| dd | display size DWORDs (four bytes) | dd esp |
| dq | display size QDWORDs (eight bytes) | dq esp |
| dW or dc | display ASCII characters of size WORD and DWORD | dW KERNELBASE, dW kernelbase+0x40 |
| L | change length of bytes to display (default is 0x80) | dd esp L4, dd esp L10 |
| da or du | display memory content as either ASCII or Unicode | |
| poi | displays data referenced from a memory address | dd poi(esp) |
| dt | displays structures from memory. Use *-r* for recursion. You can also specify a field name | dt ntdll!\_TEB, dt -r ntdll!\_TEB, dt -r ntdll!\_TEB ThreadLocalStoragePointer |
| sizeof() | display the size of a structure | ?? sizeof(ntdll!\_TEB) |
| ed | edit process memory data of size DWORD | ed esp 41414141 |
| ea | edit process memory data with ASCII characters | ea esp "Hello" |
| s | search memory space for specified bytes. Requires the type to search for, the starting point in memory, the length of memory and the pattern to search | s -d 0 L?80000000 41414141 |
| r | list and/or modify registers | r , r ecx, r ecx=41414141
| bp | set a breakpoint on a symbol or address | bp kernel32!WriteFile |
| bl | list breakpoints | |
| bd \/ be \/ bc | disable, enable and clear breakpoints | bd 0, be 0, bc 0|
| bu | set a breakpoint on an unresolved function | bu ole32!WriteStringStream |
| | breakpoint based actions | bp kernel32!WriteFile ".printf \"The number of bytes written is: %p\", poi(esp + 0xC);.echo;g" |
| | conditional break point actions | bp kernel32!WriteFile ".if (poi(esp + 0x0C) != 4) {gc} .else {.printf \"The number of bytes written is 4\";.echo;}"
| lm | list modules | lm, lm m kernel32 (accepts wildcards) |
| x | examine a module | x kernelbase!CreateProc* | 
| ? | evaluate expression command used for calculations | ? 77269bc0 - 77231430, ? 0n41414141, ? 0y1110100110111 |
| .formats | converts between different formats at once including the ASCII representation of the values | .formats 41414141 |
| !vprot | checks for memory protections | |



