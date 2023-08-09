# check_log_tiny
Nagios plugin to check pattern in log file

# Install
$ cp check_log_tiny /usr/local/nagios/libexec
$ cd /usr/local/nagios
$ vi etc/objects/commands.cfg
----------------------------------------------------
...
define command {    
    command_name    check_log_tiny
    command_line    $USER1$/check_log_tiny -F $ARG1$ -q $ARG3$
}
...
----------------------------------------------------

$ vi etc/objects/servers/${YOUR_SERVER}.cfg
----------------------------------------------------
...
define service {
    use                     $TEMPLATE
    host_name               $YOUR_SERVER_IP
    service_description     CHECK VERY_IMPORTANT_LOG
    check_command           check_log_tiny!/var/log/${YOUR_LOG}.log!ERROR
}
...
----------------------------------------------------
