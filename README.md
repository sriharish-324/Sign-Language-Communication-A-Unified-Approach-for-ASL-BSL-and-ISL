# Sign Language Communication: A Unified Approach for ASL, BSL, and ISL

This project aims to create a unified approach for American Sign Language (ASL), British Sign Language (BSL), and Indian Sign Language (ISL) using [Mediapipe](https://mediapipe.dev/), a popular library for building applications with human pose models.

## Installation

### Method 1: Using Default Python 3.6.9

The Jetson device comes with Python 3.6.9 by default. You can install Mediapipe 0.8.3 using the following command:

```bash
pip install https://files.pythonhosted.org/packages/12/74/f55fc21266c08c304f05a409ba388c50f94fb52ef0f99100bb60287c4d91/mediapipe-0.8.3-cp36-cp36m-manylinux2014_x86_64.whl
### Method 2: Change Python 3.6.9 to Python 3.8

```bash
sudo apt update
sudo apt install python3.8
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1
sudo apt install python-pip
pip install mediapipe