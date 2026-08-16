# junction0-recipe

OpenFactory recipe for building Junction0 Linux.

## What is Junction0?

Junction0 is a Rust-powered Linux distribution built on Alpine Linux. It features:

- **junction0-busd**: Unified system bus with crash recovery
- **junction0-pid**: Process unification watcher
- **junction0-res**: Intelligent resource manager
- **junction0-drv**: Containerized driver installer

## Building with OpenFactory

1. Go to [build.openfactory.tech](https://build.openfactory.tech)
2. Paste the contents of `junction0.json`
3. Click "Build"
4. Wait for the build to complete (~15-30 minutes)
5. Download the ISO
6. Boot in QEMU or on real hardware

## Testing the Build

```bash
# Boot in QEMU
qemu-system-x86_64 -cdrom junction0.iso -m 4G -smp 2

# Verify services
ssh junction0@localhost -p 2222
junction0-busd --status
junction0-pid --status
junction0-res --status
junction0-drv --status
```

## Architecture

```
Alpine Linux (musl, busybox)
├── systemd (PID 1)
├── junction0-busd (TCP:9553)
├── junction0-pid (process watcher)
├── junction0-res (resource monitor)
├── junction0-drv (driver isolator)
└── COSMIC Desktop (optional)
```

## License

MIT OR Apache-2.0
