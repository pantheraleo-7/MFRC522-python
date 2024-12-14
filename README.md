# mfrc522

A python library to read/write RFID tags via the budget MFRC522 RFID module.

This code was published in relation to a [blog post](https://pimylifeup.com/raspberry-pi-rfid-rc522/) and you can find out more about how to hook up your MFRC reader to a Raspberry Pi there.

## Installation

The package is available on PyPI:
```shell
pip install mfrc522
```

To build from source - clone this repository and run the setup script inside the top level directory:
```shell
git clone https://github.com/pimylifeup/MFRC522-python
cd MFRC522-python
python setup.py install
```

## Example Code

To read from a tag:

```python
import time

from mfrc522 import SimpleMFRC522


reader = SimpleMFRC522()

try:
    while True:
        id, text = reader.read()
        print(f"{id =}\n{text =}")
        time.sleep(5)
finally:
    reader.cleanup()
```

To write to a tag:

```python
import time

from mfrc522 import SimpleMFRC522


reader = SimpleMFRC522()

try:
    while True:
        data = input("Enter the data to write and then place the tag: ")
        id, text = reader.write(data)
        print(f"{id =}\n{text =}")
        time.sleep(5)
finally:
    reader.cleanup()
```
