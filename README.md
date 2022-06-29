# forte_on_kos
An example of runing Eclipse 4diac forte on KOS CE


Init source:


cd forte_on_kos

git submodule update --init --recursive


Compile docker image

as usual :)


Setup development enviroment:

docker run -it -v .:/workspace --device /dev/net/tun:/dev/net/tun --privileged --rm getting-started bash


Compile and run in Docker:
./cross-build.sh


Expected rezult:

[ROFS] Files: 5, size: 22130688 (0x0151b000).
[ROFS] File #00: einit            - size:   614960 (0x00096230)
[ROFS] File #01: Forte            - size: 17381064 (0x010936c8)
[ROFS] File #02: Env              - size:   607860 (0x00094674)
[ROFS] File #03: NetVfs           - size:  3012040 (0x002df5c8)
[ROFS] File #04: ksm.module       - size:   498288 (0x00079a70)
[AU..] Starting core audit...
[VLOG] Virtual logging subsystem initialized.
[VMM ] Virtual Memory Manager service initialized.
[IO  ] I/O subsystem successfully initialized.
[FS  ] File System Manager successfully initialized.
[XHCI] XHCIDBG service initialized.
[CM  ] Connection Manager successfully initialized.
[KSM ] Module: 'ksm.module' loaded.
[KSM ] Audit log created.
[KSM ] Module: 'ksm.module' initialized.
[KSM ] Server: 'kl.core.Core' executed.
[KSM ] Security system successfully initialized.
[INIT] Starting 'Einit' ...
[INIT] Starting system worker.
lan9118: error: PHY read reg 9
lan9118: error: PHY read reg 10
[2022-06-28T08:51:04.227][Info][NS] Can't connect with Name Server.
[vfs.NetVfs] Failed to initialize VFS backends
[2022-06-28T08:51:04.598][Info][NS] Can't connect with Name Server.
INFO: T#1671732896: FORTE try start....
INFO: T#1696262624: FORTE is up and running
INFO: T#1698970000: Using provided bootfile location set in CMake: forte.fboot
INFO: T#1699811536: Boot file forte.fboot could not be opened. Skipping...



