# Features

Please review our [plans](./Plans.md) page to view different plan options.

### Deployment and Configurable Features

- **Self-registration:** The agent automatically registers itself on the Launchpad for seamless data tracking and centralized management.
- **System Metadata Retrieval:** Captures system metadata like hostname, OS version, and other details for an overview of the system’s environment.
- **Secure Embedded Configuration:** Internal configurations are securely embedded into the agent binaries to prevent unauthorized access.
- **MQTT Data Transmission:** Securely transfers data using the MQTT protocol with built-in authentication.
- **Cross-Platform Installers:** Windows/Linux installers with all dependencies for quick deployment.
- **Containerized Deployment:** Supports automatic deployment via Kubernetes and ECS for scalability.
- **Geolocation Support:** Retrieves latitude and longitude from the agent’s configuration for localization.
- **Email Notifications:** Sends email notifications based on event severity.
- **External Data Exporter:** Exports collected data to third-party visualization tools.

## Monitoring Features

- **Health Score Tuning:** Customizable health score matrix for performance tracking.
- **Remote Monitoring:** Enables monitoring of device URLs and ports remotely.
- **Threshold-Based Alerts:** Configurable alerts based on user-defined thresholds.

## Rootcause Features
- **Rootcause Classification:** Clasification of Normal and Faulty behavior(s) on the device
- **Classification Alerts:** Receieve notifications when specific rootcauses are occuring
- **Faulty Channel Forwarding:** Receive payloads of the channels that created the faulty condition/rootcause 

## Notifications and Alerts

- **Abnormalities and Attack Detection Alerts:** Generates alerts for detected anomalies and publishes them to the launchpad.
- **Email Notification for Alerts:** Sends real-time email alerts.
- **AI-Based and Threshold-Based Alerts:** Uses AI insights and thresholds to trigger alerts.
- **External Exporter Alerts via HTTPS or Prometheus:** Sends alerts to external monitoring tools.
- **Remote HTTP/HTTPS Endpoint Status Alerts:** Notifies on endpoint availability issues.
- **Remote Server Port Status Alerts:** Alerts on remote server port status changes.
