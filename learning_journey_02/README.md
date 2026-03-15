# Learning Journey 02 — Development & Practice notes

This directory contains notes and walkthroughs for setting up a Linux kernel
development environment, QEMU-based test environment, and performing 2 different 
practice runs. All of this documention is to prepare someone for actual Linux
kernel development.  Read these in the order below: first the environment setup, 
then QEMU test environment, then the 2 practice runs. 

Files
-
- [Linux Native Based Development Environment Setup](LINUX_NATIVE_BASED_DEV_ENV.md):
  - Purpose: step-by-step host setup for building and contributing to the
    Linux kernel (Rocky Linux 9 in the author's case).
  - Key contents: resources/links used, assumptions, package installation
    checks, how to retrieve the kernel source, creating tags, copying an
    existing kernel config, using `scripts/config` to clear signed-key
    settings, `make olddefconfig`, build/install steps (`make -j$(nproc)`,
    `sudo make modules_install install`), and GRUB configuration tips for
    Rocky 9 (timeout/menu visibility).
  - Additional: detailed vim/email/git-send-email setup (including using a
    Google App Password), testing send-email, and a typical workflow for
    preparing and emailing patches.

- [QEMU Virtual Machine (VM) Test Environment Creation](QEMU_VM_BASED_TESTING.md):
  - Purpose: Create a QEMU-based virtual machine test environment for safely booting
    and testing custom-built Linux kernels outside of the host system.
  - Key contents: installing QEMU/KVM virtualization tools (qemu-kvm, qemu-img,
    virt-install, virt-manager), verifying CPU virtualization support (lscpu, /proc/cpuinfo,
    lsmod kvm), creating a QCOW2 disk image (qemu-img create), launching a VM with
    qemu-system-x86_64, installing Rocky Linux via VNC (tigervnc, vncviewer), rebuilding
    initramfs with virtio drivers (dracut), and booting a custom kernel in the VM with kernel
    parameters for debugging (console=ttyS0, nokaslr, earlyprintk, rd.shell).
    
- [Practice Run #1](PRACTICE_RUN_1.md):
  - Purpose: a concise checklist for a practice change and verification loop.
  - Key contents: git basics (branching, fetching, rebasing), how to
    configure the kernel for a ticket (copying /boot config, setting
    CONFIG_LOCALVERSION), example of making a temporary change (example
    printk added to `drivers/bluetooth/btusb.c`), build/install steps,
    how to verify with `dmesg`, and how to revert the practice change
    (`git reset --hard HEAD`).

- [Practice Run #2](PRACTICE_RUN_2.md):
  - Purpose: GDB Debugging in Linux native environment against Linux kernel
    in guest QEMU VM.  Second practice run of building and installing a custom
    Linux kernel, focusing on using GDB to debug and validate changes made to
    kernel source code.
  - Key contents: using gdb for kernel debugging, compiling kernel with debug
    symbols (CONFIG_DEBUG_INFO), running kernel under qemu with -s -S for debugger
    attachment, connecting gdb to the kernel (target remote), inspecting stack
    traces and variables, and using debugging to diagnose practice kernel source c
    ode changes.
    
How to use these notes
-
- Step 1: Follow the steps in [Linux Native Based Development Environment Setup](LINUX_NATIVE_BASED_DEV_ENV.md)
  to prepare your Linux native kernel development environment and verify email/git tooling.
- Step 2: Follow the steps in [QEMU Virtual Machine (VM) Based Testing](QEMU_VM_BASED_TESTING.md)
  to prepare your QEMU/VM kernel  test environment.
- Step 3: Use [Practice Run #1](PRACTICE_RUN_1.md) to make a
  small, reversible change and exercise the build/send/test loop.
- Step 4: Use [Practice Run #2](PRACTICE_RUN_2.md) to understand process of using GDB against
  Linux kernel in QEMU VM.
  
## Questions / Support

Technical support is available when coffee is being supplied.

If you’d like to move forward, please [buy me a coffee](https://buymeacoffee.com/wg21908) and send me an email!
