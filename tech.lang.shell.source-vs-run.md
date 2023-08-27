---
id: wnr8unyt9tb84ph46qqe0oj
title: Source Vs Run
desc: ''
updated: 1692985344313
created: 1692984952359
---

## TLDR
```shell
# Runs the hi.sh script within the parent process.
source /tmp/hi.sh

# Creates child process to run hi.sh script in.
/tmp/hi.sh
```

## Details
Lets say you have a script `/tmp/hi.sh`

Which has the following ($$ prints [[tech.ref.pid]])
```shell
echo "My PID: $$"
```

If you run it as 

```shell
/tmp/hi.sh
```

You will get PID that is different from parent process.

But if you run it as 
```shell
source /tmp/hi.sh
```
You will get the same PID as your parent process. 

## Example code:
```shell
echo 'echo pid in /tmp/hi.sh: $$' > /tmp/hi.sh
chmod +x /tmp/hi.sh

echo "PID of parent process is: $$"
echo "Running /tmp/hi.sh"
/tmp/hi.sh

echo "Source /tmp/hi.sh"
source /tmp/hi.sh
```