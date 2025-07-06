# Nessus SOP

**Nessus Installation and Configuration:** **(WINDOWS)**

1. Download and Install Nessus from the official website.
2. Run Task Manager as Administrator -> More Details -> Services -> Stop Tenable Nessus.
3. Run Command Prompt as Administrator -> cd \Program Files\Tenable\Nessus
    1. For Help -> nessuscli.exe --help
4. Activate Nessus License -> nessuscli.exe fetch --register (Activation Code)
5. Once all plugins are installed, run the following commands:
    1. exe adduser CLA
    2. exe password omijb007
6. Run Task Manager as Administrator -> More Details -> Services -> Start Tenable Nessus.
7. On Browser, go to [https://127.0.0.1:8834](https://127.0.0.1:8834/)

**Nessus Installation and Configuration:** **(LINUX)**

1. Download and Install Nessus from official website.
2. Go to Terminal -> cd /Downloads
3. To Install, run-> sudo dpkg -i Nessus*.deb
    1. If proxy required, run -> sudo /opt/nessus/sbin/nessuscli fix --secure --set proxy = IP Address
    2. If port required, run -> sudo /opt/nessus/sbin/nessuscli fix --secure --set port = Port Number
4. To set up Nessus, run -> sudo /opt/nessus/sbin/nessuscli (Activation Code)
5. Once all plugins are installed, run the following commands:
    1. nessuscli adduser CLA
    2. nessuscli password omijb007
6. On Browser, go to [https://127.0.0.1:8834](https://127.0.0.1:8834/)

**Set Up Nessus:** (This will be the **main file**)

Before performing any scanning Select the ‘Main’ Scan -> More -> Copy to My Scans. Just change the IP address with the given one.

1. Login on Nessus using username and password as above. Let the plugins get installed.
2. Once done, go to New Scan -> Select Advanced Scan. Following are the configurations:
    1. **Basic -> General**:
        1. Name: Main
        2. Target: 10.10.10.1
    2. **Discovery -> Host Discovery:**
        1. Ping the Remote Host (Off)

**Discovery -> Port Scanning:**

1. Consider Unscanned Ports as Closed (Select)
    1. Port Scan Range: 0-65535
- Verify open TCP ports found by local port enumerators (Select)
1. **Assessment -> Windows:**
    1. Request information about SMB Domain (Select)
    2. RID Brute Forcing (On)

**Assessment -> Malware:**

1. Scan for malware (On)
    1. **Report:**
        1. Designate hosts by their DNS name (Select)
        2. Display hosts that respond to ping (Select)
- Display unreachable hosts (Select)
1. **Plugins**:
    1. Denial of Service (Disable)

Rest all should be kept as it is.

If there’s Internal Scanning mentioned, and credentials are given put them while configuring in the Credentials tab.

For Windows -> Put Username & Password.

For Linux -> Select SSH -> Authentication Method: Password -> Put Username and Password -> Elevate Privileges with su or sudo(ask the client)

For External Scanning, no need to put anything in the credentials tab.

**To Download Nessus Reports:**

1. Go to the specific Nessus scan -> Export -> Download the Nessus file.
2. Then go to Report and Select CSV and Generate Report.

Make Folders for each project and save both the files there.
