# n8n Workflow Visualization

## Predictive Maintenance Agent Workflow

┌─────────────────┐ ┌──────────────────┐ ┌─────────────────────┐
│ Cron Trigger │───▶│ Sensor Data │───▶│ Predictive Maintenance│
│ (Every 2 min) │ │ Simulator │ │ Agent (IF Node) │
└─────────────────┘ └──────────────────┘ └──────────┬──────────┘
│
┌────────────────────────────────────┼────────────────────────────────┐
│ │ │
▼ ▼ │
┌──────────────────┐ ┌──────────────────┐ │
│ Maintenance │ │ Log Normal │ │
│ Alert Generator │ │ Operation │ │
│ (Function Node) │ │ (Function Node) │ │
└─────────┬────────┘ └──────────────────┘ │
│ │
▼ │
┌──────────────────┐ │
│ Production │ │
│ Orchestrator │ │
│ Agent │ │
│ (Function Node) │ │
└─────────┬────────┘ │
│ │
▼ │
┌──────────────────┐ ┌──────────────────┐ ┌─────────┴────────┐
│ Email Alert │ │ Google Sheets │ │ Console Output │
│ to Maintenance │ │ Logging │ │ (Debug Info) │
│ Team │ │ (Optional) │ │ │
└──────────────────┘ └──────────────────┘ └──────────────────┘