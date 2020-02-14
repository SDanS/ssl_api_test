# ssl_api_test

```
1. Install & Configure Interworx Control Panel 
2. Review Documentation on API to determine if we can automate SSL from an external billing systems.

1. Install & Configure Plesk Control Panel 
2. Review Documentation on API to determine if we can automate SSL from an external billing systems.

1. Install & Configure DirectAdmin 
2. Review Documentation on API to determine if we can automate SSL from an external billing systems.

1. Install & Configure Blesta Billing System 
2. Configure for close to real life testing. 
```

## Interworx

### Test Configuration

* Environment setup:
  * Vultr VM specs:
    * For the purposes of PoC the following will be used:
      * 2GB Memory
      * 2GB Swap
      * 55GB disk
      * 1 VCPU
    * For testing, it may be wise to use a more Memory constrained system.
      * Interworx' documentation seems to indicate (not super clearly) that it should be able to run on a system with 1GB of memory.
  * OS: CentOS7 (max supported)
  * [System Requirements](https://www.interworx.com/support/faq/requirements-interworx-control-panel/)

#### Installation

[Interworx Installation](https://www.interworx.com/support/faq/install-interworx-control-panel/)



## Plesk

### Test Configuration

* Environment setup:
  * Vultr VM specs:
    * For the purposes of PoC the following will be used:
      * 2GB Memory
      * 2GB Swap
      * 55GB disk
      * 1 VCPU
    * For testing, it may be wise to use a more Memory constrained system.
  * OS: CentOS7 (max supported) and Windows (?)
    * It runs on many OS(s).
  * [Software Requirements](https://www.plesk.com/blog/various/plesk-requirements-hardware-software/)
  * [Hardware Requirements](https://docs.plesk.com/release-notes/12.5/hardware-requirements/)

#### Installation

[Install instructions](https://www.plesk.com/blog/various/install-plesk-linux/)

Plesk version: Obsidian

* [New SSL mail feature](https://bobcares.com/blog/plesk-onyx-vs-obsidian/)
* 
```
Would you like to help Plesk make better products by sending information 
about issues occurred, including installation and upgrade issues? [Y/n]: n
```
* Used the Recommended Installation.
* 
```
        The installation has been finished. Plesk is now running on your server.
  
        To complete the configuration process, browse either of URLs:
          * https://149.28.76.248.vultr.com/login?secret=C5p9DNgaTBO1s-yCRrvLMwXQnsSkbBOryj5-uZT8MOXy7LV9
          * https://149.28.76.248/login?secret=C5p9DNgaTBO1s-yCRrvLMwXQnsSkbBOryj5-uZT8MOXy7LV9
  
        Use the username 'admin' to log in. To log in as 'admin', use the 'plesk login' command.
        You can also log in as 'root' using your 'root' password.
  
        Use the 'plesk' command to manage the server. Run 'plesk help' for more info.
  
        Use the following commands to start and stop the Plesk web interface:
        'service psa start' and 'service psa stop' respectively.
  
        If you would like to migrate your subscriptions from other hosting panel
        or older Plesk version to this server, please check out our assistance
        options: https://www.plesk.com/professional-services/
  


The changes were applied successfully.
```

## DirectAdmin

### Test Configuration

* Environment setup:
  * Vultr VM specs:
    * For the purposes of PoC the following will be used:
      * 2GB Memory
      * 2GB Swap
      * 55GB disk
      * 1 VCPU
    * For testing, it may be wise to use a more Memory constrained system.
  * OS: Up to CentOS 8.
    * It runs on many OS(s).
  * [System Requirements](https://www.directadmin.com/install.php)

#### Installation

[Install Guide](https://www.directadmin.com/installguide.php)

