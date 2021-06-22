# 🧩 Integrating with a Service
`nexploit-cli integration [options]` connects Nexploit with ticketing and management services deployed on local servers (currently only the On-Premise Jira is supported). The repositories of the connected services can then be integrated with the Nexploit projects and used as endpoints for the scan reports.

For more information about the integration capabilities, see [Ticketing Systems](/guide/pipeline-integration/ticketing-systems/ticketing-overview.md).

## Script Example
```bash
nexploit-cli integration                  \
--access-key INTEGRATION_ACCESS_KEY       \
--base-url https://acme.atlassian.net     \
--user username                           \
--password pa$$word                       \
--token API_TOKEN                         \
```
## Options

<table id="simple-table">
<tr>
<th><strong>Option</strong></th>
<th><strong>Description</strong></th>
</tr>
<td><code>--bus=eventBusUrl</code></td>
<td><b><i>(Deprecated)</i></b>. Nexploit event bus URL.<br><br><strong>Default:</strong><code>--bus amqps://amq.nexploit.app:5672</code></td>
</tr>
<tr>
<td><code>--access-key=integrationKey</code></td>
<td>The unique identifier generated on the <strong>JIRA INTEGRATION CONFIG</strong> popup of the <a href="https://nexploit.app/" target="_blank" rel="noopener">nexploit.app</a>.<br> Required to authorize Nexploit to the On-Premise Jira (local Jira Server).</td>
</tr>
<tr>
<td><code>--type=jira</code></td>
<td>Integration service type (currently only JIRA is supported).</td>
</tr>
<tr>
<td><code>--base-url=serviceUrl</code></td>
<td>The base URL to the Jira instance API.</td>
</tr>
<tr>
<td><code>--user=serviceUserName</code></td>
<td>Use a username for a local Jira Server or email for the Atlassian Jira Cloud.</td>
</tr>
<tr>
<td><code>--password=serviceUserPassword</code></td>
<td>Use a password for a local Jira Server or API token for the Atlassian Jira Cloud.</td>
</tr>
<tr>
<td><code>--token=apiKey</code>,<br><code>-t=apiKey</code></td>
<td>Nexploit <a href="https://kb.neuralegion.com/#/guide/np-web-ui/advanced-set-up/managing-org?id=managing-organization-apicli-authentication-tokens" target="_blank" rel="noopener">organization API key</a> or <a href="https://kb.neuralegion.com/#/guide/np-web-ui/advanced-set-up/managing-personal-account?id=managing-your-personal-api-keys-authentication-tokens" target="_blank" rel="noopener">personal API key</a> with the <code>bot</code> scope.<br> The <code>bot</code>scope enables connection between Nexploit and the Nexploit CLI.</td>
</tr>
<tr>
<td><code>--daemon</code>,<br> <code>-d</code></td>
<td>Runs the integration in a daemon mode.</td>
</tr>
</table>
