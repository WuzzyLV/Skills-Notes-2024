[ID3](https://github.com/wapmorgan/Mp3Info)

```
RewriteEngine on
RewriteCond "%{REQUEST_FILENAME}"       !-f
RewriteCond "%{REQUEST_FILENAME}"       !-d
RewriteRule ^(.*)$ /index.php?path=$1 [QSA,L]
```

```php
header("Content-Transfer-Encoding: binary");
header("Content-Type: audio/mpeg, audio/x-mpeg, audio/x-mpeg-3, audio/mpeg3");
header('Content-Disposition:: inline; filename="song.mp3"');
header('Content-length: ' . filesize($song['path']));
header('Cache-Control: no-cache');
header('Accept-Ranges: bytes');
readfile($song['path']);
```
