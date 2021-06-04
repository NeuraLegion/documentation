# 🔛 Initializing a Repeater
```nexploit-cli repeater [options]``` initializes a local Repeater process. When a scan is connected to such a Repeater, all the scan requests are pulled from the cloud through the Repeater to the local target of the scan.

The Repeater enables you to run the Nexploit scans on a local compiled application, without exposing your ports externally. This means that you can scan an application without having to deploy it or to generate external reports.

The Repeater relies on the supported versions of the Nexploit CLI. For example, if you have already connected a Repeater, you cannot connect another Repeater with the same ID but a different CLI version. In this case, you first need to install the latest version of the Nexploit CLI and then procceed with the connection.   

For details about how the Repeater works, see [On-Prem Agent Repeater (Agent) Deployment](guide/introduction/deployment-options.md#on-premises-repeater-agent).

## Additional Features
* Enables multiple scans to run through a single Repeater.
* Option to add headers to requests locally (authentication cookie and so on), without exposing them to the cloud.

> [!WARNING|label:Important]
The Repeater requires a working `AUTH_TOKEN` with the scope repeaters:write.

## Options

<table id="simple-table">
<tr>
<th width=27%><strong>Option</strong></th>
<th><strong>Description</strong></th>
</tr>
<tr>
<td><code>--id=repeaterId</code></td>
<td>The ID of an existing Repeater that you want to use.</td>
</tr>
<tr>
<td><code>--token my-jwt-authentication-token</code></td>
<td>The unique identifier used to authenticate a user. It can be issued in your organization’s dashboard.</td>
</tr>
<tr>
<td><code>--bus=eventBus</code></td>
<td>Nexploit Event Bus URL.<br><br><strong>Default:</strong><code>--bus amqps://amq.nexploit.app:5672</code></td>
</tr>
<tr>
<td><code>--header=extraHeader</code>,<br> <code>-H=extraHeader</code></td>
<td>Extra headers to be passed with each request. Also, it can be used to remove a header by providing a name without content. For example, -H "Host:".<br><br><strong><font color="red">Warning:</font></strong> Headers set with this option override the original headers and are set in all requests.</td>
</tr>
<tr>
<td><code>--headers=json</code></td>
<td>JSON string that contains a header list, which is initially empty and consists of zero or more name and value pairs. <br><br><strong><font color="red">Warning:</font></strong> Headers set with this option override the original headers and are set in all requests.</td>
</tr>
<tr>
<td><code>--proxy=proxyUrl</code></td>
<td>SOCKS URL to proxy all traffic.<br><br> <em>Example:</em> <code>nexploit-cli repeater --proxy socks://209.97.150.167:1080 ...</code>.<br><br> <strong><font color="blue">Note:</font></strong> SOCKS4, SOCKS5, SOCKS4a, SOCKS5h are currently supported. By default, if you specify <code>SOCKS://&lt;URL&gt;</code> , then SOCKS5h is applied.</td>
</tr>
<tr>
<td><code>--daemon</code>, <code>-d</code></td>
<td>Initializes the Repeater as a local daemon service <br><br> <strong><font color="blue">Note:</font></strong> If you run this command while a service is already running, it will first stop &amp; delete the running service, and restarts it with the new repeater settings.<br><br> <strong><font color="blue">Note:</font></strong> Currently supported operating systems include windows (wscm) &amp; Linux (systemd).</td>
</tr>
<tr>
<td><code>--remove-daemon</code>, <code>--remove</code>, <code>--rm</code></td>
<td>Stops and deletes the running repeater service.</td>
</tr>
<tr>
<td><code>--scripts</code></td>
<td>Loads scripts to the Repeater from a JSON of <code>{ "host": "filepath" }</code>.<br><br><b><font color="blue">Note:</font></b> Wildcards are also supported, for example: <code>--scripts '{"*": "./hmac.js"}'</code> for a global script for all target hosts, or <code>--scripts '{"*.domain.com": "./hmac.js"}'</code> for all target hosts on sub-domains.<br><br>If you have loaded a local script to the Repeater using the relative CLI command, loading remote scripts from <a href="https://nexploit.app/" target="_blank" rel="noopener">nexploit.app</a> is disabled automatically.<br><br>See <a href="#/guide/np-web-ui/advanced-set-up/using-repeaters-scripts/scripts-overview">Repeater Scripts</a> for more information about how the Repeater Scripts work.</td>
</tr>
<tr>
<td><code>--cacert</code></td>
<td>You may require to authorize Nexploit to your network server by providing valid TLS/SSL certificates. This option allows you to load a file with multiple CA certificates to the Repeater that you use for the scan, for example:<br><code>nexploit-cli repeater --cacert /etc/ssl/certs/ca-certificates.crt</code><p> You can load certificates from the “Trusted Root Certification Authorities Certificate Store” (Windows ONLY):<br><code>nexploit-cli repeater --cacert true</code></p><p>The Nexploit CLI also supports autodiscovery from the following files:<br><code>/etc/ssl/certs/ca-certificates.crt</code>    <code>// Debian/Ubuntu/Gentoo etc.</code><br><code>/etc/pki/tls/certs/ca-bundle.crt</code>         <code>// Fedora/RHEL 6</code><br><code>/etc/ssl/ca-bundle.pem</code>                   <code>// OpenSUSE</code><br><code>/etc/pki/tls/cacert.pem</code>               <code>// OpenELEC</code><br><code>/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem // CentOS/RHEL 7</code><br><code>/etc/ssl/cert.pem</code>                          <code>// Alpine Linux</code><br><code>nexploit-cli repeater --cacert true</code></p></td>
</tr>
<tr>
<td><code>--cert</code></td>
<td>You can load a certificate file per host. The file must contain a certificate in the PKCS or PEM format. <p> <em>Format:</em> <code>--cert "{"hostname": "example.com", "path": "./example.pem", "passphrase": "pa$$word"}"</code><p> <em>Example:</em> <code>nexploit-cli repeater --cert "{\"path\": \"/home/user/example.pfx\", \"hostname\": \"example.com\", \"passphrase\": \"pa$$word\"}"</code><p> The <code>passphrase</code> is optional.</td>
</tr>
<tr>
<td><code>--log-level</code></td>
<td> Allows setting the level of logs to report. Any logs of a higher level than the one specified are shown.<br> The options to select : 0, 1, 2, 3, 4, "silent", "error", "warn", "notice", "verbose". The default option is 3.</td>
</tr>
</table>


