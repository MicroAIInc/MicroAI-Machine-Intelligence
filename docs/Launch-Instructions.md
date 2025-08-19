# Installation Walkthrough for Linux and Windows

In this section, we will walk through the installation process for a Linux environment and Windows environment.

## Launching MicroAI
Depending on your host hardware configuration, you may require advanced privleges to run Machine Intelligence.  The commands for linux and windows are listed below

#### Linux
```
sudo
```
#### Windows
```
runas /user:Administrator
```
The following screenshots illustrate an example of running MicroAI on Linux.

In the first screenshot, the agent is initialized and the device is activated, displaying the confirmation message: **"Device is activated successfully."** Once activated, the agent enters Training Mode, where the AI engine begins learning from the environment. A progress bar indicates the training status.  

<img src="../docs/images/Linux-Launch-Train.png" alt="Linux Initialization" width="600">

In the second screenshot, the training reaches 100%, and the agent automatically switches to Execute Mode, as confirmed by the message: **"Training complete! Execute Mode set. Everything started."** At this stage, the agent is fully operational and ready for machine intelligence tasks.  

<img src="../docs/images/Linux-Launch-Complete.png" alt="Linux Training Complete" width="600">

If the License key is invalid, the following error will be returned.  

<img src="../docs/images/Linux-Launch-Incorrect-License.png" alt="Invalid API Key Error" width="600">

If the device is registered under a different profile on Launchpad, the following error will occur. Please ensure that you are using the License key associated with the original account.  

<img src="../docs/images/Linux-Launch-Already-Registered.png" alt="Different Profile Error" width="600">


