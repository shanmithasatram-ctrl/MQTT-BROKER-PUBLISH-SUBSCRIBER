# MQTT Publish--Subscribe System using Node-RED

## Project Overview

This project demonstrates a Publish--Subscribe (Pub/Sub) system using
Node-RED and an MQTT message broker. The system simulates a Smart
Environment Monitoring System where multiple sensors publish
environmental data and subscribers receive and visualize the data in
real time.

The MQTT broker routes messages between publishers and subscribers based
on topics. A wildcard subscriber is used to monitor multiple topics, and
a Node-RED dashboard is implemented to visualize live data.

------------------------------------------------------------------------

# System Architecture

## 1. Publishers

Two publishers simulate sensor data.

Temperature Sensor Publisher\
Topic: campus/sensor/temperature\
Publishes temperature readings.

Air Quality Sensor Publisher\
Topic: campus/sensor/airquality\
Publishes air quality index (AQI) values.

------------------------------------------------------------------------

## 2. MQTT Broker

The MQTT broker acts as the message router between publishers and
subscribers.

Responsibilities: - Receives messages from publishers - Filters messages
based on topic subscriptions - Sends messages to the appropriate
subscribers - Manages QoS levels and retained messages

------------------------------------------------------------------------

## 3. Subscribers

### Topic Subscribers

Specific subscribers listen to individual topics:

-   campus/sensor/temperature
-   campus/sensor/airquality

These messages are forwarded to the Node-RED dashboard.

### Wildcard Subscriber

A wildcard subscriber monitors multiple sensor topics.

Topic used: campus/sensor/#

This subscriber receives messages from all sensors under the topic
hierarchy.

Example: campus/sensor/temperature : 30\
campus/sensor/airquality : 80

------------------------------------------------------------------------

## 4. Node-RED Dashboard

The Node-RED dashboard provides real-time visualization of sensor data.

Dashboard Components: - Temperature Gauge - Air Quality Gauge - Line
Chart for sensor history

The dashboard updates automatically whenever new messages are received.

------------------------------------------------------------------------

# MQTT Topics Used

  Topic                       Description
  --------------------------- -------------------------
  campus/sensor/temperature   Temperature sensor data
  campus/sensor/airquality    Air quality sensor data
  campus/sensor/#             Wildcard subscriber
  campus/status               System status

------------------------------------------------------------------------

# Quality of Service (QoS)

MQTT supports three QoS levels.

QoS 0 -- At most once\
Message delivered once with no acknowledgement.

QoS 1 -- At least once\
Message delivered at least once with acknowledgement.

QoS 2 -- Exactly once\
Message delivered exactly once with highest reliability.

In this project, QoS 1 is used to ensure reliable message delivery.

------------------------------------------------------------------------

# Retained Messages

Retained messages allow the broker to store the last message of a topic.

When a new subscriber connects, the broker immediately sends the
retained message.

Example: If the last temperature value was 28°C, the new subscriber
receives 28°C instantly.

------------------------------------------------------------------------

# Node-RED Flow Description

The Node-RED flow includes:

Input Nodes - MQTT In node for temperature - MQTT In node for air
quality - MQTT wildcard subscriber

Processing Nodes - Function nodes to format data - Debug nodes for
monitoring

Output Nodes - Temperature gauge - Air quality gauge - Data chart

------------------------------------------------------------------------

# Example Message Log

\[INFO\] campus/sensor/temperature : 29\
\[INFO\] campus/sensor/airquality : 75\
\[INFO\] campus/status : system running\
\[INFO\] campus/sensor/temperature : 30\
\[INFO\] campus/sensor/airquality : 78

------------------------------------------------------------------------

# Screenshots Included

1.  Node-RED Flow Screenshot
2.  MQTT Message Log Screenshot
3.  Node-RED Dashboard Screenshot

------------------------------------------------------------------------



# Technologies Used

-   Node-RED
-   MQTT Protocol
-   Mosquitto MQTT Broker
-   Node-RED Dashboard
-   JavaScript (Function Nodes)



------------------------------------------------------------------------

# Conclusion

This project demonstrates how MQTT enables efficient communication using
the publish--subscribe model. Using Node-RED and MQTT broker, real-time
sensor data can be collected, monitored, and visualized through
dashboards.


#Video   Demonstration Link
https://drive.google.com/file/d/1Y776e9hRiF8KjApRpr7ivopmiN1hr8p_/view?usp=sharing
