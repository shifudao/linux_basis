# 总结

自测题

* 试描述以下命令帮助的含义

```
lvcreate  [--addtag  Tag]  [--alloc  AllocationPolicy]  [-a|--activate  [a|e|l]{y|n}]  [-A|--autobackup {y|n}] [-C|--contiguous {y|n}] [-d|--debug] [-h|-?|--help] [--noudevsync] [--ignoremonitoring]
[--monitor {y|n}] [-i|--stripes Stripes [-I|--stripesize StripeSize]] {[-l|--extents LogicalExtentsNumber[%{VG|PVS|FREE}] | -L|--size LogicalVolumeSize[bBsSkKmMgGtTpPeE]] | -V|--virtualsize Virtual‐
Size[bBsSkKmMgGtTpPeE]} [-M|--persistent {y|n}] [--minor minor] [-m|--mirrors Mirrors [--nosync] [--mirrorlog {disk|core|mirrored} | --corelog] [-R|--regionsize MirrorLogRegionSize]] [-n|--name Log‐
icalVolume{Name|Path}] [-p|--permission {r|rw}] [-r|--readahead {ReadAheadSectors|auto|none}] [-t|--test] [-T|--thin [-c|--chunksize ChunkSize] [--discards {ignore|nopassdown|passdown}] [--poolmeta‐
datasize  MetadataSize[bBsSkKmMgG]]]  [--thinpool  ThinPoolLogicalVolume{Name|Path}]  [--type SegmentType] [-v|--verbose] [-Z|--zero {y|n}] VolumeGroup{Name|Path}[/ThinPoolLogicalVolumeName] [Physi‐
calVolumePath[:PE[-PE]]...]

lvcreate [-l|--extents LogicalExtentsNumber[%{VG|FREE|ORIGIN}] | -L|--size LogicalVolumeSize[bBsSkKmMgGtTpPeE]]  [-c|--chunksize  ChunkSize]  [--noudevsync]  [--ignoremonitoring]  [--monitor  {y|n}]
[-n|--name SnapshotLogicalVolume{Name|Path}] -s|--snapshot {[VolumeGroup{Name|Path}/]OriginalLogicalVolumeName -V|--virtualsize VirtualSize[bBsSkKmMgGtTpPeE]}
```

* 用通配符匹配目录下所有隐藏文件

* 匹配``syslog.n.gz``和``syslog.n.xz``(n是1-50任意数字)
