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
fsstat -o 2048 disk.dd
```
### File Listing
```bash
fls -o 2048 disk.dd
```
### File Recovery
```bash
icat -o 2048 disk.dd 4 > recovered_file.txt
```
- Recovers the file associated with inode 4.
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
<img width="275" height="87" alt="image" src="https://github.com/user-attachments/assets/5e0d32f6-c3fb-4c8e-9bc4-4e261e79f98f" />
`

<img width="496" height="94" alt="image" src="https://github.com/user-attachments/assets/ac7359f0-1ad5-41c4-8e87-f46931c8d04e" />

<img width="548" height="236" alt="image" src="https://github.com/user-attachments/assets/0f56d67a-2514-4651-8f02-555f0907e7b0" />

<img width="713" height="915" alt="image" src="https://github.com/user-attachments/assets/9af8af2a-8438-4d8d-aa65-9285ce3e11a4" />

<img width="1083" height="105" alt="image" src="https://github.com/user-attachments/assets/c7f80add-d0b4-456b-8510-477da91516c5" />

<img width="996" height="842" alt="image" src="https://github.com/user-attachments/assets/411e3bb9-ebd8-4c88-8f8e-d7db649a9df6" />

<img width="814" height="292" alt="image" src="https://github.com/user-attachments/assets/cf550c3b-45a6-4a32-963a-600188a861ea" />

<img width="628" height="343" alt="image" src="https://github.com/user-attachments/assets/d1e859c3-94e1-49f8-8e16-7ec7ef29edd3" />

## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
