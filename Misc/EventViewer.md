## wevtutil.exe

As Microsoft states "enables you to retrieve information about event logs and publishers. You can also use this command to install and uninstall event manifests, to run queries, and to export, archive, and clear logs."

* Access help files `wevtutil.exe /?`
* Provides help on specific command `wevtutil COMMAND /?`
* Displays number of logs on the host `wevtutil.exe el | Measure-Object`
* Gets all the event logs, using the wildcard asterick to display information about each log `Get-WinEvent -ListLog *`
* Examples retreives all providers that write to Applications log `(Get-WinEvent -ListLog Application).ProviderNames`
* Gets list of providers with names that include a specific string in the provider's name `Get-WinEvent -ListProvider *Policy*`

