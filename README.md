# xv6-unix-on-windows

This is a guide on how to build and boot xv6 on Windows.

## Resources

- **GitHub:** [https://github.com/mit-pdos/xv6-riscv](https://github.com/mit-pdos/xv6-riscv)
- **MIT Course:** [https://pdos.csail.mit.edu/6.1810/2024/schedule.html](https://pdos.csail.mit.edu/6.1810/2024/schedule.html)
- **QEMU for Windows:** [https://www.qemu.org/download/#windows](https://www.qemu.org/download/#windows)

## Build Dependencies

```bash
sudo apt install binutils-riscv64-linux-gnu qemu-system-misc gcc-riscv64-linux-gnu
```

## Build Command

```bash
make qemu
```

## Run on Windows

```bash
qemu-system-riscv64 -machine virt -bios none -kernel kernel -nographic -global virtio-mmio.force-legacy=false -drive file=fs.img,if=none,format=raw,id=x0 -device virtio-blk-device,drive=x0,bus=virtio-mmio-bus.0
```

After running the command, you should see the xv6 kernel booting:

```
xv6 kernel is booting

hart 2 starting
hart 1 starting
init: starting sh
$
```

If you type `ls` at the prompt, you should see output similar to the following:

```
$ ls
.              1 1 1024
..             1 1 1024
README         2 2 2227
xargstest.sh   2 3 93
cat            2 4 32864
echo           2 5 31720
forktest       2 6 15856
grep           2 7 36240
init           2 8 32216
kill           2 9 31680
ln             2 10 31504
ls             2 11 34808
mkdir          2 12 31736
rm             2 13 31720
sh             2 14 54168
stressfs       2 15 32608
usertests      2 16 178800
grind          2 17 47528
wc             2 18 33816
zombie         2 19 31080
console        3 20 0
```



