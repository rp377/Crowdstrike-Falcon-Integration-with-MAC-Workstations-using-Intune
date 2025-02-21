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

- Profile for Sonoma and earlier OS versions (<>)
- Profile for Sequoia and later OS versions (<>)

The profile provided by CrowdStrike for Sonoma and earlier OS versions worked as per our expections. However, the one for Sequoia did not work correctly. We have fixed that for you!!!



