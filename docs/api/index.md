---
title: API
tags:
---

# API

## Summary
This API documentation provides details about the message structure, status codes, and message types used in the system. It includes tables for Message ID, Status, Message Types, Temperature Sensor (Message Type 1), and Fan Control (Message Type 2).

## Sequence Diagram
``` mermaid
sequenceDiagram
    actor Web User
    Web User-->>+Cade: Turn on LED1
    Cade->>+Dan: Turn on LED1
    Dan->>+Jahmel: Turn on LED1
    Jahmel->>-Jahmel: LED1 ON, Trash Message
    actor In Person User
    In Person User-->>+Jahmel: Set1 Motor Speed
    Jahmel->>+Cade: Set1 Motor Speed
    Cade->>+Dan: Set1 Motor Speed
    Dan->>-Dan: Set1 Motor Speed Trash
    Web User-->>+Cade: Set2 Motor Speed
    Cade->>+Dan: Set2 Motor Speed
    Dan->>-Dan: Set2 Motor Speed Trash
    loop Every 3 second
    Cade->>+Dan: Sensor Data
    Cade-->>+Web User: Sensor Data
    Dan->>+Jahmel: Sensor Data
    Jahmel-->>+In Person User: Sensor Data
    Jahmel->>+Cade: Sensor Data
    Cade->>-Cade: Sensor Data Trash
    end
```

## Message Type Matrix

- S = Sending Message
- R = Receiving Message

| Message Type               | Message ID | Cade<br>Role: MQTT<br>ID: 0x01     | Dan<br>Role: Motor<br>ID: 0x03                | Jahmel<br>Role: HMI<br>ID: 0x02                 |
|----------------------------|------------|------------------------------------|-----------------------------------------------|-------------------------------------------------|
| sensor value               | 0x10       | S<br>(Temperature Value in °C)     | R<br>(motor turns on to cool system)          | R<br>(Debug LEDs on/off within value ranges)    |
| Set Motor Speed            | 0x20       | S<br>(Publish 1, 2, or 3)          | R<br>(Set 1 = Low, 2 = Medium, 3 = High)      | S<br>(toggle debug button press 1, 2, 3)        |
| Motor Speed Status/Speed   | 0x20       | R<br>(Upload 1, 2, 3)              | S<br>(Broadcast status/speed)                 | R<br>(Debug LED blinks to recognize message)    |




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
| Fan Control      | 0 to 3    | 0x20 |

---

### Temperature Sensor (Message Type 1)

The Temperature Sensor table defines the structure of messages for temperature data. Each byte in the message is mapped to a specific variable, with details about its type, range, and example values.

| Byte | Variable Name | Variable Type | Min Value | Max Value | Example Value |
|---|------------------|--------------|-----------|-----------|--------------|
| 1 | prefix_1         | uint8_t      | 0x41      | 0x41      | 0x41         |
| 2 | prefix_2         | uint8_t      | 0x5a      | 0x5a      | 0x5a         |
| 3 | source_id        | uint8_t      | 1         | 3         | 0x03         |
| 4 | destination_id   | uint8_t      | 1         | 3 & 88    | 0x02         |
| 5 | message_type     | uint8_t      | 0x10      | 0x20      | 0x10         |
| 6 | temp_id          | uint8_t      | 0         | 1         | 0x01         |
| 7 | status           | uint8_t      | 0         | 1         | 0x01         |
| 8 | temp_data_integer | uint8_t     | 0         | 255       | 25           |
| 9 | temp_data_fraction | uint8_t    | 0         | 99        | 50           |
| 10-62 | Unused       | uint8_t      | 0x00      | 0x00      | 0x00         |
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
            <td>1</td>
            <td>1</td>
            <td>0x10</td>
            <td>0</td>
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
            <td>3 % 88</td>
            <td>0x10</td>
            <td>1</td>
            <td>1</td>
            <td>255</td>
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
| 3     | source_id       | uint8_t      | 1         | 3         | 0x01         |
| 4     | destination_id  | uint8_t      | 1         | 3 & 58    | 0x04         |
| 5     | message_type    | uint8_t      | 0x20      | 0x20      | 0x20         |
| 6     | fan_id          | uint8_t      | 0         | 1         | 0x02         |
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
            <td>1</td>
            <td>0x20</td>
            <td>0</td>
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
            <td>3 & 88</td>
            <td>0x20</td>
            <td>1</td>
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
            <td>0x03</td>
            <td>0x20</td>
            <td>0x01</td>
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
