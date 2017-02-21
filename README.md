# Toranproxy patch fix Composer doesn't cache Toran Proxy JSON Files
[Composer doesn't cache Toran Proxy JSON files](https://github.com/composer/composer/issues/3799)


Toran proxy when generate to file repo/private/packages.json usually default sha256 is null, so compose when update alway must download file info json, with large packages it take very long time ( i have 300 private packages, and it take 300s once time composer update). Unfortunately, when you use `composer update ` or `composer update package`, composer alway redownload json all private packages although, you don't use this package for your project. So. it is very painful. After i fix it, from 300s to 30s. very happy with me. 


access to http://packages.private-domain-xxx.net/repo/private/packages.json
view orginal:
```json
{
  "providers": {
    "organization/package-xxxx": {
        "sha256": null
    }
  }
 }
 ```
 
after run patch fix it.
```json
{
  "providers": {
    "organization/package-xxxx": {
        "sha256": "80c813c34816d6a0179a6987894a7d3641b4bba5c00c56d7d9b12e5c8c399552"
    }
  }
 }
```
