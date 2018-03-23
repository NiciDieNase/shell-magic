```
echo shell-{tipps,magic}
```

# touch
```
touch foo.txt # creates file or updates access and modification time
```

# screen
```
screen -S long ./long_running_script.sh
```
ctrl+a ctrl+d # detach
screen -r [name] # reattach
screen -ls # list screen sessions

# jq
```
jq . example.json # pretty print
jq '.Inhaber | { Name, Vorname }' example.json
jq '{ "cardnumber": .Nummer, "issuer": .Herausgeber, "name": .Inhaber.Name, "lastname": .Inhaber.Name }' example.json
```

# sort && uniq && wc
```
echo "foo\nbar\nbar\nbaz\nbar"
echo "foo\nbar\nbar\nbaz\nbar" | sort
echo "foo\nbar\nbar\nbaz\nbar" | sort | uniq -c
echo "foo\nbar\nbar\nbaz\nbar" | wc -l
```

# for && while
```
for f in *.JPG; do mv $f ${f/.JPG/.jpg}; done
```

# convert
```
convert foo.png foo.jpg
convert old.png new.png  +append compare.png
```

# ssh{,-config}
```
ssh -p 2222 a128707@192.168.2.123
```
```
# only use specified keys
IdentitiesOnly yes

# use sockets
Host *
     ControlMaster auto
     ControlPath ~/.ssh/socket-%r@%h:%p

# config our server
Host braindump-server
     Hostname 192.168.2.123
     User a128707
     Port 2222
     IdentityFile ~/.ssh/arconsis
```

# mosh -> MObile SHell
- handels bad connections
- resumes shell-sessions, even in different networks
- shows typed characters without delay

# sshuttle
- can be used kind of like a VPN
- uses ssh-portforwarding
- only needs permissions to execute python on target system


# jobs (ctrl+z,&,fg)
```
./long_running_script.sh
<ctrl+z>
jobs
fg %1
```

# redirect outputs
## stdout -> Datei umleiten
```
programm > Datei.txt
```
## stderr -> Datei umleiten
```
programm 2> Datei.txt
```
## stdout UND stderr -> Datei umleiten
```
programm &> Datei.txt
```
## stdout -> stderr
```
programm 1>&2
```
## stderr -> stdout
```
programm 2>&1
```

# write files with echo
```
echo '#!/bin/sh' > script.sh
echo 'echo "Hello World"' >> script.sh
chmod +x script.sh && ./script.sh
```

# find
```
find . -name "*.jpg"
```

# man/tldr
```
man find
tldr find
```

# grep
```
grep ':' example.json
```

# netcat && socat
```
nc -l -p 8000 # listen on (tcp) port 8000
```

# curl && httpie
https://github.com/jakubroztocil/httpie
```
curl -s -H "Content-Type: application/json" \
	-XPOST http://localhost:8000 \
	-H 'Header: Value'
	--data '{"username":"YOUR.USERNAME","password":"YOUR.PASSWORD"}'

http POST :8000 \
	'Header: Value' \
	'username=YOUR.USERNAME' \
	'password=YOUR.PASSWORD'
```
Different Separators -> Different Type
- : HTTP Headers
- == URL-Parameters
- = JSON or Form-Data fields