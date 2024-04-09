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
