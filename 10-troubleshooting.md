## Troubleshooting with journalctl and dmesg

During the troubleshooting phase, I encountered several common issues:

### Permission Errors
Most of the errors I faced were related to **permissions**.  
- Some files or services required specific ownership or execution rights.  
- I solved these by adjusting permissions (`chmod`) or changing file ownership (`chown`) so the processes could run correctly.  
- In other cases, missing paths caused failures in dependent functions. Once I created the files or directories in the proper location, the errors disappeared.

### Kernel Terminating a Service
One particular service was repeatedly being killed by the kernel (OOM‑killer).  
- The process consumed too many resources and was terminated automatically.  
- After several attempts to stabilize it, I decided to stop and disable the service permanently to prevent further interruptions.  

### Resolution Summary
All issues were resolved easily by:
- Granting the necessary permissions to files and services.  
- Correcting ownership where required.  
- Creating missing paths in the proper directories.  
- Disabling the problematic service that the kernel kept killing.  

As a result, the system remained stable and no further errors appeared.
