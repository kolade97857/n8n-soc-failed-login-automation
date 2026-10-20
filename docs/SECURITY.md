# Security and safe-use notes

## Before publishing

- Never commit passwords, API keys, OAuth access/refresh tokens, session cookies, or credential exports.
- The workflow export has been sanitized to remove the original Gmail recipient, saved credential references, workflow instance ID, metadata instance ID, and Gmail webhook ID.
- n8n credential records are not included; configure credentials locally after import.
- Replace the placeholder Splunk host and alert recipient in n8n.
- Review screenshots for email addresses, usernames, internal IPs, hostnames, tokens, and other personal or environment-specific information before uploading.

## Least privilege

Use a dedicated Splunk account for automation with only the permissions needed to run the specified searches. Avoid using an administrator account. Store credentials in n8n's credential store, not in Code nodes, expressions, JSON files, or GitHub.

## TLS

The original lab used a self-signed certificate, so the workflow had certificate verification bypass enabled. This reduces protection against interception. It is retained only to reproduce the local lab. Prefer a trusted certificate and disable the bypass for any shared or production environment.

## Scope

Use only systems and logs you own or are explicitly authorized to monitor. The sample threshold is a demonstration rule and should be tuned to the environment before operational use.
