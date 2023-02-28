# ext-mcrypt fix for Mac with Intel processor

Getting mcrypt extension working with different PHP versions(7.1, 7.2, 7.3, 7.4, 8.0) via Homebrew on Mac with Intel processor.


<img width="1084" alt="Screenshot 2022-12-05 at 10 34 18" src="https://user-images.githubusercontent.com/35255562/205603298-22200b9e-ca63-4b57-9816-c3097e1d1d8a.png">


## Solution

Source: https://bertnotbob.medium.com/getting-mcrypt-extension-working-on-php-7-3-6-and-macboo-homebrew-9a45c0622424

- Check for stable pecl versions: https://pecl.php.net/package/mcrypt

`pecl install mcrypt-1.0.3`

- Find the path to your in-use php.ini file

`php --ini`

- Check path with pecl versions:

`cd /usr/local/lib/php/pecl/`

- Open php.ini file and find the entry:

`extension_dir = "/usr/local/lib/php/pecl/<pecl_version>"`


### Repeat the following steps for all versions of php that you use:

- Create an mcrypt.ini file in the conf.d directory. Write…

```
;mcrypt

extension="/usr/local/lib/php/pecl/20180730/mcrypt.so
```

- Find out which version number of pecl matches the version of php, for ex. **20180730**

- Restart the web server

`brew services restart httpd`



# ext-mcrypt fix for Mac with Apple silicon

All instructions are the same as for Intel processor, only path is different.

- Check path with pecl versions:

`cd /opt/homebrew/lib/php/pecl/`

- Open php.ini file and find the entry:

`extension_dir = "/opt/homebrew/lib/php/pecl/<pecl_version>"`

### Repeat the following steps for all versions of php that you use:

- Create an mcrypt.ini file in the conf.d directory. Write…

```
;mcrypt

extension="/opt/homebrew/lib/php/pecl/20180730/mcrypt.so
```
