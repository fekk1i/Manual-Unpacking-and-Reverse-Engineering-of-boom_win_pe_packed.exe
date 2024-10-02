# Manual Unpacking and Reverse Engineering of boom_win_pe_packed.exe

This project documents the manual unpacking and reverse engineering process of a UPX-packed executable named `boom_win_pe_packed.exe`. The goal is to demonstrate the identification of packing, manual unpacking, and recovery of a functional unpacked executable using advanced debugging tools.

## Project Overview:
The executable `boom_win_pe_packed.exe` was initially packed with UPX, a common packing technique used to compress executables and obfuscate them from analysis. This project details how to unpack the executable manually without relying on the automated UPX unpacking tool.

## Methodology:
- **PEStudio**: Used to analyze the file structure and identify packing indicators.
- **DiE (Detect It Easy)**: Performed entropy analysis to confirm high compression in the packed file.
- **x64dbg with Scylla plugin**: Used for dynamic analysis, finding the Original Entry Point (OEP), reconstructing the Import Address Table (IAT), and dumping the memory to recover a clean unpacked executable.
  
## Tools Used:
- **PEStudio**: For static analysis of the file structure and to verify packing.
- **Detect It Easy (DiE)**: For entropy checking and further confirmation of the packed file.
- **x64dbg**: Debugger used for dynamic analysis and stepping through the executable.
- **Scylla Plugin**: Used to reconstruct the Import Address Table (IAT) and repair the dumped executable.

## Unpacking Process:
1. **Initial Identification**: PEStudio and DiE confirmed the file was packed with UPX by analyzing sections and entropy.
2. **Manual Unpacking**:
   - Loaded the executable into x64dbg and identified the entry point.
   - Set a breakpoint, ran the executable, and used Scylla plugin to reconstruct the Import Address Table.
   - Dumped the process memory and repaired the dumped file using Scylla's Fix Dump feature.
3. **Verification**:
   - Verified the unpacked file by comparing its size and scanning it again with PEStudio to ensure no UPX traces remained.
   - Performed SHA-256 hash checks to validate file integrity post-unpacking.

## Results:
The project successfully unpacked the `boom_win_pe_packed.exe` file, creating a functional unpacked version (`boom_win_pe_packed_dump_SCY.exe`). The unpacking process was verified by entropy checks, import table analysis, and file size comparison.

## Conclusion:
The manual unpacking of `boom_win_pe_packed.exe` demonstrated a complete workflow for handling packed executables, from initial analysis to IAT reconstruction and validation of the final unpacked binary. The process highlights the importance of understanding executable structures and the use of debugging tools in reverse engineering.

---

### Author:
- **Ali Abdelhamid El Fekki**
  - Email: Aa2100274@tkh.edu.eg
