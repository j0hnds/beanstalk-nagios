# beanstalk-nagios

This project is an implementation of a 'command' that can
be called by Nagios to pull statistics on your beanstalkd server
via SNMP.

## Installation

The guts of this project is a single Python script, which should be
placed in the appropriate location on your Nagios server. In our
case that would be the following directory:

    /usr/lib64/nagios/plugins/third-party

## Usage

There's no point in recreating the built-in help for the script. Just
do the following to see the help message:

    [dsieh@sb ~]$ /usr/lib64/nagios/plugins/third-party/check_beanstalk.py --help
    usage: check_beanstalk.py [-h] [-a AUTHPROTOCOL] [-A AUTHPASSWORD]
                              [-C COMMUNITY] [-l SECLEVEL] [-p PORT]
                              [--ready-critical READY_CRITICAL]
                              [--ready-warning READY_WARNING] [-t TIMEOUT]
                              [--timeouts-critical TIMEOUTS_CRITICAL]
                              [--timeouts-warning TIMEOUTS_WARNING] [-u SECNAME]
                              [-v VERSION] [-V]
                              [--workers-critical WORKERS_CRITICAL]
                              [--workers-warning WORKERS_WARNING]
                              [-x PRIVPROTOCOL] [-X PRIVPASSWORD]
                              hostname

    USAGE


    positional arguments:
      hostname              Specify the host name of the SNMP agent.

    optional arguments:
      -h, --help            show this help message and exit
      -a AUTHPROTOCOL       Set the default authentication protocol for SNMPv3
                            (MD5 or SHA).
      -A AUTHPASSWORD       Set the SNMPv3 authentication protocol password.
      -C COMMUNITY, --community COMMUNITY
                            SNMP Community String to use.(Default: public)
      -l SECLEVEL           Set the SNMPv3 security level,
                            (noAuthNoPriv|authNoPriv|authPriv) (Default:
                            noAuthNoPriv)
      -p PORT, --port PORT  Set the SNMP port to be connected to (Default:161).
      --ready-critical READY_CRITICAL
                            Critical threshold for the number of current jobs
                            ready
      --ready-warning READY_WARNING
                            Warning threshold for the number of current jobs ready
      -t TIMEOUT, --timeout TIMEOUT
                            Set the timeout for the program to run (Default: 10
                            seconds)
      --timeouts-critical TIMEOUTS_CRITICAL
                            Critical threshold for the number of jobs timing out
      --timeouts-warning TIMEOUTS_WARNING
                            Warning threshold for number of jobs timing out
      -u SECNAME            Set the SNMPv3 security name (user name).
      -v VERSION            Specify the SNMP version (1, 2, 3) Default: 3
      -V, --verbose         Give verbose output (Default: False
      --workers-critical WORKERS_CRITICAL
                            Critical threshold for the number of workers running
      --workers-warning WORKERS_WARNING
                            Warning threshold for the number of workers running
      -x PRIVPROTOCOL       Set the SNMPv3 privacy protocol (DES or AES).
      -X PRIVPASSWORD       Set the SNMPv3 privacy pass phrase.

## Packaging for RPM

If you're thinking of packaging this little beauty up in
an RPM, you'll want to create a source package first. Here
are the steps you can use to create the source package.

1. Make sure the version of the package is correct in the VERSION file. This file is used by the packager.
2. Run the package.sh script. There are no arguments, just run it.

The source tar-ball will be created in the base directory of this
project: beanstalk_nagios-&lt;version&gt;.tar.bz2.

That's all.

# Copyright

Copyright (c) 2016 Dave Sieh

See LICENSE.txt for details.
