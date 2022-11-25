images_nt_header.md
===

可以分為兩大部分`FILE OPTION`、`OPTION OPTION`，mircosoft中的敘述的struct如下  
```c++
typedef struct _IMAGE_NT_HEADERS {
  DWORD                   Signature;
  IMAGE_FILE_HEADER       FileHeader;
  IMAGE_OPTIONAL_HEADER32 OptionalHeader;
} IMAGE_NT_HEADERS32, *PIMAGE_NT_HEADERS32;
```  
## Signature
  類似DOS_HEADER中的e_magic，其中NT_HEADER開頭的會是`PE\x00\x00`(4Bytes)。
  
## FILE OPTION

FILE OPTION中 mircosoft中所敘述的struct如下
```c++
typedef struct _IMAGE_FILE_HEADER {
  WORD  Machine;
  WORD  NumberOfSections;
  DWORD TimeDateStamp;
  DWORD PointerToSymbolTable;
  DWORD NumberOfSymbols;
  WORD  SizeOfOptionalHeader;
  WORD  Characteristics;
} IMAGE_FILE_HEADER, *PIMAGE_FILE_HEADER;
```
* Machine
  可執行的架構，機碼如mircosoft所述下圖  
  ![image](https://user-images.githubusercontent.com/67756786/203879135-f449d1ae-ccf9-4fce-a3f9-c9676457b25d.png)

* NumberOfSections  
  如字面上意思，說後面有多少個section
* TimeDateStamp
  編譯的時間
* PointerToSymbolTable
  目前理解為以棄用的選項
* NumberOfSymbols
  目前理解為已棄用的選項
* SizeOfOptionalHeader
  為後面option header的大小，通常為0xE0(32bits)或是0xF0(64bits)
* Characteristics
  敘述程式屬性，如mircosoft下圖:
  ![image](https://user-images.githubusercontent.com/67756786/203879436-c0803bc3-159f-4149-813a-488689f2e1bd.png)
## OPTION HEADER
OPTION HEADER，在mircosoft中的struct如下:
```c++
typedef struct _IMAGE_OPTIONAL_HEADER {
  WORD                 Magic;
  BYTE                 MajorLinkerVersion;
  BYTE                 MinorLinkerVersion;
  DWORD                SizeOfCode;
  DWORD                SizeOfInitializedData;
  DWORD                SizeOfUninitializedData;
  DWORD                AddressOfEntryPoint;
  DWORD                BaseOfCode;
  DWORD                BaseOfData;
  DWORD                ImageBase;
  DWORD                SectionAlignment;
  DWORD                FileAlignment;
  WORD                 MajorOperatingSystemVersion;
  WORD                 MinorOperatingSystemVersion;
  WORD                 MajorImageVersion;
  WORD                 MinorImageVersion;
  WORD                 MajorSubsystemVersion;
  WORD                 MinorSubsystemVersion;
  DWORD                Win32VersionValue;
  DWORD                SizeOfImage;
  DWORD                SizeOfHeaders;
  DWORD                CheckSum;
  WORD                 Subsystem;
  WORD                 DllCharacteristics;
  DWORD                SizeOfStackReserve;
  DWORD                SizeOfStackCommit;
  DWORD                SizeOfHeapReserve;
  DWORD                SizeOfHeapCommit;
  DWORD                LoaderFlags;
  DWORD                NumberOfRvaAndSizes;
  IMAGE_DATA_DIRECTORY DataDirectory[IMAGE_NUMBEROF_DIRECTORY_ENTRIES];
} IMAGE_OPTIONAL_HEADER32, *PIMAGE_OPTIONAL_HEADER32;
```
