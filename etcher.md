### Etcher烧录后，如何还原启动盘

```
diskpart

list disk

select disk 3

clean

create partition primary

list primary

select partition 1

format quick
```

