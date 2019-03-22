Shell-Magic für Anfänger

# touch
```shell
touch foo.txt # creates file or updates access and modification time
touch foo{1..10}.JPG
```
- mit -r kann ein anderes File referenziert werden, um dessen Zeiten zu verwenden, statt der aktuellen
- mit -d kann die Zeit direkt angegeben werden

# screen
```shell
screen -S long ./long_running_script.sh
```
- ctrl+a ctrl+d # detach
- screen -r [name] # reattach
- screen -ls # list screen sessions

# tmux
```shell
tmux new-session -s name  # create a new session with the identifier - here 'name'
tmux ls # list all active sessions
tmux attach -t name # attach to an active session identified by its 'name'
# detach from a session using [CTRL + B] + [D]
# create a new window inside the current session [CTRL + B] + [C]
tmux kill-server # kill the tmux server & all client instances
```

# jq
```shell
jq . example.json # pretty print
jq '.Inhaber | { Name, Vorname }' example.json
jq '{ "cardnumber": .Nummer, "issuer": .Herausgeber, "name": .Inhaber.Name, "lastname": .Inhaber.Name }' example.json
```

# sort && uniq && wc
```shell
echo "foo\nbar\nbar\nbaz\nbar"
echo "foo\nbar\nbar\nbaz\nbar" | sort
echo "foo\nbar\nbar\nbaz\nbar" | sort | uniq -c
echo "foo\nbar\nbar\nbaz\nbar" | wc -l
```

# for && while
```shell
for f in *.JPG; do mv $f ${f/.JPG/.jpg}; done
```

# convert
convert images

```shell
convert foo.png foo.jpg
convert old.png new.png  +append compare.png
```

# ssh{,-config}
```shell
ssh -p 2222 a128707@192.168.2.123
```

```shell
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

## mosh -> MObile SHell
- handels bad connections
- resumes shell-sessions, even in different networks
- shows typed characters without delay

## sshuttle
- can be used kind of like a VPN
- uses ssh-portforwarding
- only forwards TCP-Traffic
- only needs permissions to execute python on target system


# jobs (ctrl+z,&,fg)
```shell
./long_running_script.sh
<ctrl+z>
jobs
fg %1
```

# redirect outputs
### stdout -> Datei
```shell
programm > Datei.txt
```
### stderr -> Datei
```shell
programm 2> Datei.txt
```
### stdout UND stderr -> Datei
```shell
programm &> Datei.txt
```
### stdout -> stderr
```shell
programm 1>&2
```
### stderr -> stdout
```shell
programm 2>&1
```

# write files with echo
```shell
echo '#!/bin/sh' > script.sh
echo 'echo "Hello World"' >> script.sh
chmod +x script.sh && ./script.sh
```

# find
```shell
find . -name "*.jpg"
find . -mmin -5 # find files modified in the last 5 minutes
find . -ctime -1 # find files created in the last day
find . -atime +7 # find files last accessed more than a week ago

find ./src/ -name "*.java" -exec wc -l {} \; | sort # find all java-files, count number of lines and sort the result
```
- {+,-}{a,c,m}min für Zeit in Minuten (access, create, modified)
- {+,-}{a,c,m}time für Zeit in Tagen

# man/tldr
https://tldr.sh/

```shell
man find
tldr find
```

# grep
```shell
grep -E '([[:digit:]]{4}-){3}[[:digit:]]{4}' example.json
```

# netcat && socat
```shell
nc -l -p 8000 # listen on (tcp) port 8000
```

# curl && httpie
https://github.com/jakubroztocil/httpie

```shell
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

# alias
```shell
alias # prints all defined aliases
alias foo="ls -l" # defines an alias (only for current shell)
```