
Splunk enterprise vs splunk cloud

Splunk Enterprise  9.2.1
Index 500 MB/Day. Sign up and download now. After 60 days you can convert to a perpetual free license or purchase a Splunk Enterprise license to continue using the expanded functionality designed for enterprise-scale deployments.


first create splunk account with enterprise email
https://www.splunk.com/en_us/sign-up.html

download dmg
https://www.splunk.com/en_us/download/splunk-enterprise.html?locale=en_us


### splunk download wget

```

CISCOU-2034$ wget -O splunk-9.2.1-78803f08aabb-macosx-10.11-intel.dmg "https://download.splunk.com/products/splunk/releases/9.2.1/osx/splunk-9.2.1-78803f08aabb-macosx-10.11-intel.dmg"
--2024-05-22 10:39:10--  https://download.splunk.com/products/splunk/releases/9.2.1/osx/splunk-9.2.1-78803f08aabb-macosx-10.11-intel.dmg
Resolving download.splunk.com (download.splunk.com)... 18.238.192.72, 18.238.192.2, 18.238.192.25, ...
Connecting to download.splunk.com (download.splunk.com)|18.238.192.72|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 724359396 (691M) [binary/octet-stream]
Saving to: ‘splunk-9.2.1-78803f08aabb-macosx-10.11-intel.dmg’

splunk-9.2.1-78803f0 100%[=====================>] 690.80M  68.4MB/s    in 11s

2024-05-22 10:39:21 (64.6 MB/s) - ‘splunk-9.2.1-78803f08aabb-macosx-10.11-intel.dmg’ saved [724359396/724359396]

CISCOU-2034$
```




✔  The installation was successful.

Click the "Splunk" icon on the Desktop to start and connect to Splunk.

To start Splunk manually, open a Terminal window and run the command: 
$ /Applications/Splunk/bin/splunk start

Documentation:
http://docs.splunk.com/Documentation/Splunk



terminal pop up

```

This appears to be your first time running this version of Splunk.

Splunk software must create an administrator account during startup. Otherwise, you cannot log in.
Create credentials for the administrator account.
Characters do not appear on the screen when you type in credentials.

Please enter an administrator username: 




```

user: admin
password: ******

```
This appears to be your first time running this version of Splunk.

Splunk software must create an administrator account during startup. Otherwise, you cannot log in.
Create credentials for the administrator account.
Characters do not appear on the screen when you type in credentials.

Please enter an administrator username: admin
Password must contain at least:
   * 8 total printable ASCII character(s).
Please enter a new password: 



```

start and show splunk

some terminal pop ups

```
Please enter an administrator username: admin
Password must contain at least:
   * 8 total printable ASCII character(s).
Please enter a new password: 












  [Restored May 22, 2024 at 10:49:36 AM]
Last login: Wed May 22 10:46:01 on ttys006
Restored session: Wed May 22 10:49:27 PDT 2024
 (clear; '/Applications/Splunk/bin/splunk' start || touch "/tmp/splunk_start_failed_13361"); rm "/tmp/splunk_start_running_16113" 
~$  (clear; '/Applications/Splunk/bin/splunk' start || touch "/tmp/splunk_start_failed_13361"); rm "/tmp/splunk_start_running_16113" 


Splunk> Map. Reduce. Recycle.

Checking prerequisites...
	Checking http port [8000]: open
	Checking mgmt port [8089]: open
	Checking appserver port [127.0.0.1:8065]: open
	Checking kvstore port [8191]: open
	Checking configuration... Done.
		Creating: /Applications/Splunk/var/lib/splunk
		Creating: /Applications/Splunk/var/run/splunk
		Creating: /Applications/Splunk/var/run/splunk/appserver/i18n
		Creating: /Applications/Splunk/var/run/splunk/appserver/modules/static/css
		Creating: /Applications/Splunk/var/run/splunk/upload
		Creating: /Applications/Splunk/var/run/splunk/search_telemetry
		Creating: /Applications/Splunk/var/run/splunk/search_log
		Creating: /Applications/Splunk/var/spool/splunk
		Creating: /Applications/Splunk/var/spool/dirmoncache
		Creating: /Applications/Splunk/var/lib/splunk/authDb
		Creating: /Applications/Splunk/var/lib/splunk/hashDb
New certs have been generated in '/Applications/Splunk/etc/auth'.
	Checking critical directories...	Done
	Checking indexes...
		Validated: _audit _configtracker _dsappevent _dsclient _dsphonehome _internal _introspection _metrics _metrics_rollup _telemetry _thefishbucket history main summary
	Done
	Checking filesystem compatibility...  Done
	Checking conf files for problems...
	Done
	Checking default conf files for edits...
	Validating installed files against hashes from '/Applications/Splunk/splunk-9.2.1-78803f08aabb-darwin-64-manifest'
	All installed files intact.
	Done
All preliminary checks passed.

Starting splunk server daemon (splunkd)...  
Generating a RSA private key
................+++++
.................................................................................................................................................................................................................................................................................................................................................................+++++
writing new private key to 'privKeySecure.pem'
-----
Signature ok
subject=/CN=JABELK-M-957F/O=SplunkUser
Getting CA Private Key
writing RSA key
PYTHONHTTPSVERIFY is set to 0 in splunk-launch.conf disabling certificate validation for the httplib and urllib libraries shipped with the embedded Python interpreter; must be set to "1" for increased security
Done


Waiting for web server at http://127.0.0.1:8000 to be available............... Done


If you get stuck, we're here to help.  
Look for answers here: http://docs.splunk.com

The Splunk web interface is at http://JABELK-M-957F:8000

~$ 

```

/Applications/Splunk/bin/splunk start



******************* other install



/Applications/Splunk/bin/splunk start

Last login: Wed May 22 09:36:29 on ttys001
~$ /Applications/Splunk/bin/splunk start
SPLUNK GENERAL TERMS

Last Updated: August 12, 2021

These Splunk General Terms ("General Terms") between Splunk Inc., a Delaware
corporation, with its principal place of business at 270 Brannan Street, San
Francisco, California 94107, U.S.A ("Splunk" or "we" or "us" or "our") and you
("Customer" or "you" or "your") apply to the purchase of licenses and
subscriptions for Splunk's Offerings. By clicking on the appropriate button,
or by downloading, installing, accessing or using the Offerings, you agree to
these General Terms. If you are entering into these General Terms on behalf of
Customer, you represent that you have the authority to bind Customer. If you
do not agree to these General Terms, or if you are not authorized to accept
the General Terms on behalf of the Customer, do not download, install, access,
or use any of the Offerings.

See the General Terms Definitions Exhibit attached for definitions of
capitalized terms not defined herein.

/Applications/Splunk/license-eula.txt

...
"Personnel" means any employee, consultant, contractor, or subcontractor of
Splunk.

"Splunk Preexisting IP" means, with respect to any C&I Services Materials, all
associated Splunk technology and all Intellectual Property Rights created or
acquired: (a) prior to the date of the Statement of Work that includes such
C&I Services Materials, or (b) after the date of such Statement of Work but
independently of the C&I Services provided under such Statement of Work.

"Statement of Work" means the statements of work and/or any and all applicable
Orders, that describe the specific services to be performed by Splunk,
including any materials and deliverables to be delivered by Splunk.
Do you agree with this license? [y/n]:

Do you agree with this license? [y/n]: y

This appears to be an upgrade of Splunk.
--------------------------------------------------------------------------------)

Splunk has detected an older version of Splunk installed on this machine. To
finish upgrading to the new version, Splunk's installer will automatically
update and alter your current configuration files. Deprecated configuration
files will be renamed with a .deprecated extension.

You can choose to preview the changes that will be made to your configuration
files before proceeding with the migration and upgrade:

If you want to migrate and upgrade without previewing the changes that will be
made to your existing configuration files, choose 'y'.
If you want to see what changes will be made before you proceed with the
upgrade, choose 'n'.


Perform migration and upgrade without previewing configuration changes? [y/n]



Starting splunk server daemon (splunkd)...
PYTHONHTTPSVERIFY is set to 0 in splunk-launch.conf disabling certificate validation for the httplib and urllib libraries shipped with the embedded Python interpreter; must be set to "1" for increased security
Done



Waiting for web server at http://127.0.0.1:8000 to be available................ Done


If you get stuck, we're here to help.
Look for answers here: http://docs.splunk.com

The Splunk web interface is at http://JABELK-M-957F:8000

~$



/Applications/Splunk/bin/splunk help

~$ /Applications/Splunk/bin/splunk help
WARNING: Server Certificate Hostname Validation is disabled. Please see server.conf/[sslConfig]/cliVerifyServerName for details.



Welcome to Splunk's Command Line Interface (CLI).

    Type these commands for more help:

        help [command]             type a command name to access its help page
        help [object]              type an object name to access its help page
        help [topic]               type a topic keyword to get help on a topic
        help commands              display a full list of CLI commands
        help clustering            commands that can be used to configure the clustering setup
        help shclustering          commands that can be used to configure the Search Head Cluster setup
        help control, controls     tools to start, stop, manage Splunk processes
        help datastore             manage Splunk's local filesystem use
        help distributed           manage distributed configurations such as
                                   data cloning, routing, and distributed search
        help forwarding            manage deployments
        help input, inputs         manage data inputs
        help licensing             manage licenses for your Splunk server
        help settings              manage settings for your Splunk server
        help simple, cheatsheet    display a list of common commands with syntax
        help tools                 tools to help your Splunk server
        help search                help with Splunk searches

    Universal Parameters:

        The following parameters are usable by any command. For more details on each parameter, type "help [parameter]".

Syntax:

	[command] [object] [-parameter <value> | <value>]... [-uri][-auth]

      app        specify the app or namespace to run the command; for search, defaults to
                 the Search app

      auth       specify login credentials to execute commands that require you to be logged in

      owner      specify the owner/user context associated with an object; if not specified,
                 defaults to the currently logged in user

      uri        execute a command on any specified Splunk server. Use the
                 format: <ip>:<port>

      Note: Both IPv4 and IPv6 formats are supported for specifying an IP address, for example:
      127.0.0.1:80 or "[2001:db8::1]:80". By default, splunkd listens on IPv4 only. To enable
      IPv6 support, refer to the instructions in:
      http://docs.splunk.com/Documentation/Splunk/latest/Admin/ConfigureSplunkforIPv6


Objects:

	None

Required Parameters:

	None

Optional Parameters:

	None

Examples:

	None

Type "help [command]" to get help with parameters for a specific command.

Complete documentation is available online at: http://docs.splunk.com/Documentation

~$


```
CISCOU-2034$ /Applications/Splunk/bin/splunk start
The splunk daemon (splunkd) is already running.


If you get stuck, we're here to help.
Look for answers here: http://docs.splunk.com

The Splunk web interface is at http://JABELK-M-957F:8000

CISCOU-2034$
```




****************** universal forwarder

https://www.splunk.com/en_us/download/universal-forwarder.html

m1 OS X
wget -O splunkforwarder-9.2.1-78803f08aabb-darwin-universal2.dmg "https://download.splunk.com/products/universalforwarder/releases/9.2.1/osx/splunkforwarder-9.2.1-78803f08aabb-darwin-universal2.dmg"

### setup forwarder after install 

```
Getting CA Private Key
writing RSA key
PYTHONHTTPSVERIFY is set to 0 in splunk-launch.conf disabling certificate validation for the httplib and urllib libraries shipped with the embedded Python interpreter; must be set to "1" for increased security
Done


Waiting for web server at http://127.0.0.1:8000 to be available............... Done


If you get stuck, we're here to help.  
Look for answers here: http://docs.splunk.com

The Splunk web interface is at http://JABELK-M-957F:8000

~$ 
  [Restored May 22, 2024 at 1:11:24 PM]
Last login: Wed May 22 10:49:36 on ttys006
Restored session: Wed May 22 10:50:19 PDT 2024
~$  (clear; '/Applications/SplunkForwarder/bin/splunk' ftr --accept-license || touch "/tmp/splunk_start_failed_31240"); rm "/tmp/splunk_start_running_7800" 


This appears to be your first time running this version of Splunk.

Splunk software must create an administrator account during startup. Otherwise, you cannot log in.
Create credentials for the administrator account.
Characters do not appear on the screen when you type in credentials.

Please enter an administrator username: 




```

pop up

```


✔  The installation was successful.

Click the "Splunk" icon on the Desktop to start and connect to Splunk.

To start Splunk manually, open a Terminal window and run the command: 
$ /Applications/Splunk/bin/splunk start

Documentation:
http://docs.splunk.com/Documentation/Splunk
```

```
Please enter an administrator username: admin
 
Password must contain at least:
   * 8 total printable ASCII character(s).
Please enter a new password: 
Please confirm new password: 
Empty passwords are not allowed.
Please enter a new password: 








  [Restored May 22, 2024 at 1:12:17 PM]
Last login: Wed May 22 13:11:24 on ttys006
Restored session: Wed May 22 13:12:08 PDT 2024
 (clear; '/Applications/SplunkForwarder/bin/splunk' start || touch "/tmp/splunk_start_failed_9106"); rm "/tmp/splunk_start_running_24454" 
~$  (clear; '/Applications/SplunkForwarder/bin/splunk' start || touch "/tmp/splunk_start_failed_9106"); rm "/tmp/splunk_start_running_24454" 


Splunk> Map. Reduce. Recycle.

Checking prerequisites...
	Checking mgmt port [8089]: not available
ERROR: mgmt port [8089] - port is already bound.  Splunk needs to use this port.
Would you like to change ports? [y/n]: 


















```

set port to 8095 since 8089 was used

# after restart

~$ splunkcmd show web-port
Web port: 8000
~$ splunkcmd status
splunkd is not running.
~$ splunkcmd start

Splunk> CSI: Logfiles.

Checking prerequisites...
	Checking http port [8000]: open
	Checking mgmt port [8089]: open
	Checking appserver port [127.0.0.1:8065]: open
	Checking kvstore port [8191]: open
	Checking configuration... Done.
	Checking critical directories...	Done
	Checking indexes...
		Validated: _audit _configtracker _dsappevent _dsclient _dsphonehome _internal _introspection _metrics _metrics_rollup _telemetry _thefishbucket history main summary
	Done
	Checking filesystem compatibility...  Done
	Checking conf files for problems...
	Done
	Checking default conf files for edits...
	Validating installed files against hashes from '/Applications/Splunk/splunk-9.2.1-78803f08aabb-darwin-64-manifest'
	All installed files intact.
	Done
All preliminary checks passed.

Starting splunk server daemon (splunkd)...
PYTHONHTTPSVERIFY is set to 0 in splunk-launch.conf disabling certificate validation for the httplib and urllib libraries shipped with the embedded Python interpreter; must be set to "1" for increased security
Done


Waiting for web server at http://127.0.0.1:8000 to be available............ Done


If you get stuck, we're here to help.
Look for answers here: http://docs.splunk.com

The Splunk web interface is at http://JABELK-M-957F:8000

~$