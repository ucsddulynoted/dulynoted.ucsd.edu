# Local Builds

Currently, only macOS documentation exists.

## macOS

Although [Homebrew](https://brew.sh/) is used for the following steps, feel free set up your
environment however you see fit.

1. Run `brew install httpd`
2. Create a symlink from the website directory to `/opt/homebrew/var/www`
    - Note that if `www` currently exists, the directory and all its contents need to be deleted.
3. Update `/opt/homebrew/etc/httpd/httpd.conf` as follows
    - Replace `Allow Override None` to `Allow Override All` in `<Directory "/opt/homebrew/var/www">`
        - This ensures that `.htaccess` works properly
    - Uncomment `LoadModule rewrite_module lib/httpd/modules/mod_rewrite.so`
        - This ensures that `.htaccess` url rewrites work properly
4. Run `brew services start httpd`

The website should now be accessibly from `https://localhost:8080/`

To stop your local build, run `brew services stop httpd`.
