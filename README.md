## Basic usage

If you are running the script for the first time:

    # chmod +x /etc/adblock.sh
    # sh /etc/adblock.sh -f

There should be status updates in the output, but there should be *no* errors. If there are no errors, you should be good to go.+

## Whitelists and blacklists

The script supports defining whitelisted urls. That is, urls that will be filtered out of the downloaded blocklists. To whitelist urls, place them (one per line) in */etc/white.list*.

Similarly, the script supports defining blacklisted urls - urls that will be added to the downloaded blocklists. To blacklist urls, place them (one per line) in */etc/black.list*.

NOTE: The whitelist support is pretty stupid, so don't expect smart filtering (e.g., domain extrapolation). I've found it tedious, but worthwhile, to find the offending url in */etc/block.hosts* and copy it to */etc/white.list*.

## Advanced usage

### Configuration 

The config section of the script has some variables that alter the behaviour of the script.

For example, if you change:

    ONLY_WIRELESS = "N"
    
to

    ONLY_WIRELESS = "Y"
    
Then only the wireless interface of the router will filter the blocklist.

All variables:

* ONLY_WIRELESS (Y/N): Only filter on wireless interface
* EXEMPT (Y/N): Exempt ip range from filtering (between START_RANGE and END_RANGE)
* IPV6 (Y/N): Add IPv6 support
* SSL (Y/N): Install wget with ssl support (only needed for ssl websites)
* TRANS (Y/N): Modify router web server to server transparent pixel responses for blocked websites
* ENDPOINT_*: Define the IP to return for blocked hostnames (IPv4 and IPv6)
* CRON: The cron line to put in the crontab

### Toggle on and off

To toggle the blocking on and off, run the script with the -t switch:

    # sh /etc/adblock.sh -t

### Manually update blocklist

To manually update the blocklist, run the script without switches:

    # sh /etc/adblock.sh