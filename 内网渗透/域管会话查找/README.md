use:
~~~bash
net group "Domain Controllers" /domain > "Domain Controllers.txt" && net group "Domain admins" /domain > "Domain admins.txt" && FOR /F %i in ("Domain Controllers.txt") do @echo [+] Querying DC %i && @netsess -h %i 2>null >sessions.txt && FOR /F %a in ("Domain admins") DO @type sessions.txt | @findstr /I %a
~~~
