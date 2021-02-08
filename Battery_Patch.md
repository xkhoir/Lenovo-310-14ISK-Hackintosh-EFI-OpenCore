# Patching Battery Lenovo Ideapad 310 14ISK on DSDT :

Do not do this patch, if your battery percentage is working well.

## FIX 16 BIT REGISTERS :

| 16 Bit Registers | 
| ----------- |
| B1SN,   16, |
| B1DV,   16, | 
| B1DC,   16, | 
| B1FC,   16, | 

### Apply patch on DSDT with MaciAsl :
```
into device label EC0 code_regex B1SN,\s+16, replace_matched begin BSN0,8,BSN1,8, end;
into device label EC0 code_regex B1DV,\s+16, replace_matched begin BDV0,8,BDV1,8, end;
into device label EC0 code_regex B1DC,\s+16, replace_matched begin BDC0,8,BDC1,8, end;
into device label EC0 code_regex B1FC,\s+16, replace_matched begin BFC0,8,BFC1,8, end;
```

### Then apply this :
```
into method label B1B2 remove_entry;
into definitionblock code_regex . insert
begin
Method (B1B2, 2, NotSerialized) { Return(Or(Arg0, ShiftLeft(Arg1, 8))) }\n
end;
```

### Then apply this B1B2 method :
```
B1B2(\_SB.PCI0.LPCB.EC0.BDC0,\_SB.PCI0.LPCB.EC0.BDC1)
B1B2(\_SB.PCI0.LPCB.EC0.BFC0,\_SB.PCI0.LPCB.EC0.BFC1)
B1B2(\_SB.PCI0.LPCB.EC0.BDV0,\_SB.PCI0.LPCB.EC0.BDV1)
B1B2(\_SB.PCI0.LPCB.EC0.BSN0,\_SB.PCI0.LPCB.EC0.BSN1)
```

## FIX LARGER than 32 BIT REGISTERS  :

| LARGER than 32 BIT Registers| 
| ----------- |
| FWBT,   64, |
| SMDA,   256, | 
| BMN0,   72, | 
| BDN0,   64, | 

### Apply patch on DSDT with MaciAsl :
```
into device label EC0 code_regex (FWBT,)\s+(64) replace_matched begin FWBX,%2,//%1%2 end;
into device label EC0 code_regex (SMDA,)\s+(256) replace_matched begin SMDX,%2,//%1%2 end;
into device label EC0 code_regex (BMN0,)\s+(72) replace_matched begin BMNX,%2,//%1%2 end;
into device label EC0 code_regex (BDN0,)\s+(64) replace_matched begin BDNX,%2,//%1%2 end;
```

### Then apply this :
```
FWBT -  \_SB.PCI0.LPCB.EC0.RECB(0X14,64)
SMDA -  \_SB.PCI0.LPCB.EC0.RECB(0X64,256)
BMN0 -  \_SB.PCI0.LPCB.EC0.RECB(0X8F,72)
BDN0 -  \_SB.PCI0.LPCB.EC0.RECB(0X98,64)
```

### Then apply this Standart B1B2 method for Larger than 32 BIT Registers :
```
into method label B1B2 remove_entry;
into definitionblock code_regex . insert
begin
Method (\B1B2, 2, NotSerialized)\n
{\n
ShiftLeft (Arg1, 8, Local0)\n
Or (Arg0, Local0, Local0)\n
Return (Local0)\n
}\n
end;
```

### Next patch and apply this "Standard utility methods to read/write buffers from/to EC"
```
into device label EC0 insert
begin
Method (RE1B, 1, NotSerialized)\n
{\n
OperationRegion(ERAM, EmbeddedControl, Arg0, 1)\n
Field(ERAM, ByteAcc, NoLock, Preserve) { BYTE, 8 }\n
Return(BYTE)\n
}\n
Method (RECB, 2, Serialized)\n
{\n
ShiftRight(Arg1, 3, Arg1)\n
Name(TEMP, Buffer(Arg1) { })\n
Add(Arg0, Arg1, Arg1)\n
Store(0, Local0)\n
While (LLess(Arg0, Arg1))\n
{
	Store(RE1B(Arg0), Index(TEMP, Local0))\n
	Increment(Arg0)\n
	Increment(Local0)\n
}\n
Return(TEMP)\n
}\n
end;

into device label EC0 insert
begin
Method (WE1B, 2, NotSerialized)\n
{\n
   OperationRegion(ERAM, EmbeddedControl, Arg0, 1)\n
   Field(ERAM, ByteAcc, NoLock, Preserve) { BYTE, 8 }\n
   Store(Arg1, BYTE)\n
}\n
Method (WECB, 3, Serialized)\n
{\n
   ShiftRight(Arg1, 3, Arg1)\n
   Name(TEMP, Buffer(Arg1) { })\n
   Store(Arg2, TEMP)\n
   Add(Arg0, Arg1, Arg1)\n
   Store(0, Local0)\n
   While (LLess(Arg0, Arg1))\n
   {\n
       WE1B(Arg0, DerefOf(Index(TEMP, Local0)))\n
       Increment(Arg0)\n
       Increment(Local0)\n
   }\n
}\n
end;
```
### Then save with .aml format and restart the laptop. When the boot picker select nvram and enter
