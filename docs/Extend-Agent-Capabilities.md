# Extending Agent Capabilities (Remediation & Customization)

MicroAI allows users to extend its machine intelligence capabilities by processing JSON output and implementing custom remediation actions. Users can utilize any programming language to parse data and take appropriate actions based on security alerts. Additionally, MicroAI provides built-in exporters to forward data to preferred remote locations such as HTTP, MQTT, or Redis.

# Output Json Payload

The agent generates both synchronous and asynchronous payloads, which are essential for monitoring alerts, notifications, and real-time device updates. By subscribing to these payloads, users can implement custom remediation strategies or automated responses.

For a detailed breakdown of both SYNC and ASYNC payload structures, refer to the [payload documentation](./Sync-and-Async-Payloads.md).

## Custom Remediation Examples

### Configure External Exporter

In order to extend the capabalities of the agent, the alerts and synschronous data needs to be configured to an output based on the selected protocol. The example below shows how this can be configured to use the http protocol.

```json
{
  // ... other fields ...
    "ExternalExporter": {
      "ExternalExporterType": "HTTP", // Update the exporter Type
      "Https_Post_Endpoint": "http://localhost:8000", // Add the desired endpoint
      "Output_Redis_Endpoint": "",
      "Output_MQTT": {
        "Endpoint": "127.0.0.1",
        "Port": 1884,
        "Username": "",
        "Password": "",
        "topic_prefix": "data/"
      }
    }
  // ... other fields ...
}
```

### Filtering Alerts to Relevancy
By analyzing incoming alerts, users can filter out non-critical events and focus on relevant security incidents. This can be done by:
- Identifying alert types (e.g., `MAIAlert`) from MicroAI JSON output.
- Filtering based on severity, category, or keywords.
- Logging only high-priority alerts.

**Example Python Script to Filter Alerts:**

```python
from fastapi import FastAPI, Request
import json

# List of severities to filter
SEVERITIES_TO_FILTER = ["High", "Critical"]  # You can easily change these values

app = FastAPI()

def process_message(message):
    """Process and filter MAIAlert messages with specified severity levels."""
    try:
        data = json.loads(message)
        for alert in data.get("feed", []):
            if alert.get("message_type") == "MAIAlert" and alert.get("severity") in SEVERITIES_TO_FILTER:
                print(f"\n#High/Critical Alert Detected!")
                print(f"Time: {alert['edge_datetime']}")
                print(f"Device: {alert['device_id']}")
                print(f"Alert: {alert['sensor_name']}")
                print(f"Severity: {alert['severity']}")
                print(f"Details: {alert['text_value']}\n")
    except json.JSONDecodeError:
        print("? Error decoding JSON")

@app.post("/")
async def receive_alerts(request: Request):
    """API endpoint to receive alerts and process them."""
    try:
        data = await request.json()  # Parse the JSON data

        if data.get("message_type") == "ASYNC":
            print("[INFO] Processing ASYNC message...")

            for alert in data.get("feed", []):
                msg_type = alert.get("message_type", "")
                if "MAIAlert" in msg_type:
                    process_message(json.dumps(data))  # Process the received message
        return {"status": "success", "message": "Alert processed"}
    
    except json.JSONDecodeError:
        print("[ERROR] Failed to decode JSON message!")
        return {"status": "error", "message": "Invalid JSON"}

if __name__ == "__main__":
    import uvicorn
    uvicorn.run(app, host="0.0.0.0", port=8000)
```

