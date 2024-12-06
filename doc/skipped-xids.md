# NVIDIA GPU XID Errors and Troubleshooting Suggestions

This document lists a subset of NVIDIA GPU XID errors categorized as **application errors**. These errors typically indicate issues occurring at the application level while the GPU hardware remains healthy. For more details about XID errors, please refer to the [NVIDIA XID Error Documentation](http://docs.nvidia.com/deploy/xid-errors/index.html#topic_4).

When encountering the following XID errors, follow these steps to troubleshoot:

1. **Resubmit the workload** and observe whether the XID error disappears.  
2. If the error persists, **inspect your code or analyze logs** to determine if the XID error is caused by user code.  
3. If no issues are found in the code, **contact your platform's technical support team** for assistance.

## XID Error Descriptions and Potential Causes

| **XID** | **Description**                                                                                   |
|---------|---------------------------------------------------------------------------------------------------|
| 13      | **Graphics Engine Exception**. Typically caused by array out-of-bounds access or instruction errors. Hardware issues are rare. |
| 31      | **GPU memory page fault**. Usually caused by illegal memory access in the application. Hardware or driver issues are very unlikely. |
| 43      | **GPU stopped processing**. Most often caused by application-level errors, not hardware problems.  |
| 45      | **Preemptive cleanup, due to previous errors**. Commonly occurs when running multiple CUDA applications and encountering a DBE (device fault). Typically caused by manual application exit or other issues (e.g., hardware failure or resource limitations). Logs should be analyzed to identify the root cause. |
| 68      | **NVDEC0 Exception**. Usually indicates hardware or driver-related problems.                       |

## Notes

- In most cases, these XID errors are caused by user code or the application runtime environment rather than GPU hardware itself.  
- When diagnosing issues, it is recommended to prioritize reviewing application logic and log information.  
- If the problem persists and cannot be identified, seek professional support for further troubleshooting.
