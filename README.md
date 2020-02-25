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

## Control Panels

### Interworx

#### Test Configuration

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

##### Installation

[Interworx Installation](https://www.interworx.com/support/faq/install-interworx-control-panel/)



### Plesk

#### Test Configuration

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

##### Installation

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

### DirectAdmin

#### Test Configuration

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

##### Installation

[Install Guide](https://www.directadmin.com/installguide.php)

Trial Licensed on directadmin-01.sectigodemo.com until April 14.

* Necessary for installation.

## Server Information

interworx-01.sectigodemo.com

> IP address: 45.76.77.89
> Licensed: Yes

* Accounts:
  * iwx-01: 
    * Granted all privileges.
    * Granted all Package Features.
    * Granted all Package Options except:
      * Account Backup (Off by default)
    * Secondary Domain: add-iwx-01.sectigodemo.com
    * Subdomain:  sub.iwx-01.sectigodemo.com

directadmin-01.sectigodemo.com

> IP address: 149.28.65.95
> Licensed: Trial Until April 14th

* Accounts
  *  Same general setup as above.
     *  TODO: say more.

plesk-01.sectigodemo.com

> IP address:  149.28.76.248 
> Licensed: No

* Accounts
  * Users and domains are nuts on plesk, but again, happy path to victory.

Needed dns entries: 

interworx-01.sectigodemo.com : 45.76.77.89
iwx-01.sectigodemo.com : 45.76.77.89
sub.iwx-01.sectigodemo.com : 45.76.77.89
add-iwx-01.sectigodemo.com : 45.76.77.89

directadmin-01.sectigodemo.com : 149.28.65.95
da-01.sectigodemo.com : 149.28.65.95
sub.da-01.sectigodemo.com : 149.28.65.95
add-da-01.sectigodemo.com : 149.28.65.95
blesta.sectigodemo.com : 149.28.65.95

plesk-01.sectigodemo.com : 149.28.76.248
p-01.sectigodemo.com : 149.28.76.248
sub.p-01.sectigodemo.com : 149.28.76.248
add-p-01.sectigodemo.com : 149.28.76.248

## Anticipated Issues

DNS propagation: if we can't use subdomains as main account domain in the panel this may slow things down. Maybe nothing but it's something to keep in mind.

## Testing considerations

Test case and configuration considerations.

* Panel limitations around subdomains, email only domains (?), various service certificates, etc.
* Account setup processes.
  * Account permissions/privileges for setting up ssl via API?
* Tested via account and admin/root authentication if possible.
* Testing permutations: optional service providers: i.e., MTA and MDA, or webservers for docs.
  * Permutation options are really the responsibility of the panel around how their api works with each service, but it's a good documentation and support head's up.
    * Confusion, on the part of the customer and support around the separation of concerns of the panel and the product, will incur support cost.
  * Integration testing will eventually arise as a necessity as panels update and bork their API with some underlying service change.

## Blesta Installation

I chose to install it on the Directadmin server. This choice was based on the fact that Plesk is not a good choice for various reasons from research I did. The way ( it may be a solved problem now ) that it restarts apache smashes the blesta api connection.

DirectAdmin has it's own set of problems. But it seems like the most stable of the three to install it on. Interworx has been generally frustrating to work with so far. It needs some tweaking before it's ready to do any type of work. The interface suddenly and frequently becomes unresponsive and the iworx server stops serving pages. Restarting the iworx process resolves the issue, but not for long. It almost seems to be ddos(ing) itself, but I need to dig into it further before I jump to any conclusions.

Installing the prerequisite php modules required a little wrangling.

* yum install epel-release ; yum install uw-imap-devel uw-imap-static libc-client
* yum install gmp-devel
* And adding the prerequisites through the php custombuild script.
* Tons of symlinking /usr/lib64/*.{so,a} to /usr/lib

### Account setup

Creating a reseller for backup purposes. This should make the domain and user setups transferrable . . . to another directadmin server. A similar setup should be considered for any other test components aside from test accounts/domains. This will require further thought. But we're just exploring right now. Nothing is written in stone yet.

Rsync seems to be the best bet here.

### GOTCHAS

Turn off SSL for all of the blesta modules until I can look into service certificates. . . It fails quite silently on DirectAdmin.

It was necessary to install a letsencrypt ssl certificate for plesk. There is no option to disable ssl in the module configuration.

* See if there is a way to simply make it more permissive.

csf is installed on the blesta directadmin server. This too causes failures that are very quite.


- [ ]   Generate Certs for each domain and subdomain
- [ ]   Work out authentication scripts.
- [ ]   Spec out api calls.
- [ ]   Wrtie api calls.
