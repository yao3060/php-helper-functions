# php helper functions

## Array Insert
```php
if(!function_exists('array_insert')){
  function array_insert(
      array $array = [],
      int $position = 0,
      array $new_array = [],
      bool $preserve_keys = true
  ): array {
      return array_slice($array, 0, $position, $preserve_keys) +
          $new_array +
          array_slice($array, $position, count($array) - 1, $preserve_keys);
  }
}
```

## Get the Client Real IP address

```php
if(!function_exists('get_client_real_ip')){
  function get_client_real_ip()
  {
      $ipaddress = '';
      if (isset($_SERVER['HTTP_CLIENT_IP']))
          $ipaddress = $_SERVER['HTTP_CLIENT_IP'];
      else if (isset($_SERVER['HTTP_X_FORWARDED_FOR']))
          $ipaddress = $_SERVER['HTTP_X_FORWARDED_FOR'];
      else if (isset($_SERVER['HTTP_X_FORWARDED']))
          $ipaddress = $_SERVER['HTTP_X_FORWARDED'];
      else if (isset($_SERVER['HTTP_FORWARDED_FOR']))
          $ipaddress = $_SERVER['HTTP_FORWARDED_FOR'];
      else if (isset($_SERVER['HTTP_FORWARDED']))
          $ipaddress = $_SERVER['HTTP_FORWARDED'];
      else if (isset($_SERVER['REMOTE_ADDR']))
          $ipaddress = $_SERVER['REMOTE_ADDR'];
      else
          $ipaddress = 'UNKNOWN';
      return $ipaddress;
  }
}
```

## Get Media File Type From URL

```php
if (!function_exists('get_file_type_from_url')) {
    function get_file_type_from_url(string $url, string $default = 'file'): string
    {
        $ext = pathinfo($url, PATHINFO_EXTENSION);
        if (in_array($ext, ['jpg', 'jpeg', 'jpe', 'gif', 'png', 'webp'])) {
            return 'image';
        }

        if (in_array($ext, wp_get_audio_extensions())) {
            return 'audio';
        }

        if (in_array($ext, wp_get_video_extensions())) {
            return 'video';
        }

        return $default;
    }
}
```

## Get Datetime  in GMT ISO8601 format

```php
if (!function_exists('gmt_iso8601')) {
    function gmt_iso8601($time)
    {
        return (new \DateTime(null, new \DateTimeZone('UTC')))->setTimestamp($time)->format('Y-m-d\TH:i:s\Z');
    }
}
```
