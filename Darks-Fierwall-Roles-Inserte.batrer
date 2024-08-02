@echo off
setlocal enabledelayedexpansion

:choose_action
echo #
echo ###########################################
echo ## DarkSmite's Fierwall Roles Inserterer ##
echo ###########################################
echo #
echo Do you want to add or remove firewall rules?
set /p ACTION=Enter A for Add or R for Remove: 
if /i "%ACTION%"=="A" goto add_rules
if /i "%ACTION%"=="R" goto remove_rules
echo Invalid choice. Please enter A for Add or R for Remove.
goto choose_action

:add_rules
:ask_rule_name
set /p NAME=Enter the rule name: 
if "%NAME%"=="" goto ask_rule_name

:ask_inbound_tcp
set /p IN_TCP_PORT=Enter the inbound TCP port number (or press Enter to skip): 
if not "%IN_TCP_PORT%"=="" (
    echo Allowing TCP port %IN_TCP_PORT% for inbound connections
    netsh advfirewall firewall add rule name="%NAME% TCP Inbound" protocol=TCP dir=in localport=%IN_TCP_PORT% action=allow
)

:ask_inbound_udp
set /p IN_UDP_PORT=Enter the inbound UDP port number (or press Enter to skip): 
if not "%IN_UDP_PORT%"=="" (
    echo Allowing UDP port %IN_UDP_PORT% for inbound connections
    netsh advfirewall firewall add rule name="%NAME% UDP Inbound" protocol=UDP dir=in localport=%IN_UDP_PORT% action=allow
)

:ask_outbound_tcp
set /p OUT_TCP_PORT=Enter the outbound TCP port number (or press Enter to skip): 
if not "%OUT_TCP_PORT%"=="" (
    echo Allowing TCP port %OUT_TCP_PORT% for outbound connections
    netsh advfirewall firewall add rule name="%NAME% TCP Outbound" protocol=TCP dir=out localport=%OUT_TCP_PORT% action=allow
)

:ask_outbound_udp
set /p OUT_UDP_PORT=Enter the outbound UDP port number (or press Enter to skip): 
if not "%OUT_UDP_PORT%"=="" (
    echo Allowing UDP port %OUT_UDP_PORT% for outbound connections
    netsh advfirewall firewall add rule name="%NAME% UDP Outbound" protocol=UDP dir=out localport=%OUT_UDP_PORT% action=allow
)

echo Firewall rules added successfully.
pause
goto end

:remove_rules
:ask_rule_name_remove
set /p NAME=Enter the rule name: 
if "%NAME%"=="" goto ask_rule_name_remove

:ask_inbound_tcp_remove
set /p IN_TCP_PORT=Enter the inbound TCP port number to remove (or press Enter to skip): 
if not "%IN_TCP_PORT%"=="" (
    echo Removing TCP port %IN_TCP_PORT% for inbound connections
    netsh advfirewall firewall delete rule name="%NAME% TCP Inbound" protocol=TCP dir=in localport=%IN_TCP_PORT%
)

:ask_inbound_udp_remove
set /p IN_UDP_PORT=Enter the inbound UDP port number to remove (or press Enter to skip): 
if not "%IN_UDP_PORT%"=="" (
    echo Removing UDP port %IN_UDP_PORT% for inbound connections
    netsh advfirewall firewall delete rule name="%NAME% UDP Inbound" protocol=UDP dir=in localport=%IN_UDP_PORT%
)

:ask_outbound_tcp_remove
set /p OUT_TCP_PORT=Enter the outbound TCP port number to remove (or press Enter to skip): 
if not "%OUT_TCP_PORT%"=="" (
    echo Removing TCP port %OUT_TCP_PORT% for outbound connections
    netsh advfirewall firewall delete rule name="%NAME% TCP Outbound" protocol=TCP dir=out localport=%OUT_TCP_PORT%
)

:ask_outbound_udp_remove
set /p OUT_UDP_PORT=Enter the outbound UDP port number to remove (or press Enter to skip): 
if not "%OUT_UDP_PORT%"=="" (
    echo Removing UDP port %OUT_UDP_PORT% for outbound connections
    netsh advfirewall firewall delete rule name="%NAME% UDP Outbound" protocol=UDP dir=out localport=%OUT_UDP_PORT%
)

echo Firewall rules removed successfully.
pause

:end
