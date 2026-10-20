# Evidence index

The evidence is organized by source and purpose. Screenshots are included as captured during the lab session; they have been renamed for easier navigation, but the image contents have not been altered. Review them before public posting if you want to redact any local usernames, hostnames, or IP addresses.

## PowerShell / Windows endpoint

The `powershell/` folder contains the PowerShell screenshots shared during the October 20 troubleshooting session, ordered by timestamp in their filenames.

Highlighted captures:
- `*windows-event-4625-history.png` — query of Windows Security Event ID 4625 with historical local results.
- `*windows-security-input-configuration.png` — Splunk Universal Forwarder Security input configuration.
- `*windows-event-input-configuration.png` — Windows Event Log input configuration.
- `*splunk-forwarder-service-running.png` — Splunk Forwarder service state showing Running / Automatic / LocalSystem.
- `*failed-logon-events-in-windows.png` — failed-logon event messages and timestamps.
- `*recent-4625-query-initial-attempt.png` — a recent-event query attempt that shows a RUNAS error and no matching result at that moment; this is troubleshooting evidence, not a success result.
- `*recent-4625-query-result.png` — a subsequent recent Event ID 4625 query showing a matching Windows Security Auditing event.

Other timestamped PowerShell captures preserve the additional configuration, command output, and troubleshooting evidence from the same session.

## Splunk

- `splunk/01_four_historical_event_4625_results.png` — four historical Event ID 4625 records returned by the Splunk search.
- `splunk/02_splunk_event_code_distribution.png` — distribution of event codes in Splunk. This shows indexed Windows telemetry, but does not by itself prove fresh Event ID 4625 ingestion.

## n8n

- `n8n/01_n8n_workflow_overview.png` — workflow canvas showing the Splunk HTTP Request nodes and JavaScript processing.
- `n8n/02_detection_output_below_threshold.png` — detector output below the configured threshold.
- `n8n/03_n8n_workflow_execution_overview.png` — workflow execution canvas.

## Evidence limitation

During troubleshooting, the local Windows Security log showed Event ID 4625 records, but newly generated events were not consistently appearing in Splunk. The historical Splunk query returned four events, and the detector reported two failures within 15 minutes, below the threshold of five. The evidence therefore supports a working prototype and a tested synthetic alert path, but **does not prove fully reliable live Splunk-to-n8n monitoring**.
