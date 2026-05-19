# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis

```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat disk.dd
```


### File Listing
```bash
fls disk.dd
```


### File Recovery
```bash
icat disk.dd 11 > recovered_file.txt
```
- Recovers the file associated with inode 11.
 

## SAMPLE WORKFLOW (Windows)
```bash
# Step 1: View partitions
mmls.exe C:\forensics\disk.dd

# Step 2: View file system details
fsstat.exe -o 2048 C:\forensics\disk.dd

# Step 3: List files
fls.exe -r -o 2048 C:\forensics\disk.dd

# Step 4: Recover a file
icat.exe -o 2048 C:\forensics\disk.dd 6 > C:\forensics\image.jpg
```
## OUTPUT:
**Disk Structure Analysis Results**

**Create Disk**

<img width="539" height="183" alt="image" src="https://github.com/user-attachments/assets/92186254-780a-4cae-8a9f-e6e1dae21c3b" />


**File System Metadata**


<img width="932" height="768" alt="WhatsApp Image 2026-05-19 at 2 01 03 PM" src="https://github.com/user-attachments/assets/c1b09b17-1798-478c-8c77-64abcfa4c069" />


**File Listing**


<img width="614" height="79" alt="image" src="https://github.com/user-attachments/assets/288b2b23-2a49-4ec9-bb9d-7fbddedd84e4" />



**File Recovery**


 <img width="478" height="348" alt="image" src="https://github.com/user-attachments/assets/724eaa30-5ce9-4a04-92d3-90a0f7d792cc" />
 
## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
