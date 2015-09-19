#Check for Stale Passwords

Version: *2.8*
<br />
Author: *William Stearns* - *wstearns@cloudpassage.com*


A ruby script that looks at all Halo-secured systems in a single portal account and reports on all server-local accounts whose passwords have not been changed in over M days (where M is specified on the command line).
 

##List of Files

* stale-passwords.rb --  The main Ruby check stale passwords script
* README.md

##Requirements and Dependencies

* The Ruby interpreter (>2.0) must be installed on the machine that executes the script.
* Access to wlslib.rb (A Ruby Library for accessing the CloudPassage API), available on GitHub here: https://github.com/cloudpassage/wlslib
* These Ruby gems are required:  oauth2, rest-client, json, date, and optparse. The following command will install all optional gems needed by the CloudPasssage API clients: 
```
sudo gem install oauth2 rest-client json public_suffix ip
```
* A read-only (preferred) or full access API key and secret , placed in /etc/halo-api-keys separated by a vertical pipe, like: aa00bb44|11111111222222223333333344444444 This file should be owned by the user that runs api scripts, mode 600. 
* *Developers only: If you're working with an alternate grid, put that grid's api hostname and port in the third column of the line:* aa00bb44|11111111222222223333333344444444|api.example.com:9999

##Usage

###*Installation* 
* Copy stale-passwords.rb and wlslib.rb to the same directory in your path. wlslib.rb will also be found if you copy it to any directory in your ruby library search path, which can be seen by running echo 'puts $:' | irb

###*Example Commands*

Show help text and parameters:
```
stale-passwords.rb -h
```

List all non-system accounts whose passwords have not been changed in the last 90 days:
```
stale-passwords.rb -m 90 -i ab45fe98 --nosys
```

As above, but only show the actual lines, no headers:
```
stale-passwords.rb -m 90 -i ab45fe98 --nosys 2>/dev/null
```

As above, but pipe output only to another script:
```
stale-passwords.rb -m 90 -i ab45fe98 --nosys | process_stale_passwords
```

Save to disk for later processing, such as importing into a database or spreadsheet
```
stale-passwords.rb -m 90 -i ab45fe98 --nosys >stale-password-accounts.csv
````

##License

Copyright (c) 2013, CloudPassage, Inc.
All rights reserved.

Redistribution and use in source and binary forms, with or without modification,
are permitted provided that the following conditions are met:
    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in the
      documentation and/or other materials provided with the distribution.
    * Neither the name of the CloudPassage, Inc. nor the
      names of its contributors may be used to endorse or promote products
      derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL CLOUDPASSAGE, INC. BE LIABLE FOR ANY DIRECT,
INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED ANDON ANY THEORY OF
LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE
OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF
ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

 
 
<!---
#CPTAGS:community-unsupported audit integration
-->
