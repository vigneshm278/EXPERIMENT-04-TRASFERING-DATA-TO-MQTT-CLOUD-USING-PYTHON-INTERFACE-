### NAME:
### ROLL NO :
### DEPARTMENT 
### DATE



## EXPERIMENT-04-TRASFERING-DATA-TO-MQTT-CLOUD-USING-PYTHON-INTERFACE-



## AIM:
To transfer data from a Python script to an MQTT cloud server (HiveMQ Cloud) using the MQTT protocol. 
## APPARATUS/SOFTWARE REQUIRED: 
1.HiveMQ Cloud account
Python installed on your system
3. Required Python library: paho-mqtt
4. Internet connection

## THEORY 
### Message Queuing Telemetry Transport (MQTT)
MQTT is a lightweight messaging protocol used for efficient communication between devices over the Internet. It follows a publish-subscribe model, making it ideal for IoT applications.


 Message Queuing Telemetry Transport (MQTT)

MQTT is a lightweight and efficient messaging protocol designed for small, low-power devices that need to communicate over unreliable networks. It is widely used in Internet of Things (IoT) applications due to its low bandwidth requirements and minimal overhead.

MQTT Architecture and Working Principle

MQTT follows a publish-subscribe model, which is different from the traditional client-server architecture. Instead of direct communication between devices, MQTT introduces an intermediary called the broker that manages message distribution.

Broker: The central server that routes messages between clients (e.g., HiveMQ Cloud). The broker ensures that messages are delivered to the correct subscribers.

Client: Any device or application that sends (publishes) or receives (subscribes to) messages. Each client can act as a publisher, a subscriber, or both.

Topics: Channels through which messages are communicated (e.g., test/topic). Clients publish messages to a topic, and subscribers receive them based on their topic subscriptions.

QoS (Quality of Service) Levels: Define message delivery reliability:

QoS 0 (At most once): The message is sent without acknowledgment. It may be lost if network issues occur.

QoS 1 (At least once): The message is guaranteed to be delivered but may be duplicated.

QoS 2 (Exactly once): Ensures that the message is delivered only once, providing the highest level of reliability.

Why Use MQTT?

Lightweight Protocol: Ideal for IoT applications with limited resources.

Low Bandwidth Usage: Efficient data transmission over constrained networks.

Reliable Message Delivery: Supports different QoS levels.

Scalability: Suitable for large-scale IoT networks.

![image](https://github.com/user-attachments/assets/d21bcc04-9617-43dc-8cce-1dda54ea4562)

FIGURE -01 BLOCK DIAGRAMATIC REPRESENTATION OF MQTT PROTOCOL


### PROCEDURE 

Step 1: Set Up HiveMQ Cloud Account

Go to HiveMQ Cloud Console.

Sign up or log in.

Create a new cluster (if not already created).

Navigate to "Access Management" > "Credentials" and note the:

Host URL (e.g., your-cluster-url.hivemq.cloud)

Port (default: 8883 for secure connections)

Username & Password for authentication.

Step 2: Install Required Python Library

Run the following command in your terminal or command prompt to install the required MQTT library:

pip install paho-mqtt

Step 3: Write a Python Script to Publish Data

Create a Python script and paste the following code:

import paho.mqtt.client as mqtt

# HiveMQ Cloud credentials
BROKER = "your-cluster-url.hivemq.cloud"  # Replace with your HiveMQ Cloud broker URL
PORT = 8883  # Secure MQTT port
USERNAME = "your-username"  # Replace with your HiveMQ username
PASSWORD = "your-password"  # Replace with your HiveMQ password
TOPIC = "test/topic"  # Define your MQTT topic

#### Callback function when the client connects to the broker
def on_connect(client, userdata, flags, rc):
    if rc == 0:
        print("Connected to HiveMQ Cloud!")
    else:
        print(f"Connection failed with code {rc}")

#### Create MQTT client
client = mqtt.Client()

#### Set username and password for HiveMQ Cloud authentication
client.username_pw_set(USERNAME, PASSWORD)

#### Enable TLS for secure connection
client.tls_set()

#### Assign callback function
client.on_connect = on_connect

#### Connect to HiveMQ Cloud broker
client.connect(BROKER, PORT, 60)

#### Publish a message
message = "Hello from Python to HiveMQ!"
client.publish(TOPIC, message)
print(f"Message published: {message}")

#### Disconnect
client.disconnect()

Step 4: Verify Data Reception in HiveMQ Cloud

Open HiveMQ Cloud Console.

Go to "Live Data" > "MQTT Web Client".

Subscribe to the topic (test/topic).

Run the Python script.

Check if the message appears in the HiveMQ Web Client.
## PROGRAM
[





]

### OUTPUT SCREENSHOTS



## Results

Data was successfully transmitted from Python to HiveMQ Cloud and verified using the MQTT Web Client.



 
  
