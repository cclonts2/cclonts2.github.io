---
title: API
tags:
---

# Summary
This API documentation provides details about the message structure, status codes, and message types used in the system. It includes tables for Message ID, Status, Message Types, Temperature Sensor (Message Type 1), and Fan Control (Message Type 2).

## Message ID

The Message ID table defines the unique identifiers for system members and their associated addresses. Each member is assigned a specific ID and address for communication within the system.

| Member        | System            | ID  | Address |
|---------------|-------------------|-----|---------|
| Cade Clonts   | Wifi              | 1   | 0x01    |
| Jahmel        | Human Interface   | 2   | 0x02    |
| Dan           | Fan Control       | 3   | 0x03    |
| Broadcast     | All               | 88  | 0x58    |

### Status

The Status table defines the status codes used in the system to indicate the state of a message or operation.

| Status | Code  |
|--------|-------|
| Normal | 0x00  |
| Error  | 0x01  |

## Message Types

The Message Types table categorizes the types of messages and their associated status or code ranges.

| Category         | Status/Code | Address |
|------------------|-------------|----|
| Temp Data        | 0 to 255  | 0x10 |
| Fan Control      | 0-125       | 0x20 |

---

### Temperature Sensor (Message Type 1)

The Temperature Sensor table defines the structure of messages for temperature data. Each byte in the message is mapped to a specific variable, with details about its type, range, and example values.

| Byte | Variable Name | Variable Type | Min Value | Max Value | Example Value |
|---|------------------|--------------|-----------|-----------|--------------|
| 1 | prefix_1        | uint8_t      | 0x41      | 0x41      | 0x41         |
| 2 | prefix_2        | uint8_t      | 0x5a      | 0x5a      | 0x5a         |
| 3 | source_id       | uint8_t      | 3         | 3         | 0x03         |
| 4 | destination_id  | uint8_t      | 1         | 88        | 0x58         |
| 5 | message_type    | uint8_t      | 0x10      | 0x10      | 0x10         |
| 6 | temp_id         | uint8_t      | 0         | 255       | 0x01         |
| 7 | status          | uint8_t      | 0         | 1         | 0x01         |
| 8 | temp_data_integer | uint8_t    | 0       | 255       | 25           |
| 9 | temp_data_fraction | uint8_t   | 0         | 99        | 50           |
| 10-62 | Unused       | uint8_t     | 0x00       | 0x00     | 0x00         |
| 63 | suffix_1        | uint8_t      | 0x59      | 0x59      | 0x59         |
| 64 | suffix_2        | uint8_t      | 0x42      | 0x42      | 0x42         |


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>

<details>
    <summary>Inverted</summary>
    <table>
        <tr>
            <th></th>
            <th>Byte 1</th>
            <th>Byte 2</th>
            <th>Byte 3</th>
            <th>Byte 4</th>
            <th>Byte 5</th>
            <th>Byte 6</th>
            <th>Byte 7</th>
            <th>Byte 8</th>
            <th>Byte 9</th>
            <th>Byte 10-62</th>
            <th>Byte 63</th>
            <th>Byte 64</th>
        </tr>
        <tr>
            <td><strong>Variable Name</strong></td>
            <td>prefix_1</td>
            <td>prefix_2</td>
            <td>source_id</td>
            <td>destination_id</td>
            <td>message_type</td>
            <td>temp_id</td>
            <td>status</td>
            <td>temp_data_integer</td>
            <td>temp_data_fraction</td>
            <td>Unused</td>
            <td>suffix_1</td>
            <td>suffix_2</td>
        </tr>
        <tr>
            <td><strong>Variable Type</strong></td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
        </tr>
        <tr>
            <td><strong>Min Value</strong></td>
            <td>0x41</td>
            <td>0x5a</td>
            <td>3</td>
            <td>1</td>
            <td>0x10</td>
            <td>1</td>
            <td>0</td>
            <td>0</td>
            <td>0</td>
            <td>0x00</td>
            <td>0x59</td>
            <td>0x42</td>
        </tr>
        <tr>
            <td><strong>Max Value</strong></td>
            <td>0x41</td>
            <td>0x5a</td>
            <td>3</td>
            <td>88</td>
            <td>0x10</td>
            <td>255</td>
            <td>1</td>
            <td>155</td>
            <td>99</td>
            <td>0x00</td>
            <td>0x59</td>
            <td>0x42</td>
        </tr>
        <tr>
            <td><strong>Example Value</strong></td>
            <td>0x41</td>
            <td>0x5a</td>
            <td>0x03</td>
            <td>0x58</td>
            <td>0x10</td>
            <td>0x01</td>
            <td>0x01</td>
            <td>25</td>
            <td>50</td>
            <td>0x00</td>
            <td>0x59</td>
            <td>0x42</td>
        </tr>
    </table>

</details>

</body>
</html>

---

### Fan Control (Message Type 2)

The Fan Control table defines the structure of messages for controlling fan speed. Each byte in the message is mapped to a specific variable, with details about its type, range, and example values.

| Byte  | Variable Name   | Variable Type | Min Value | Max Value | Example Value |
|-------|-----------------|--------------|-----------|-----------|--------------|
| 1     | prefix_1        | uint8_t      | 0x41      | 0x41      | 0x41         |
| 2     | prefix_2        | uint8_t      | 0x5a      | 0x5a      | 0x5a         |
| 3     | source_id       | uint8_t      | 1         | 2         | 0x01         |
| 4     | destination_id  | uint8_t      | 4         | 4         | 0x04         |
| 5     | message_type    | uint8_t      | 0x20      | 0x20      | 0x20         |
| 6     | fan_id          | uint8_t      | 1         | 255       | 0x02         |
| 7     | status          | uint8_t      | 0         | 1         | 0x01         |
| 8     | fan_speed_data  | uint8_t      | 0         | 3         | 0x02         |
| 9     | fan_speed_set   | uint8_t      | 0         | 3         | 0x01         |
| 10-62 | Unused          | uint8_t      | 0x00      | 0x00      | 0x00         |
| 63    | suffix_1        | uint8_t      | 0x59      | 0x59      | 0x59         |
| 64    | suffix_2        | uint8_t      | 0x42      | 0x42      | 0x42         |

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>

<details>
    <summary>Inverted</summary>
    <table>
        <tr>
            <th></th>
            <th>Byte 1</th>
            <th>Byte 2</th>
            <th>Byte 3</th>
            <th>Byte 4</th>
            <th>Byte 5</th>
            <th>Byte 6</th>
            <th>Byte 7</th>
            <th>Byte 8</th>
            <th>Byte 9</th>
            <th>Byte 10-62</th>
            <th>Byte 63</th>
            <th>Byte 64</th>
        </tr>
        <tr>
            <td><strong>Variable Name</strong></td>
            <td>prefix_1</td>
            <td>prefix_2</td>
            <td>source_id</td>
            <td>destination_id</td>
            <td>message_type</td>
            <td>fan_id</td>
            <td>status</td>
            <td>fan_speed_data</td>
            <td>fan_speed_set</td>
            <td>Unused</td>
            <td>suffix_1</td>
            <td>suffix_2</td>
        </tr>
        <tr>
            <td><strong>Variable Type</strong></td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
            <td>uint8_t</td>
        </tr>
        <tr>
            <td><strong>Min Value</strong></td>
            <td>0x41</td>
            <td>0x5a</td>
            <td>1</td>
            <td>4</td>
            <td>0x20</td>
            <td>1</td>
            <td>0</td>
            <td>0</td>
            <td>0</td>
            <td>0x00</td>
            <td>0x59</td>
            <td>0x42</td>
        </tr>
        <tr>
            <td><strong>Max Value</strong></td>
            <td>0x41</td>
            <td>0x5a</td>
            <td>2</td>
            <td>4</td>
            <td>0x20</td>
            <td>255</td>
            <td>1</td>
            <td>3</td>
            <td>3</td>
            <td>0x00</td>
            <td>0x59</td>
            <td>0x42</td>
        </tr>
        <tr>
            <td><strong>Example Value</strong></td>
            <td>0x41</td>
            <td>0x5a</td>
            <td>0x01</td>
            <td>0x04</td>
            <td>0x20</td>
            <td>0x02</td>
            <td>0x01</td>
            <td>0x02</td>
            <td>0x01</td>
            <td>0x00</td>
            <td>0x59</td>
            <td>0x42</td>
        </tr>
    </table>
</details>
</body>
</html>

## Code

Functionality
- Can recieve temperature data and fan speed set messages and display them on a web server.
- Can take inputs of 0, 1, 2 or 3 from a web server and send it as a set fan speed message to the fan system.
- When receiving a message with it's own destination id will blink an LED
- When the temperature goes above the threshold 34°C a message to fan system to set to 3 (high fan speed) will be sent automatically.
- When the temperature dips below the threshold 34°C a message to fan system to set to 2 (medium fan speed) will be sent automatically.
- Pass messages where the destination id is not it's own.
- Ignore messages that source id is it's own.
- Ignore messages that are not within preset id's for source and destinations, do not begin with AZ and end with YB

<details>
    <summary>ESP32 Code</summary>
        <pre><code>
# Derived from: 
# * https://github.com/peterhinch/micropython-async/blob/master/v3/as_demos/auart.py
# * https://github.com/tve/mqboard/blob/master/mqtt_async/hello-world.py
# * https://github.com/peterhinch/micropython-mqtt
# * https://github.com/embedded-systems-design/external_pycopy-lib
# * https://www.adafruit.com/product/2651
# * https://www.bosch-sensortec.com/products/environmental-sensors/pressure-sensors/pressure-sensors-bmp280-1.html
# * https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bmp280-ds001.pdf
# * https://github.com/vitally/BMP280  
# * https://github.com/micropython-IMU/micropython-bmp180

import ssl

from mqtt_as.mqtt_as import MQTTClient
from mqtt_as.mqtt_local import wifi_led, blue_led, config
import uasyncio as asyncio
from machine import UART
from machine import Pin
from machine import I2C
import bmp280
import time
from config import *

MAX_MESSAGE_LEN = 64
MAX_SEND_RATE = 5
MAXTX = 5

# Define team IDs and broadcast ID
team = [b'\x01', b'\x02', b'\x03']  # Cade, Jahmel, Dan
my_id = b'\x01'  # Set this device's ID (e.g., Cade)
broadcast = b'\x58'  # Broadcast ID

uart = UART(2, 9600,tx=21,rx=14)
uart.init(9600, bits=8, parity=None, stop=1,flow=0) # init with given parameters

led1 = Pin(12, Pin.OUT)

debug_button = Pin(15, Pin.IN, Pin.PULL_UP)

# Set up I2C (GPIO21=SDA, GPIO22=SCL)
i2c = I2C(0, scl=Pin(2), sda=Pin(3), freq=100000)

# Scan I2C bus to confirm connection
print("I2C devices found:", i2c.scan())  # Should include [118] for 0x76

# Initialize BMP280 (default address 0x76)
sensor = bmp280.BMP280(i2c)

# Optional: set oversampling for better accuracy
# sensor.use_case(bmp280.CASE_WEATHER)

# Initialize LED on pin 14
led2 = Pin(14, Pin.OUT)

def send_message(source, destination, message_type, sensor_id=None, status=None, temp_data=None, fan_id=None, fan_speed_data=None, fan_speed_set=None):
    """
    Sends a message with the specified structure.
    """
    if source not in team:
        print(f"ESP: Invalid source '{source}'")
        return
    if destination not in team and destination != broadcast:
        print(f"ESP: Invalid destination '{destination}'")
        return

    # Construct the message
    message = bytearray(64)
    message[0] = 65  # prefix_1 (0x41 in decimal)
    message[1] = 90  # prefix_2 (0x5A in decimal)
    message[2] = source[0]  # source_id
    message[3] = destination[0]  # destination_id
    message[4] = message_type  # message_type

    if message_type == 16:  # Temp Data (0x10 in decimal)
        if not (-40 <= temp_data <= 155):
            print("ESP: Temperature data out of range (-40 to 155)")
            return
        message[5] = sensor_id  # sensor_id
        message[6] = status  # status
        message[7] = int(temp_data)  # temp_data as a single value

    elif message_type == 32:  # Fan Control (0x20 in decimal)
        if not (1 <= fan_id <= 255):
            print("ESP: Fan ID out of range (1 to 255)")
            return
        if status not in [0, 1]:  # 0x00 and 0x01 in decimal
            print("ESP: Invalid fan status (must be 0 or 1)")
            return
        if not (0 <= fan_speed_data <= 3):
            print("ESP: Fan speed data out of range (0 to 3)")
            return
        if not (0 <= fan_speed_set <= 3):
            print("ESP: Fan speed set value out of range (0 to 3)")
            return
        message[5] = fan_id  # fan_id
        message[6] = status  # status
        message[7] = fan_speed_data  # fan_speed_data
        message[8] = fan_speed_set  # fan_speed_set

    else:
        print("ESP: Invalid message type")
        return

    # Unused bytes are already initialized to 0 by default
    message[62] = 89  # suffix_1 (0x59 in decimal)
    message[63] = 66  # suffix_2 (0x42 in decimal)

    print(f"ESP: Sending message: {message}")
    uart.write(message)


def handle_message(message):
    """
    Handles an incoming message by parsing its structure.
    Processes messages intended for this device, broadcast messages, and passes on others.
    """
    if len(message) != 64:
        print("ESP: Invalid message length")
        return

    # Parse the message
    prefix_1 = message[0]
    prefix_2 = message[1]
    source_id = message[2]
    destination_id = message[3]
    message_type = message[4]
    suffix_1 = message[62]
    suffix_2 = message[63]

    # Validate prefixes and suffixes
    if prefix_1 != 0x41 or prefix_2 != 0x5A or suffix_1 != 0x59 or suffix_2 != 0x42:
        print("ESP: Invalid message format")
        return

    # Ignore messages from myself
    if source_id == my_id[0]:
        print("ESP: Ignoring message from myself")
        return

    # Process messages intended for this device
    if destination_id == my_id[0]:
        print("ESP: Message is for me")
        
        # Blink LED on pin 14
        led2.value(1)  # Turn on LED
        time.sleep(0.1)  # Short delay
        led2.value(0)  # Turn off LED

        # Handle specific message types (e.g., Temp Data, Fan Control)
        process_message_by_type(message_type, message)

    # Process broadcast messages
    elif destination_id == broadcast[0]:
        if source_id != my_id[0]:
            print("ESP: Handling broadcast message from another device")
            # Handle specific message types (e.g., Temp Data, Fan Control)
            process_message_by_type(message_type, message)

            # Pass the message along
            print("ESP: Passing along broadcast message")
            uart.write(message)
        else:
            print("ESP: Ignoring broadcast message from myself")

    # Pass on messages intended for others
    elif destination_id != my_id[0] and destination_id != broadcast[0]:
        print("ESP: Passing on message for another device")
        uart.write(message)

    else:
        print("ESP: Unsupported message type or invalid destination")


async def process_message_by_type(message_type, message):
    """
    Processes a message based on its type.
    """
    if message_type == 16:  # Temp Data (0x10 in decimal)
        sensor_id = message[5]
        status = message[6]
        temp_data = message[7]

        if not (-40 <= temp_data <= 155):
            print("ESP: Received temperature data out of range (-40 to 155)")
            return

        print(f"ESP: Handling Temp Data message")
        print(f"Sensor ID: {sensor_id}, Status: {status}, Temperature: {temp_data} °C")

    elif message_type == 32:  # Fan Control
        fan_id = message[5]
        status = message[6]
        fan_speed_data = message[7]
        fan_speed_set = message[8]

        if not (1 <= fan_id <= 255):
            print("ESP: Received invalid fan ID (1 to 255)")
            return
        if status not in [0, 1]:
            print("ESP: Received invalid fan status (must be 0 or 1)")
            return
        if not (0 <= fan_speed_data <= 3):
            print("ESP: Received invalid fan speed data (0 to 3)")
            return
        if not (0 <= fan_speed_set <= 3):
            print("ESP: Received invalid fan speed set value (0 to 3)")
            return

        print(f"ESP: Handling Fan Control message")
        print(f"Fan ID: {fan_id}, Status: {status}, Fan Speed Data: {fan_speed_data}, Fan Speed Set: {fan_speed_set}")

        # Publish the fan_speed_data to a separate MQTT topic
        fan_speed_topic = "fan/speed"
        fan_speed_payload = str(fan_speed_data)
        await client.publish(fan_speed_topic, fan_speed_payload, qos=1)
        print(f"Published fan speed data to MQTT topic '{fan_speed_topic}': {fan_speed_payload}")

    else:
        print("ESP: Unsupported message type")


async def process_rx():
    """
    Processes incoming messages over the UART network.
    Handles messages intended for this device, passes on messages for others,
    and ignores invalid or self-sent messages.
    """
    stream = b''
    receiving_message = False

    while True:
        # Read one byte
        c = uart.read(1)

        # If a byte is received
        if c is not None:
            stream += c

            # Check for message start
            if stream[-2:] == b'AZ' and not receiving_message:
                # Start a new message
                receiving_message = True
                stream = b'AZ'  # Reset stream to only include the prefix

            # Check for message end
            elif stream[-2:] == b'YB' and receiving_message:
                # Complete the message
                receiving_message = False
                message = stream  # Copy the full message
                stream = b''  # Clear the stream

                # Validate message length
                if len(message) != MAX_MESSAGE_LEN:
                    print(f"ESP: Invalid message length ({len(message)}), ignoring")
                    # Wait for the next valid prefix
                    receiving_message = False
                    stream = b''
                    continue

                # Handle the received message
                handle_message(message)
                led1.value(led1.value() ^ 1)  # Toggle LED
                continue

            # Abort if message exceeds buffer size
            elif receiving_message and len(stream) > MAX_MESSAGE_LEN:
                print("ESP: Message too long, aborting")
                receiving_message = False
                stream = b''  # Clear the stream and wait for the next prefix

        await asyncio.sleep_ms(10)


async def check_debug_button():
    """
    Checks the state of the debug button and sends a message to the MQTT server if pressed.
    """
    while True:
        if debug_button.value() == 0:  # Button is pressed (active low)
            # Turn on LED1 to indicate the button is pressed
            led1.value(0)

            # Example message to publish
            debug_message = "Debug button pressed"
            print(f"ESP: Debug button pressed, sending message: {debug_message}")

            # Publish the message to the MQTT server
            await client.publish(TOPIC_PUB, debug_message, qos=1)

            # Wait for the button to be released to avoid multiple triggers
            while debug_button.value() == 0:
                await asyncio.sleep_ms(50)

        else:
            # Turn off LED1 when the button is not pressed
            led1.value(1)

        await asyncio.sleep_ms(50)  # Check the button state every 50ms


async def receiver():
    b = b''
    sreader = asyncio.StreamReader(uart)
    while True:
        res = await sreader.read(1)
        if res==b';':
            b+=res
            await client.publish(TOPIC_PUB, b, qos=1)

            print('published', b)
            b = b''
        else:
            b+=res


# Subscription callback
def sub_cb(topic, msg, retained):
    """
    Handles incoming MQTT messages and sends a fan control message to Dan (\x03)
    based on the message content (0, 1, 2, or 3).
    """
    print(f'Topic: "{topic.decode()}" Message: "{msg.decode()}" Retained: {retained}')

    # Check if the message is a valid number (0, 1, 2, or 3)
    try:
        value = int(msg.decode())
        if value in [0, 1, 2, 3]:
            # Send a fan control message to Dan (\x03)
            send_message(
                source=my_id,               # This device's ID
                destination=b'\x03',        # Dan's ID
                message_type=32,            # Fan Control message type
                fan_id=1,                   # Example fan ID
                status=1,                   # Example status (e.g., ON)
                fan_speed_data=value,       # Fan speed data (same as value)
                fan_speed_set=value         # Fan speed set (same as value)
            )
            print(f"Sent fan control message to Dan with fan_speed_set: {value}")
        else:
            print("Message is not a valid fan speed value (0-3)")
    except ValueError:
        print("Message is not a valid integer")

    # Forward the message to UART
    uart.write(msg)


async def wifi_han(state):
    wifi_led(not state)
    print('Wifi is ', 'up' if state else 'down')
    await asyncio.sleep(1)

# If you connect with clean_session True, must re-subscribe (MQTT spec 3.1.2.4)
async def conn_han(client):
    await client.subscribe(TOPIC_SUB, 1)

async def read_temperature_and_publish():
    """
    Reads temperature data from the BMP280 sensor, publishes it to the MQTT server,
    broadcasts it to all devices, and sends a fan control message to Dan based on the temperature.
    Ensures the fan control message is sent only once when crossing the threshold.
    """
    last_fan_speed = None  # State variable to track the last sent fan speed

    while True:
        # Read temperature from the sensor
        temp_data = sensor.temperature

        # Ensure the temperature data is within valid ranges
        if not (-40 <= temp_data <= 155):
            print("ESP: Temperature data out of range (-40 to 155)")
            await asyncio.sleep(2)
            continue

        # Print the temperature data
        print(f"Temperature: {temp_data:.2f} °C")

        # Publish the temperature data to the MQTT server
        temp_payload = f"{temp_data:.2f}"
        await client.publish(TOPIC_PUB, temp_payload, qos=1)
        print(f"Published temperature data to MQTT: {temp_payload}")

        # Send the temperature data as a broadcast message
        send_message(
            source=my_id,               # This device's ID
            destination=broadcast,      # Broadcast ID
            message_type=16,            # Temp Data message type
            sensor_id=1,                # Example sensor ID
            status=1,                   # Example status (e.g., valid data)
            temp_data=temp_data         # Single temperature value
        )
        print(f"Broadcasted temperature data: {temp_data:.2f} °C")

        # Determine the fan speed based on the temperature
        if temp_data >= 34:
            fan_speed = 3  # High speed
        else:
            fan_speed = 2  # Medium speed

        # Send the fan control message only if the fan speed has changed
        if fan_speed != last_fan_speed:
            send_message(
                source=my_id,               # This device's ID
                destination=b'\x03',        # Dan's ID
                message_type=32,            # Fan Control message type
                fan_id=1,                   # Example fan ID
                status=1,                   # Example status (e.g., ON)
                fan_speed_data=fan_speed,   # Fan speed data
                fan_speed_set=fan_speed     # Fan speed set
            )
            print(f"Sent fan control message to Dan with fan_speed_set: {fan_speed}")
            last_fan_speed = fan_speed  # Update the state variable

        # Wait before reading the temperature again
        await asyncio.sleep(2)

async def main(client):
    try:
        await client.connect()
    except OSError:
        print('Connection failed.')
        return
    asyncio.create_task(receiver())

    n = 0
    while True:
        await asyncio.sleep(5)
        print('publish', n)
        # If WiFi is down the following will pause for the duration.
        await client.publish(TOPIC_HB, '{} {}'.format(n, client.REPUB_COUNT), qos = 1)
        n += 1

# Demonstrate scheduler is operational.
async def heartbeat():
    s = True
    while True:
        await asyncio.sleep_ms(500)
        blue_led(s)
        s = not s

# Define configuration
config['server'] = MQTT_SERVER
config['ssid']     = WIFI_SSID
config['wifi_pw']  = WIFI_PASSWORD

config['ssl']  = True
# read in DER formatted certs & user key
with open('certs/student_key.pem', 'rb') as f:
    key_data = f.read()
with open('certs/student_crt.pem', 'rb') as f:
    cert_data = f.read()
with open('certs/ca_crt.pem', 'rb') as f:
    ca_data = f.read()
ssl_params = {}
ssl_params["cert"] = cert_data
ssl_params["key"] = key_data
ssl_params["cadata"] = ca_data
ssl_params["server_hostname"] = MQTT_SERVER
ssl_params["cert_reqs"] = ssl.CERT_REQUIRED
config["time_server"] = MQTT_SERVER
config["time_server_timeout"] = 10

config['ssl_params']  = ssl_params

config['subs_cb'] = sub_cb
config['wifi_coro'] = wifi_han
config['connect_coro'] = conn_han
config['clean'] = True
config['user'] = MQTT_USER
config["password"] = MQTT_PASSWORD

# Set up client
MQTTClient.DEBUG = True  # Optional
client = MQTTClient(config)

asyncio.create_task(process_rx())
asyncio.create_task(check_debug_button())
asyncio.create_task(heartbeat())
asyncio.create_task(read_temperature_and_publish())
try:
    asyncio.run(main(client))
finally:
    client.close()  # Prevent LmacRxBlk:1 errors
    asyncio.new_event_loop()

</code></pre>
</details>

- [ESP Code Rev1](esp32_mqtt.zip)
- [ESP Code Rev2](esp32_mqtt_Rev2.zip) 4/22/25
- [ESP Code Rev2.1](esp32_mqtt_Rev2.1.zip) 4/22/25
