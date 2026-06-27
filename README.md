# Steam Download Optimizer

A PowerShell script that temporarily sets Steam's CPU priority to `High` during game downloads and automatically reverts it to `Normal` when the download finishes.

## Why use it ?
Steam downloads are heavily compressed. In many cases, your download speed is bottlenecked by your CPU's ability to decompress the files, rather than your actual network speed. By raising the process priority, Windows allocates more CPU time to Steam, which can speed up the download and installation process.

*Note: The actual improvement in download speed will depend heavily on your specific hardware configuration (CPU, SSD speed) and your network bandwidth.*

## How it Works
The script does not rely on checking folders or reading log files. Instead, it measures Steam's real-time I/O (Input/Output) traffic. 
- If Steam is actively processing data (Network + Disk), the script keeps the priority at `High`.
- If the I/O drops (meaning the download is finished, paused, or cancelled), the script restores the priority to `Normal` and exits.

## How to use
1. Download the script file (`steam-download-optimizer.ps1`).
2. Make sure Steam is running.
3. Right-click the `.ps1` script and select **Run with PowerShell**.
4. Accept the Administrator prompt (this is required by Windows to change process priorities).
5. Leave the console window open. It will automatically monitor the process and close itself when the job is done.
