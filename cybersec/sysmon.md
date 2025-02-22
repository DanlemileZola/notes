# Introduction

## What is sysmon ? 

It's an enhanced logging software meant to integrate system informations/events into a SIEMs in a more efficient way than traditional syslogs. 
Sysmon works with kernel-level event sources, allowing to captures events as they happen, where traditional CLI tools (ps, netstat, etc) query their informations from logs files. 
Working on a lower level offers :

- More granularity on what its logged :
    When a process is create, it can logs the command-line arguments used, parent processes, hashes and user details. 
    Network connections can be link to the command which initialize them.
    Monitors modification on files with more ease, more details and alongside other events. 
- Structured and consistent logging :
    Use XML format which make it easier to analyze and integrate into SIEMs, where standard logs use plain text scattered across different files. 
- More protection against attackers evasion : 
    Sysmon operates independently and can send logs directly to a remote SIEM, where native system logs are more easily by-passed by attackers (by disabling or deleting them).

## How does it work ? 

It relies on [eBPF](https://ebpf.io/) which is a technology that run programs in sandboxed allow programs to execute code in a kernel space, adding additional capabilities to the softwares whilst reducing the inherent risks of running at such a low level.  
From the perspective of sysmon, it allow to monitor the system by creating 
rules more difficult to set with user space applications. 

crosoft/SysmonForLinux/tree/main)rnel by running : 
```bash
ls /sys/kernel/btf/vmlinux
``` 

Which confirmed the file were 