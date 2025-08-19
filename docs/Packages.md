# 📦 Software Downloads

Welcome to the **official download page** for our software. Below, you'll find download links for **Linux (x64, ARM, ARM64)** and **Windows (x64)**.

---

## 🐧 Linux Downloads
| Version | Architecture | Tar File |
|------|-------------|---------|
| 1.5.1 | **x64**   | [Download](https://maicdn.micro.ai/AtomML_Plus/linux/MicroAI-MI-linux-amd64-1.5.1.tar.gz) |
| 1.5.1 | **ARM**     | [Download](https://maicdn.micro.ai/AtomML_Plus/linux_arm/MicroAI-MI-linux-arm-1.5.1.tar.gz) |
| 1.5.1 | **ARM64**   | [Download](https://maicdn.micro.ai/AtomML_Plus/linux_arm/MicroAI-MI-linux-arm64-1.5.1.tar.gz) |


> **Note:** To use the Docker image:
#### Key Considerations
- Ensure Docker is installed and running on your system before executing the commands. See [Docker docs](https://docs.docker.com/engine/install/).
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

#### For Linux (x64) Systems

```bash
docker run --name microai_mi_<latest-version> -e MAI_API_KEY=<license-key> -ti plasmacomputing/microai_mi:linux-amd64-<latest-version> 
```

#### For Linux ARM (x86) Systems

```bash
docker run --name microai_mi_<latest-version> -e MAI_API_KEY=<license-key> -ti plasmacomputing/microai_mi:linux-arm-<latest-version>  
```

#### For Linux ARM (x64) Systems

```bash
docker run  --name microai_mi_<latest-version> -e MAI_API_KEY=<license-key> -ti plasmacomputing/microai_mi:linux-arm64-<latest-version> 
```

---

## 🖥️ Windows Download
| Version | Architecture | Tar File |
|------|-------------|---------|
| 1.5.1 | **x64**   | [Download](https://maicdn.micro.ai/AtomML_Plus/windows/MicroAI-AtomML-Plus-windows-arm64-1.5.1.tar.gz) |

---

## 📖 Installation Instructions

### **Linux (Tar Files)**
Copy the following section for your operating system and architecture and update the command to match it with your details.

- Replace `<latest-version>` with the latest release version.
- Replace `<license-key>` with a valid license key retrieved from [step 3](../README.md#step-3-activate-your-license)

#### **Linux (x64)**

```bash
wget https://maicdn.micro.ai/AtomML_Plus/linux/MicroAI-MI-linux-amd64-<latest-version>.tar.gz
tar -xzf MicroAI-MI-linux-amd64-<latest-version>.tar.gz 
cd MicroAI-MI-linux-amd64-<latest-version>/bin 
chmod +x main
sudo ./main -MAI_API_KEY=<license-key>
```

#### **Linux (ARM)**

```bash
wget https://maicdn.micro.ai/AtomML_Plus/linux_arm/MicroAI-MI-linux-arm-<latest-version>.tar.gz
tar -xzf MicroAI-MI-linux-arm-<latest-version>.tar.gz 
cd MicroAI-MI-linux-arm-<latest-version>/bin 
chmod +x main
sudo ./main -MAI_API_KEY=<license-key>
```

#### **Linux (ARM64)**

```bash
wget https://maicdn.micro.ai/AtomML_Plus/linux_arm/MicroAI-MI-linux-arm64-<latest-version>.tar.gz
tar -xzf MicroAI-MI-linux-arm64-<latest-version>.tar.gz 
cd MicroAI-MI-linux-arm64-<latest-version>/bin 
chmod +x main
sudo ./main -MAI_API_KEY=<license-key>
```
---


### **Windows**
```powershell
Invoke-WebRequest https://maicdn.micro.ai/AtomML_Plus/windows/MicroAI-MI-Plus-linux-arm64-<latest-version>.tar.gz -OutFile MicroAI-MI-windows-amd64-<latest-version>.tar.gz
tar -xzf MicroAI-MI-windows-arm64-<latest-version>.tar.gz 
Set-Location MicroAI-MI-windows-arm64-<latest-version>/bin 
Start-Process -FilePath "main.exe" -ArgumentList "MAI_API_KEY=<license-key>" -Verb RunAs
```

See [Launching MicroAI Machine Intelligence](./Launch-Instructions.md) for a detailed walkthrough.