# Linux Command-Line Practice

This repository focuses on using core Linux command-line tools to inspect system information and process CSV datasets.

---

## 📌 Objectives

- Using the following commands:
  - `cut`
  - `sort`
  - `uniq -c`
  - `grep`
- Practice navigating the filesystem and analyzing text data.

---

## 📦 Preparation

To download the dataset (NYC Taxi Data for April 2019) from Google Drive, we use the [`gdown`](https://github.com/wkentaro/gdown) command.

### Install dependencies
```bash
# Install pip
sudo apt install python3-pip

# Install gdown
sudo pip install gdown
```

## 📦 Download the Dataset

```bash
gdown 18oi_OAsRnI8YA0xtQ5smcJsL7lHI-2x0
```

## 📝 Tasks

1. Find the home directory path.

    Use the $HOME environment variable.

```bash
echo $HOME
```



2. Find which files under /proc/ contain memory and CPU information.

```bash
ls /proc | grep mem   # Memory-related files
ls /proc | grep cpu   # CPU-related files
```



3.  Identify the file under /etc/ that contains the OS version.

```bash
ls /etc | grep release
```


## 🔍 Use of Regular Expressions

This task also demonstrates the use of **regular expressions (regex)** to filter and extract specific patterns from datasets.

In the NYC Taxi Data analysis task, the following command was used for NYC Taxi Data Analysis: Look for most Popular Pickup Locations.

```bash
grep '^.*,"2019-04-02' 2019-04.csv | cut -d',' -f8 | sort | uniq -c | sort -nr | head -n 3
```

## 📄 Notes
- All commands were executed in a **UNIX/Linux environment**.
- The dataset (NYC Taxi data) is **not included** in the repository due to file size.
- Regular expressions were used to filter rows by specific dates for analysis.
- This README serves both as documentation and as a reproducible guide for running the same analyses.