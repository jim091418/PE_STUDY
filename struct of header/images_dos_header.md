images_dos_header
===
microsoft struct IMAGE_DOS_HEADER

```
protected struct IMAGE_DOS_HEADER
        {
            public ushort e_cblp;
            public ushort e_cp;
            public ushort e_cparhdr;
            public ushort e_crlc;
            public ushort e_cs;
            public ushort e_csum;
            public ushort e_ip;
            public uint e_lfanew;
            public ushort e_lfarlc;
            public ushort e_magic;
            public ushort e_maxalloc;
            public ushort e_minalloc;
            public ushort e_oemid;
            public ushort e_oeminfo;
            public ushort e_ovno;
            public ushort[] e_res;
            public ushort[] e_res2;
            public ushort e_sp;
            public ushort e_ss;
        }
```

目前理解為有用的是e_magic、e_lfanew  
* e_magic為開頭MZ(必定)
* e_lfanew為NT_HEADER的開頭位址  

