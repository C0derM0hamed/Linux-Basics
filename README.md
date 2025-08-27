---

#  Linux Course Summary

This repository contains my notes and hands-on practice exercises from the ITI Linux course.
The content is organized by chapters, covering essential Linux commands and concepts.

---

## CH03 – File and Directory Basics

**Create directories and files**

```bash
mkdir project
cd project
mkdir src docs data
touch src/main.c docs/readme.txt data/input.txt
```

**Navigate between directories**

```bash
cd src
cd ..
cd docs
```

**List files with details**

```bash
ls -l
ls -lh
```

**File properties**

```bash
stat src/main.c
du -sh data/
df -h
```

**View file contents**

```bash
cat docs/readme.txt
less docs/readme.txt
head -n 5 data/input.txt
tail -n 5 data/input.txt
```

**File globbing**

```bash
ls data/*.txt
ls src/ma?.c
```

---

## CH04 – vi Editor

**Open and edit a file**

```bash
vi notes.txt
```

* Press `i` → insert mode
* Type your text
* Press `Esc :wq` → save and exit

**Copy / Cut / Paste**

* Copy: `yy`
* Cut: `dd`
* Paste: `p`

**Search and Replace**

```bash
/SearchWord
:%s/old/new/g
```

**Customization**

```bash
:set number
```

Make it permanent in `~/.vimrc`:

```bash
set number
syntax on
```

---

## CH05 – User and Group Administration

**Add user**

```bash
sudo useradd -m ali
sudo passwd ali
```

**Modify user**

```bash
sudo usermod -c "Project Manager" ali
```

**Add group**

```bash
sudo groupadd devs
sudo usermod -aG devs ali
```

**Switch active group**

```bash
newgrp devs
```

**Using sudo**

```bash
sudo apt update
sudo cat /etc/shadow
```

---

## CH06 – File Ownership & Permissions

**Change ownership**

```bash
sudo chown ali:devs project/
```

**Change permissions**

```bash
chmod 644 file.txt
chmod 755 script.sh
```

**Special permissions**

```bash
sudo chmod u+s script.sh   # SUID
sudo chmod g+s project/    # SGID
sudo chmod +t /shared      # Sticky bit
```

---

## CH07 – Shutdown & Virtual Consoles

**Switch to TTY**

```
Ctrl + Alt + F2
```

**Shutdown and reboot**

```bash
sudo shutdown -h now
sudo shutdown -r now
sudo reboot
```

---

## CH08 – Network & Initialization

**View network interfaces**

```bash
ip a
ping 8.8.8.8
```

**Alias**

```bash
alias ll='ls -lh'
```

Make it permanent:

```bash
echo "alias ll='ls -lh'" >> ~/.bashrc
```

---

## CH09 – Processes & Signals

**List processes**

```bash
ps aux
top
```

**Change priority**

```bash
nice -n 10 script.sh
renice -n 5 -p 1234
```

**Send signals**

```bash
kill -9 1234
kill -HUP 5678
```

---

## CH10 – Redirection & Piping

**Output redirection**

```bash
ls > files.txt
```

**Input redirection**

```bash
sort < files.txt
```

**Error redirection**

```bash
ls /nofile 2> error.txt
```

**Piping**

```bash
ls | grep ".txt"
```

**tee command**

```bash
ls | tee out.txt
```

---

## CH11 – Sort & Compare

**Word/line count**

```bash
wc -l file.txt
```

**Compare files**

```bash
diff file1.txt file2.txt
```

**Cut columns**

```bash
cut -d: -f1 /etc/passwd
```

**Search**

```bash
grep "root" /etc/passwd
```

**Sort**

```bash
sort file.txt
```

---

## CH12 – Inodes & Links

**Check inode**

```bash
ls -i file.txt
```

**Links**

```bash
ln -s file.txt link1   # Soft link
ln file.txt link2      # Hard link
```

**Find files**

```bash
find /etc -name "*.conf"
```

---

## CH13 – Compress & Archive

**Archive**

```bash
tar -cvf backup.tar project/
```

**Extract**

```bash
tar -xvf backup.tar
```

**Compress**

```bash
gzip file.txt
gunzip file.txt.gz
```

**tar with gzip**

```bash
tar -czvf backup.tar.gz project/
tar -xzvf backup.tar.gz
```

---
