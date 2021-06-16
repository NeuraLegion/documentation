# ℹ Command Language Syntax
Nexploit CLI accepts a wide variety of configuration arguments. You can run ```nexploit-cli --help``` command for comprehensive documentation. The configuration options in the command line must be passed after the program command that Nexploit CLI is executing.

```bash
 nexploit-cli.exe <command> [options] [<file | scan>]
```
* Most commands and some options have aliases. Aliases are shown in the syntax statement for each command.
* Option names are prefixed with a double dash (--). Option aliases are prefixed with a single dash (-). Arguments are not prefixed. For example:

```bash
  nexploit-cli scan:stop --token my-jwt-authentication-token
```
* Support is provided for an array of values of a specific argument, separated by a space. For example:

```bash
  nexploit-cli scan:run
  --token my-jwt-authentication-token
  --name scan-name
  --crawler target-url
```
Nexploit CLI provides multiple global options that can affect the behavior of each command, as follows:


<table id="simple-table">
<tr>
<th width="25%"><strong>Option</strong></th>
<th><strong>Description</strong></th>
</tr>
<tr>
<td><code>--config=configPath</code></td>
<td>Specifies the path to the configuration file. By default, the CLI tries to discover the config in <code>package.json</code> in the root directory of your application or a separate file by a specified name in the working directory. For details, see <a href="/#/guide/np-cli/configuration-files.md">Configuration Files</a> for more information.</td>
</tr>
<tr>
<td><code>--api=proxyUrl</code></td>
<td>Nexploit base URL. The default is <code>https://nexploit.app/</code>.</td>
</tr>
<tr>
<td><code>--proxy=proxyUrl</code></td>
<td>SOCKS4 or SOCKS5 URL to proxy all traffic.</code></td>
</tr>
</table>


Typically, the generated artifact can be given as an argument to the command or specified with the `--archive` option. You can see archive:generate for more information.