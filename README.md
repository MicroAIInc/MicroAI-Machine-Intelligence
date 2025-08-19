<p align="right">
  <img src="https://img.shields.io/badge/MicroAI_Security_&_Monitoring-2.3.0-green" alt="Static Badge">
</p>
<br />
<p align="center">
  <img src="./docs/images/microai-logo.png" alt="MicroAI Logo" width="250">
</p>

<h3 align="center">MicroAI Machine Intelligence</h3>

<p align="center">
  MicroAI Machine Intelligence is an Edge-native AI platform that embeds and trains advanced, multi-layer predictive algorithms directly on a device or machine.
</p>

<p align="center">
  This guide will help you <strong>install</strong>, <strong>configure</strong>, and <strong>validate</strong> the MicroAI Machine Intelligence agent, ensuring it operates correctly and securely. No technical expertise is required—just follow the steps carefully, and you'll have the agent up and running in no time!
</p>


## Table of Contents

- [Deployment](#deployment)
- [Validation](#validation)
- [Configurations](#configurations)
- [Features](#features)
- [Troubleshooting](#troubleshooting)
- [License](#license)
- [Contact](#contact) 

## Deployment

Follow the steps below to deploy MicroAI Machine Intelligence on your system. The deployment process varies depending on your operating system and architecture. Before proceeding, ensure you have your licensing key, which is essential for activating the agent.

Determine your Operating system and architecture [here](./docs/Detect-OS-Arch.md).

### Step 1: Download the Package

Download the latest supported release from the [packages](./docs/Packages.md) page and transfer it onto the system intended for installation. Alternatively, use the commands directly from [step 2](#step-2-extract-and-set-up-the-agent).

---
### Step 2: Extract and Set Up the Agent

Copy the following section for your operating system and architecture and update the command to match it with your details.

- Replace `<latest-version>` with the latest release version. The latest version can be found on the [packages](./docs/Packages.md) page or on the top of this page.

#### **Linux (x64)**

```bash
wget https://maicdn.micro.ai/AtomML_Plus/linux/MicroAI-MI-linux-amd64-<latest-version>.tar.gz
tar -xzf MicroAI-MI-linux-amd64-<latest-version>.tar.gz
cd MicroAI-MI-linux-amd64-<latest-version>/bin
chmod +x main
```

#### **Linux (ARM x86)**

```bash
wget https://maicdn.micro.ai/AtomML_Plus/linux_arm/MicroAI-MI-linux-arm-<latest-version>.tar.gz
tar -xzf MicroAI-MI-linux-arm-<latest-version>.tar.gz
cd MicroAI-MI-linux-arm-<latest-version>/bin
chmod +x main
```

#### **Linux (ARM x64)**

```bash
wget https://maicdn.micro.ai/AtomML_Plus/linux_arm/MicroAI-MI-linux-arm64-<latest-version>.tar.gz
tar -xzf MicroAI-MI-linux-arm64-<latest-version>.tar.gz
cd MicroAI-MI-linux-arm64-<latest-version>/bin
chmod +x main
```
#### **Windows (x64)**

```powershell
Invoke-WebRequest https://maicdn.micro.ai/AtomML_Plus/windows/MicroAI-MI-linux-arm64-<latest-version>.tar.gz -OutFile MicroAI-MI-windows-amd64-<latest-version>.tar.gz
```
---
### Step 3: Activate your License

Activate your license and retrieve your license key on <a href="https://launchpad.micro.ai/activate/mitrial" target="_blank">MicroAI Launchpad</a>. See [activation walkthrough](./docs/Registration-Instructions.md) for guided steps.

---


### Step 4: Run the Agent

Replace `<license-key>` with a valid license key retrieved from [step 3](#step-3-activate-your-license). See [configurations](./docs/Configurations.md#default-configurations) to find the default configurations the agent is set up with.

#### **Run Standalone**

```bash
sudo ./main -MAI_API_KEY=<license-key>
```

---
#### **Windows (x64)**

Double-click the `.exe` file and follow the installation steps. See [Launching MicroAI Machine Intelligence](docs/Launch-Instructions.md) for a detailed walkthrough.
___
#### **Docker**

Docker provides an efficient way to run MicroAI in a containerized environment. If you prefer deploying the agent as a Docker container, use the following commands, selecting the appropriate version based on your system architecture.

#### Key Considerations
- Ensure Docker is installed and running on your system before executing the commands.
- Replace `<license-key>` with the actual MicroAI License key for authentication.
- The image tag `<latest-version>` corresponds to the MicroAI agent version; update it as needed for newer versions.
- If you need to update the configuration file, you can mount the config directory using the `-v` option and add this to the commands below:  
  ```bash
  -v <absolute_path_to_config_directory_on_host_machine>:/home/MI/config
  ```
- Similarly, to access logs from the host machine, mount the log directory as follows:  
  ```bash
  -v <absolute_path_to_log_directory_on_host_machine>:/home/MI/data/logs
  ```

#### For Linux x64 Systems

```bash
docker run --name microai_MI_<latest-version> -e MAI_API_KEY=<license-key> -ti plasmacomputing/microai_MI:linux-amd64-<latest-version>
```

#### For Linux ARM (x86) Systems

```bash
docker run --name microai_MI_<latest-version> -e MAI_API_KEY=<license-key> -ti plasmacomputing/microai_MI:linux-arm-<latest-version>-rc1
```

#### For Linux ARM (x64) Systems

```bash
docker run --name microai_MI_<latest-version> -e MAI_API_KEY=<license-key> -ti plasmacomputing/microai_MI:linux-arm64-<latest-version>-rc1
```
See [Launching MicroAI Machine Intelligence](docs/Launch-Instructions.md) for a detailed walkthrough.

## Validation

After installation, use the following steps to ensure the agent is running correctly:

1. **Check if the process is running**:
   ```bash
   ps aux | grep main
   ```
2. **Verify logs for errors**:
   ```bash
   cat <installation-path>/data/logs/microai-main.log
   ```
3. **Confirm API key authentication and start of agent**:
   ```bash
   cat <installation-path>/data/logs/microai-main.log

   [*] MicroAI AtomML+ v1.5.1 - Release <os> <arch>
   [-] MicroAI Starting
   [-] Training Mode set
   [-] Profile API: ***
   [-] Device activation completed on <datetime of activation>
   [-] Training complete!
   [-] starting subprocess 0
   [-] starting subprocess 1
   [-] starting subprocess 2
   [-] starting subprocess 3
   [-] Everything started
   ```

If all checks pass, the agent is successfully installed and operational!


## Configurations

To customize your agent settings, refer to the [Configurations Guide](docs/Configurations.md).  This will allow you to change things such as Engine Sensitivity, Channel Update Rates, and Alert and notfication settings


If you wish to view your profile, devices or update your plan, follow this [guide](./docs/Update-Profile.md).

## Features

Take a peek at our [feature page](docs/Feature-List.md) for current features available with our agent.

## Troubleshooting

If you encounter issues, try these solutions:

### Issue: "Permission Denied" on Running `./main`

- Solution:
  ```bash
  chmod +x main
  sudo ./main -MAI_API_KEY=<license-key>
  ```

### Issue: API Key Authentication Fails

- Solution:
  1. Verify your License key
  2. Ensure you have an active internet connection
  3. Check logs:
     ```bash
     <installation-path>/data/logs/microai-main.log
     ```

For further assistance, contact [**support@micro.ai**](mailto\:support@micro.ai).

---

## License

See [Software Licensing Agreement](License.txt) for more details.

---

## Contact

- **Company:** MicroAI™
- **Website:** [https://machineintelligence.micro.ai](https://machineintelligence.micro.ai)
- **Email:** [support@micro.ai](mailto\:support@micro.ai)

