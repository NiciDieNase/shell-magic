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

# ssh{,-config} && sshuttle && mosh
```
```

# jobs (ctrl+z,&,fg)
```
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

# curl && httpie
```
```

# netcat && socat
```
```
