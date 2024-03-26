## NAME: RAMKUMAR G
## REG NO:212223220084

# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids


	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }

```


##OUTPUT

![315942124-252193ae-b9d6-40ce-b6d8-70ed10ed9d0d](https://github.com/RamkumarGunasekaran/Linux-Process-API-fork-wait-exec/assets/144870820/e37b1a01-9f81-4fc6-8f12-49a38bfcc232)













## C Program to create new process using Linux API system calls fork() and exit()
```
#include <stdlib.h>
#include <sys/wait.h>
#include<stdio.h>
#include<unistd.h>
#include <sys/types.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}

```




##OUTPUT



![315942077-965646a8-09cb-4b6b-a403-fbb9fc00bb7b](https://github.com/RamkumarGunasekaran/Linux-Process-API-fork-wait-exec/assets/144870820/c399d709-a95e-4516-b2fd-97b085f9117c)





## C Program to execute Linux system commands using Linux API system calls exec() family

```
#include <stdlib.h>
#include <sys/wait.h>
#include<stdio.h>
#include<unistd.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}

```


##OUTPUT



![315941982-8462a79b-d076-48fc-8f8f-4ae94ee31829](https://github.com/RamkumarGunasekaran/Linux-Process-API-fork-wait-exec/assets/144870820/deb0a646-ce79-437a-aed0-a929c2bda7a4)















# RESULT:
The programs are executed successfully.
