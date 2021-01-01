#### TFTP

```tftp -i 10.11.0.111 put somefile.rar somefile.rar```

```tftp -i 10.11.0.111 get somefile.rar somefile.rar```

-----


#### Python

```import urllib```

```urllib.urlretrieve ("http://www.example.com/songs/mp3.mp3", "mp3.mp3")```

-----


#### Powershell

```$WebClient = New-Object System.Net.WebClient```

```$WebClient.DownloadFile("https://www.contoso.com/file","C:\path\file")```

-----

```Invoke-WebRequest -Uri "http://www.contoso.com" -OutFile "C:\path\file"```

-----


#### netcat

*On receiving end:*

```nc -l -p 1234 > out.file```

*On the sending end:*

```nc -w 3 [destination] 1234 < out.file```

-----
