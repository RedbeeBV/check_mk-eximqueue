# check_mk-eximqueue
Check used for and by check_mk in order to monitor exim queue count

I happily built on to Fabian Peters' created work and thank him for giving to the community.
( http://fabianpeter.de/monitoring/exim-mailqueue-check-for-check_mk/ )


## Installation Guide
- switch user to the user that runs the site (omd sites)
- Copy the eximqueue-1.0.mkp over to your OMD server (scp, or otherwise just curl it/git clone it)
- Install it using the check_mk package manager (cmk -P install PACK.mkp, where PACK is eximqueue-1.0.mkp )
 - Verify that it installed the eximqueue check in /omd/sites/YOURSITEHERE/var/check_mk/packages and that `cmk -L|grep eximqueue` is there.

- On the clients you want to monitor you need to copy the mk_exim over to the library path exim uses. (Version dependant, can be read out using `check_mk_agent|grep LocalDirectory` on the CLI of the client. Usually it is something like /usr/share/check-mk-agent/local )
- Reindex the machine on the monitoring server (cmk -I or cmk -II $hostnamehere) to activate the monitoring and get it to pop up in the webinterface.
