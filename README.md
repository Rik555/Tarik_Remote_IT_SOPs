# Tarik_Remote_IT_SOPs
Standard Operating Procedures (SOPs) for Tier 1 Remote Support, showcasing CompTIA Security+ principles applied to CLI troubleshooting and ticket resolution workflows.
01_CLI_Troubleshooting_Guide.md
CLI Troubleshooting: Standard Operating Procedure (SOP)

This document outlines the systematic use of the Windows Command Line Interface (CLI) for diagnosing and resolving common Tier 1 connectivity and system issues. This process is designed for remote support environments.

Scenario 1: User Reports "No Internet Access"

Goal: Quickly isolate the problem (Local PC, Local Network, or ISP).

Command
ipconfig /all

Purpose
Verify the PC has a valid IP address, Subnet Mask, and Default Gateway.

Expected Secure Result
The IP address must be within the network's known range (e.g., 192.168.1.x) and DNS server addresses must be present and correctly configured.

ping 8.8.8.8

Test external connectivity to a known, reliable DNS server.

Should show 4 successful replies. If this fails, the issue is beyond the local network (e.g., router or ISP failure).

tracert 8.8.8.8

Trace the path of the connection hop-by-hop.

If the traceroute fails early (after the first few hops), it points to a local gateway or router failure that requires local intervention.

Scenario 2: System Sluggishness / Unexpected Activity (Security Focus)

Goal: Identify resource-intensive or unauthorized processes utilizing Security+ knowledge.

Command
tasklist

Purpose
Lists all running processes and their memory usage.

Security Implication
Used to quickly identify any unknown or unusually large processes consuming resources, which may indicate unauthorized software or malware.

netstat -ano

Lists all active network connections and the corresponding Process ID (PID).

This is a crucial security tool (Sec+ concept). If an unfamiliar PID is communicating with a foreign IP address, it indicates potential malware or data exfiltration that needs immediate termination via taskkill.

sfc /scannow

System File Checker.

Used to verify the integrity of all protected system files and repair corrupted files—a core maintenance and troubleshooting step for system stability and integrity.
