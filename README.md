update-cf-dns
=============
bash script for updating a cloudflare DNS record based on your detected public IP.

WIP notes
---------
I'm not yet parsing the supplied domain as well as I'd like, needing to find and seperate subdomain and domain to identify the tarket cloudflare zone and record.

Requires
--------
* __bash__
* __curl__
* __jq__
* cloudflare account and API token.
* said account being used for domain's DNS

Usage
-----
`update-cf-dns [cf_domain] [cf_token]`  
script is intended to be set as a cronjob that will check and update a DNS A record if your server's Public IP has changed.  
__CF_DOMAIN__  is the full domain for the record you will to check and update. Must be supplied as either the first argument on the script, or as an environment variable `CF_DOMAIN`  
__CF_TOKEN__  Your cloudflare API key. Must be supplied as the second argument or better as an environment variable `CF_TOKEN`. Your API token must also have read permissions for all zones, and write permissions for at least your target zone.  
  
Given cloudflare's API usage limits, and general DNS practice and TTL, I'd recomend setting this as a cronjob that only runs every 12 to 6 hours. This is not intended as a fully dynamic dns solution or for critical systems.

Links
-----

https://api.cloudflare.com/
