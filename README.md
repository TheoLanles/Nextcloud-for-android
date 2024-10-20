 # Nexcloud-for-android
 
 ## script to install nextcloud on android (firetv cube/stick, nvidia shield, phone etc)

- install termux from fdroid https://f-droid.org/en/packages/com.termux/
- install termux:boot from https://f-droid.org/en/packages/com.termux.boot/ and run it once
open termux and paste following code start:

` termux-setup-storage; pkg update -o Dpkg::Options::='--force-confold' --force-yes -fuy; pkg install wget -y; wget -O - https://raw.githubusercontent.com/TheoLanles/Nextcloud-for-android/refs/heads/main/install.sh | bash; `

### to modify the php memory
then find where php.ini is located and do :

` php --ini `
` nano path/to/php/php.ini `

if no php.ini file exists, create one with this in it:

`
[PHP]
memory_limit = 512M
upload_max_filesize = 100M
post_max_size = 100M
max_execution_time = 300
`

or if it already exists, change memory_limit = 128M to memory_limit = 512M.

### then stop and start lighttps with this command:

` pkill lighttpd and lighttpd -f ~/lighttpd.conf `

finally open a browser and navigate to http://localhost:8080/ to finish the setup. essentially this will install a termux instance, that runs on boot and prevents deep sleep of your device. the nextcloud server will be open to all external hosts and no SSL certificate will be used!
