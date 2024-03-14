## a guide to the platonic operating system

```
@/
└── @fs1/
    ├── system/
    │   ├── boot/
    │   ├── config/
    │   ├── kernel/
    │   ├── process/
    │   ├── program/
    │   │   ├── core*
    │   │   ├── library/
    │   │   └── share/
    │   └── variable/
    └── user/
        └── william/
            ├── configs/
            ├── program/
            └── desktop/
                ├── docs/
                ├── downloads/
                ├── pics/
                └── vids/
```

every device plugged into the computer is listed inside '@', and ordered numerically, like '@fs1', '@fs2' and so on

we can interpret '@fs1' as just @, relative to our local filesystem, so the system directory can be called as @system

### @system

the files used by the system are in @system, containing

- **boot**, used for the boot process
- **config**, used to configure programs
- **kernel**, used to communicate with the kernel
- **process**, used for processes
- **program**, used for programs
- **variable**, used for various files used by programs that can change over time - this is the most flexible directory in the entire @system directory

then, we have the subdirectories like *library* and *share* inside **program**, this are for what the name says: libraries and shared resources - the other directories shall not be overloaded with other subdirectories, except **variable**

### @user

the user directory lists all the directories created for the users - it shall have a directory with the name of the user, and inside it, this structure:

- **configs**, for his personal configuration for his programs that are not shared across the system
- **program**, for his local programs that, again, are not shared across the system

and finally

- **desktop**, which hosts all files that the user wants to store whatsoever - this may be separated into another partition for security reasons, as well as the others or the main user directory **william**

### examples

**Q:** where are the icons for a program stored?  
**A:** in @system/program/share/

**Q:** where are the build files for the package manager   stored?  
**A:** in @system/variable/

**Q:** where are logs from the display server stored?  
**A:** in @system/variable/

**Q:** if i want to install a program, but i don't have the admninistrator permissions to do so, how should i proceed?   
**A:** download a program, build it, or if it comes built, store the binary in @system/user/yourname/program/ and execute it if you want - the 'program' directory is in the environment directories, like @system/program/
