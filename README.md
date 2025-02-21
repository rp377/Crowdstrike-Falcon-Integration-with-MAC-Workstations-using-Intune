## Prerequisites:

### System Requirements
Installing the Falcon sensor for Mac requires administrator privileges, also known as elevated privileges.

### Supported Operating Systems
The Falcon sensor for Mac is currently supported on these macOS versions:

| macOS Version       | Minimum Sensor Version    | Falcon End-of-Support Date |
|---------------------|-------------------------|----------------------------|
| macOS Sequoia 15   | All supported sensor versions <br> Intel CPUs and Apple silicon native support included | December 31, 2027 |
| macOS Sonoma 14    | All supported sensor versions <br> Intel CPUs and Apple silicon native support included | December 31, 2026 |
| macOS Ventura 13   | All supported sensor versions <br> Intel CPUs and Apple silicon native support included | December 31, 2025 |

> **Note:** Falcon does not support hosts running in containers, such as Docker.

### Host authorizations
Apple requires system extensions to be approved before they can be loaded. The Falcon sensor for Mac requires these additional authorizations on each host:

- Full Disk Access (FDA) to Falcon

| **Important** | If Full Disk Access is not enabled, the sensor enters reduced functionality mode (RFM). See [Reduced functionality mode: Mac hosts](</documentation/page/e261a9b7/falcon-sensor-for-mac-deployment#pb0ee694>). |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------|


- Falcon system extension
  - Falcon non-removable system extension (macOS Sequoia 15 and later)
- Falcon network filter extension

If you use profiles provided by CrowdStrike, these authorizations are already configured for you. Apple doesn't allow profiles to be deployed outside of an MDM
solution. We strongly recommend you use an MDM solution to distribute the profile to your endpoints prior to the deployment process. These authorizations are
only required once. Subsequent upgrades using the built-in upgrade functionality of the sensor will not require additional confirmation approvals on the host.

### Crowdstrike has created 2 profiles based on OS Versions

- [Profile for Sonoma and earlier OS versions](<https://github.com/rp377/Crowdstrike-Falcon-Integration-with-MAC-Workstations/blob/main/Falcon%20Profile%20-%20no%20Kext.mobileconfig>)
- [Profile for Sequoia and later OS versions](<https://github.com/rp377/Crowdstrike-Falcon-Integration-with-MAC-Workstations/blob/main/Falcon%20Profile%20OS%20v15.mobileconfig>)

The profile provided by CrowdStrike for Sonoma and earlier OS versions worked as per our expections. However, the one for Sequoia did not work correctly. We have fixed that for you!!!
You can refer the above-attached profiles only to meet your requirements.

### Installing the Falcon sensor for Mac

There are diﬀerent methods to successfully install the sensor:

- Recommended installation method: Use an MDM solution to distribute the profile we provide to your endpoints prior to the deployment process. This
streamlines the deployment and avoids manual authorization steps on hosts.
- Alternate installation methods:
  - Use the standalone installer which streamlines your authorization and post-verification steps.

| **Note** | If you don’t use an MDM to distribute the profile we provide, multiple authentication confirmations from the OS occur on the host and must manually be approved. |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------|

### Recommended installation method: Using an MDM to sync profiles

1. Use an MDM to deploy the correct profile to the hosts. This step can be performed any time prior to sensor deployment. You can utilize the profiles mentioned above.
2. Use the Google Chrome browser to download the sensor installer
3. Copy your customer ID checksum (CCID) from Host setup and management > Deploy > Sensor downloads.
4. Run the sensor installer on your device using one of these two methods:
  - Double-click the .pkg file.
  - Run this command at a terminal, replacing <installer_filename> with the path and file name of your installer package:
    ```sh
    sudo installer -verboseR -package <installer_filename> -target /
    ```
5. When prompted, enter administrative credentials for the installer.
6. Run falconctl, installed with the Falcon sensor, to provide your customer ID checksum (CCID). This command is slightly diﬀerent if you're installing with installation tokens. In this example, replace 0123456789ABCDEFGHIJKLMNOPQRSTUV-WX with your CID.
  ```sh
  sudo /Applications/Falcon.app/Contents/Resources/falconctl license 0123456789ABCDEFGHIJKLMNOPQRSTUV-WX
  ```



