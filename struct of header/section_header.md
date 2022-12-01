section_header.md
===

微軟中定義的section header struct如下
```c++
typedef struct _IMAGE_SECTION_HEADER {
  BYTE  Name[IMAGE_SIZEOF_SHORT_NAME];
  union {
    DWORD PhysicalAddress;
    DWORD VirtualSize;
  } Misc;
  DWORD VirtualAddress;
  DWORD SizeOfRawData;
  DWORD PointerToRawData;
  DWORD PointerToRelocations;
  DWORD PointerToLinenumbers;
  WORD  NumberOfRelocations;
  WORD  NumberOfLinenumbers;
  DWORD Characteristics;
} IMAGE_SECTION_HEADER, *PIMAGE_SECTION_HEADER;
```
當中常用到的資訊如下:
* Name  
這個section header的名字，常見的有.text、.data、.idata、.rdata...etc
* VirtualSize  
決定要分配記憶體大小
* VirtualAddress  
決定寫進記憶體的哪裡位址
* SizeOfRawData  
這個資料的大小
* PointerToRawData  
進入資料的位址
* Characteristics  
決定接下來的資料權限(可讀、可寫、可執行)
