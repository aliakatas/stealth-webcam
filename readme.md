# Raspberry Pi Zero W 2 – Camera Web Stream

This project demonstrates how to expose a Raspberry Pi Zero W 2 camera feed through a simple **Flask web server**, making the live video accessible via a web browser on your local network (or remotely with proper networking setup).

---

## Features

* Live MJPEG video streaming via Flask
* Built using **Picamera2** and **libcamera**
* Lightweight: designed for Raspberry Pi Zero W 2
* Customizable backend (Flask + OpenCV)

---

## Prerequisites

* Raspberry Pi Zero W 2 running Raspberry Pi OS Bookworm (64-bit recommended)
* Camera module enabled (`raspi-config` → Interfaces → Camera)
* Python 3.11+

---

## Installation

### 1. Update your system

```bash
sudo apt update && sudo apt full-upgrade
```

### 2. Install camera libraries

```bash
sudo apt install -y libcamera-apps libcap-dev
```

### 3. Create and activate a Python virtual environment

```bash
python3 -m venv --system-site-packages venv
source venv/bin/activate
pip install --upgrade pip
```

### 4. Install Python dependencies

You can either install from the provided `requirements.txt`:

```bash
pip install -r requirements.txt
```

Or manually install the necessary packages:

```bash
pip install flask picamera2 opencv-python-headless
```
Then export/update the `requirements.txt` file:
```bash
pip freeze >> requirements.txt
```

---

## Usage

1. Start the Flask server:

   ```bash
   python3 app.py
   ```

2. Open a browser on your local network and navigate to:

   ```
   http://<raspberrypi-ip>:5000
   ```

3. You should now see the live video feed from your Raspberry Pi camera. 🎥

---

## Notes

* For best performance on the Pi Zero W 2, avoid using full `opencv-python`; use `opencv-python-headless`.
* If you want to access the feed remotely, you’ll need to configure **port forwarding** or use a **reverse proxy** with HTTPS (e.g., Traefik, Nginx).
* Tested on **Raspberry Pi OS Bookworm (64-bit)** with `python3-libcamera` and `python3-kms++` installed system-wide.
* The original code and idea can be found at [instructables](https://www.instructables.com/Raspberry-Zero-Cam-With-Webserver/) and [joejackson3/webcam Github](https://github.com/joejackson3/webcam).

---

## License

This project is released under the MIT License. See [LICENSE](LICENSE) for details.
