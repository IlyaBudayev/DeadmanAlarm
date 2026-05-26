
### There are several ways to run it — choose the one that fits your use case.

### 1) The easiest way: Docker

If you want a demo mode without hardware:

```bash
docker pull ruvnet/wifi-densepose:latest
docker run -p 3000:3000 ruvnet/wifi-densepose:latest
```

Then open:

```text
http://localhost:3000
```

---

### 2) Run as a Python package

If you want to work with it from Python:

```bash
pip install ruview
# or
pip install wifi-densepose
```

If you also need the client libraries:

```bash
pip install "ruview[client]"
# or
pip install "wifi-densepose[client]"
```

---

### 3) Run from source code

If the project is already cloned locally:

#### Python version

```bash
pip install -e .
```

If it does not work from the project root, try the legacy v1 mode:

```bash
cd v1
pip install -e .
```

#### Rust version

The main Rust implementation is located in `v2/`:

```bash
cd v2
cargo test --workspace --no-default-features
```

If you only want to verify compilation of a specific crate:

```bash
cd v2
cargo check -p wifi-densepose-train --no-default-features
```

---

### 4) If you have ESP32 and need live sensing

Then you need to:

- flash the firmware,
- provision Wi-Fi,
- start the sensing server / application.

Something like this:

```bash
python -m esptool --chip esp32s3 --port COM9 --baud 460800 write_flash ...
python firmware/esp32-csi-node/provision.py --port COM9 --ssid "YourWiFi" --password "secret" --target-ip 192.168.1.20
```

---

