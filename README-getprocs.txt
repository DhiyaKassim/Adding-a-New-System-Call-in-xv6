getprocs System Call
Added int getprocs(void) to xv6-riscv using syscall number 23. Number 22 was already assigned to sync.
Files modified:
kernel/syscall.h: defines SYS_getprocs.
kernel/syscall.c: declares and registers sys_getprocs.
kernel/defs.h: declares the kernel helper.
kernel/proc.c: counts only RUNNABLE or RUNNING processes, acquiring each process lock while checking its state.
kernel/sysproc.c: implements the syscall wrapper.
user/user.h: declares the user interface.
user/usys.pl: generates the syscall stub.
user/getprocs.c: tests the syscall.
Makefile: includes the getprocs program in UPROGS.
Testing:
Built and booted xv6 using make qemu. Running the test produced:
$ getprocs
Processes running: 1
 counts only RUNNABLE or RUNNING processes.The original version returned 3.
 After the extra-credit modification, it returned 1 because init and the shell were sleeping.
