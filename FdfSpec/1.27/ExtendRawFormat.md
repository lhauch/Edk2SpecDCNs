DCN


### Summary

1. Extend the RAW format to support multiple binary files.


## 3.6 [FV] Sections

**Prototype**

```ini
<type3>     ::= <TS> "FILE" <MTS> "RAW" <Eq> <NamedGuidOrPcd>
                <Options2>

...

<Options2>  ::= [<Use>] [<FileOpts>] <MTS>
                "{" [<EOL>]
~~                    {<Filename>} {<SectionData>} <TS>~~
>                   {<Filename>} {<FileList>} {<SectionData>} <TS>
                "}" [<EOL>]
>
> <FileList> ::= [<FfsAlignment>] <NormalFile>
```


**Examples**

> ```ini
FILE RAW = 197DB236-F856-4924-90F8-CDF12FB975F3 {
$(OUTPUT_DIRECTORY)/$(TARGET)_$(TOOL_CHAIN_TAG)/$PLATFORM_ARCH)/File.bin
}
```
> ```ini
FILE RAW = 197DB236-F856-4924-90F8-CDF12FB975F3 {
  Align=16 $(PLATFORM_PACKAGE)/Binaries/File1.pdb
  Align=16 $(PLATFORM_PACKAGE)/Binaries/File1.pdb
  Align=16 $(PLATFORM_PACKAGE)/Binaries/File1.pdb
}
```
