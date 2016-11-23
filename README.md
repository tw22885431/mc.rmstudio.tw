# Repository of mc.rmstudio.tw

This is the git repository of mc.rmstudio.tw website. If you are willing to contribute, feel free to fork, modify and send pull request.

## Development

You can do shallow clone to get this repo more quickly.

`git clone https://github.com/RMStudioTW/mc.rmstudio.tw.git --depth 1`


## Static Pages Local Installation

It's easy to set up static pages.

### Apache 2.4

To enable SSI on Apache is very easy. Take Ubuntu for example, just execute `a2enmod include` then you have a SSI-ready Apache.

The second step is adding virtual host configs to your Apache configuration:

```apache
<VirtualHost *:80>
    ServerName mc-rmstudio.yourdomain.name
    ServerAdmin admin@yourdomain.name
    DocumentRoot /path/to/this/repo/
    <Directory /path/to/this/repo>
        Options FollowSymLinks Includes
        SSILegacyExprParse on
        Order allow,deny
        Require all granted
    </Directory>
</VirtualHost>
```

Enable the new virtual host with `a2ensite mc-rmstudio`, restart Apache, and open *http://mc-rmstudio.yourdomain.name*. You should now see the webpages.

### Nginx

Example of site configuration with SSI module enabled:

```nginx
server {
    listen 80;
    server_name mc-rmstudio.yourdomain.name;
    root /path/to/this/repo/;

    ssi on;
    ssi_types text/shtml;
    index index.html index.htm index.shtml index.php;
}
```

## Coding Style
* Please always use LF on line ending, and set 4 space characters as indent.
* Please take [Mozilla Coding Style](https://developer.mozilla.org/en-US/docs/Mozilla_Coding_Style_Guide) as reference.
