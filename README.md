# Automated Chess with Computer Vision

This project controls a physical automated chessboard using a Raspberry Pi and a camera. It utilizes the OpenCV library to analyze the state of the board in real-time and a Flask web server to display the processed view for debugging purposes.

## Prerequisites

- A Raspberry Pi (tested on Zero 2 W) with Raspberry Pi OS Lite (64-bit).
- A Raspberry Pi camera, correctly connected.
- An internet connection.
- Python 3 and `pip` installed.

## Installation

These instructions will guide you through setting up the project environment from scratch on a new Raspberry Pi or a new SD card.

1. **Install System Dependencies**
   First, we need to update the system and install the essential packages needed to clone the repository (`git`) and to build the Python libraries (`build-essential`, `cmake`,    FFmpeg libraries, etc.).
   ```bash
   sudo apt update
   sudo apt full-upgrade -y # Realiza una actualización completa del sistema y dependencias
   sudo apt install -y git build-essential cmake pkg-config libavformat-dev libavcodec-dev libavutil-dev libswscale-dev libavdevice-dev libcap-dev python3-dev
   sudo apt install -y python3-libcamera python3-kms++
   sudo apt autoremove -y # Limpia paquetes no necesarios
   sudo apt clean
   ```
   After these commands, it's a good practice to reboot:

   ```bash
   sudo reboot
   ```

3.  **Clone the Repository**
    Open a terminal and clone this repository into your preferred directory (e.g., `/home/pi`).

    ```bash
    git clone https://github.com/antxia29/chess.git
    cd chess
    ```

4.  **Create the Virtual Environment**
    It is highly recommended to use a virtual environment to isolate the project's dependencies.

    ```bash
    python3 -m venv --system-site-packages chess
    ```
    *(This will create a folder named `chess` containing a clean copy of Python, and include the libraries installed out of it)*.

5.  **Activate the Virtual Environment**
    Whenever you want to work on the project, you need to activate the environment.

    ```bash
    source chess/bin/activate
    ```
    *(You will notice your terminal prompt changes to show `(chess)` at the beginning)*.

6.  **Install Dependencies**
    
    ```bash
    pip install --upgrade pip
    pip install picamera2 opencv-python flask numpy
    ```

You're all set! The environment is ready to go.

## Usage

To start the main program, which launches the web server and the camera analysis:

1.  Make sure the virtual environment is activated (`source chess/bin/activate`).
2.  Run the server script:
    ```bash
    python servidor_analisis.py
    ```
3.  The program will indicate that the server is running. To see the processed image, open a web browser on a computer on the same network and navigate to:
    `http://<RASPBERRY_PI_IP>:8000`

    *(You can find your Pi's IP address with the command `hostname -I`)*.
