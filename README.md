# Batch File Logging Guide (.bat)

This guide shows what kind of information can be written to a `.txt` file using a Windows batch (`.bat`) script.

---

## 📌 Overview
A batch file can write almost any command-line output into a text file.  
This is useful for logging, debugging, monitoring, and automation.

---

## 📝 Basic Syntax

```bat
command >> output.txt
````

* `>`  overwrites the file
* `>>` appends to the file
* `2>&1` redirects errors as well

---

## 📅 Date and Time

```bat
echo %date% %time% >> log.txt
```

Use case: execution logs, timestamps.

---

## 💻 System Information

### Computer Name

```bat
echo Computer: %COMPUTERNAME% >> log.txt
```

### Current User

```bat
echo User: %USERNAME% >> log.txt
```

### Windows Version

```bat
ver >> log.txt
```

---

## 🌐 Network Information

### IP Configuration

```bat
ipconfig >> log.txt
```

### Active Connections

```bat
netstat -an >> log.txt
```

### Ping & Traceroute

```bat
ping google.com >> log.txt
tracert google.com >> log.txt
```

---

## 📂 Files and Directories

### File List

```bat
dir >> files.txt
```

### Directory Tree

```bat
tree >> tree.txt
```

---

## 🧠 Running Processes

```bat
tasklist >> processes.txt
```

Filter a specific process:

```bat
tasklist | find "chrome" >> chrome.txt
```

---

## ⚙️ Command Output & Errors

Log standard output:

```bat
some_command >> output.txt
```

Log output **and** errors:

```bat
some_command >> output.txt 2>&1
```

---

## 🔍 Conditions and Checks

```bat
if exist test.txt echo File exists >> log.txt
```

```bat
if %errorlevel% neq 0 echo Error detected >> log.txt
```

---

## 🔁 Variables and Loops

```bat
set count=0
:loop
set /a count+=1
echo Iteration: %count% >> log.txt
timeout /t 1 > nul
goto loop
```

---

## 🧾 Custom Log Messages

```bat
echo Script started >> log.txt
echo Backup completed successfully >> log.txt
echo ERROR: Network unreachable >> log.txt
```

---

## ⚠️ Limitations

Batch files **cannot directly**:

* Read hardware temperatures
* Work with APIs or JSON
* Perform strong encryption

However, batch scripts **can call external tools** that output data to text files.

---

## 🧩 Example: Simple System Logger

```bat
@echo off
echo ===== START ===== >> log.txt
echo %date% %time% >> log.txt
echo User: %USERNAME% >> log.txt
ipconfig | find "IPv4" >> log.txt
ping google.com >> log.txt
echo ===== END ===== >> log.txt
```
