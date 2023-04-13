# pyulog

A lightweight python to parse log files from ArduPilot vehicles based on the [MavLink](https://mavlink.io/) protocol. It is built on top of [pymavlink](https://github.com/ArduPilot/pymavlink) and uses [NumPy](https://numpy.org/) under the hood to vectorize messages.

## Installation

Installation with pip:

```bash
pip install pyulog
```

or via Poetry

Installation from source:

```bash
poetry add pyulog
```

## Development

Install the package in editable mode:

```bash
pip install -e .
```

Pymavlog is built using [Poetry](https://github.com/python-poetry/poetry), so make sure to have it in your local development environment

```bash
pip install poetry
```

## Testing

```bash
poetry run pytest tests --cov pymavlog
```

or

```bash
make tests
```

## Usage

The main class of the package is `MavLog`, which parses the log file messages in-memory as NumPy arrays. You can parse a file like:

```python
from pymavlog import MavLog


filepath = "foo/bar.bin"
mavlog = MavLog("foo/bar.bin")
mavlog.parse()
```

and access the messages like:

```python
imu_messages = mavlog.get("IMU")
```

and do some calculations, for example calculating the average value:

```python
avg_gyr_x = imu_messages["GyrX"].mean()
```

More info in the docs (TBD).
