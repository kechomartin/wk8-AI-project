# AI Agents Simulation for AutoParts Inc.

## Overview
This n8n workflow demonstrates the core interaction between the **Predictive Maintenance Agent** and **Production Orchestrator Agent** for AutoParts Inc.'s smart manufacturing implementation.

## Workflow Description

### Trigger
- Simulated machine sensor data (vibration levels) exceeding threshold

### Nodes & Process:
1. **Cron Trigger**: Simulates regular sensor data polling (every 2 minutes)
2. **Function Node - Sensor Data Simulator**: Generates realistic machine sensor data with random vibration levels
3. **IF Node - Predictive Maintenance Agent**: Analyzes vibration data and triggers alert if threshold exceeded
4. **Function Node - Alert Generator**: Creates detailed maintenance alert with machine info and severity
5. **Function Node - Production Orchestrator Agent**: Reschedules production and creates maintenance ticket
6. **Email Node**: Sends alert to maintenance team (configure with your email)
7. **Google Sheets Node**: Logs all maintenance events (optional)

## Setup Instructions

### 1. Import the Workflow
- Go to n8n Settings > Import from File
- Select `workflow_export.json` from this folder

### 2. Configure Nodes

#### Email Node (Node #6):
- Update "Send To" field with your actual email address
- Configure your email provider (Gmail, SMTP, etc.)

#### Google Sheets Node (Node #7 - Optional):
- Connect your Google account
- Create a spreadsheet with columns: Timestamp, MachineID, VibrationLevel, Status, AlertMessage, RescheduledJobs
- Update the spreadsheet ID in the node

### 3. Activate the Workflow
- Toggle the workflow to "Active"
- The cron trigger will run every 2 minutes for demonstration

## Expected Output

When vibration exceeds 7.5 (on a 0-10 scale):
- Maintenance alert email sent to team
- Production jobs automatically rescheduled
- Event logged to Google Sheets (if configured)
- Console output showing the agent decisions

## Testing

1. **Normal Operation**: Vibration < 7.5 - No alerts, normal logging
2. **Maintenance Alert**: Vibration > 7.5 - Full alert workflow triggered
3. **Manual Trigger**: Use "Execute Workflow" button to test immediately

## Customization

- Adjust vibration threshold in IF Node (#3)
- Modify maintenance response time in Production Orchestrator (#5)
- Add additional alert channels (Slack, SMS)
- Integrate with actual machine APIs