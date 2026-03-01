# Smart Mess Monitoring System using Node-RED and MQTT

## Project Overview
This project implements a Smart Mess Monitoring System using Node-RED and the MQTT publish–subscribe architecture.

The system simulates real-time monitoring of a campus mess by tracking food temperature, student demand, and chef preparation status. It demonstrates core MQTT concepts such as publishers, subscribers, wildcard topics, Quality of Service (QoS), retained messages, and live data visualization using a dashboard.

## System Architecture
The system follows the MQTT publish–subscribe communication model.
### Publishers
Three publishers are implemented in this system:

1. Food Temperature Publisher  
   - Topic: `mess/food/temperature`  
   - QoS: 0  
   - Generates random temperature values between 60–80°C  
   - Simulates a food container temperature sensor  

2. Student Demand Publisher  
   - Topic: `mess/food/demand`  
   - QoS: 1  
   - Generates random demand values between 0–100  
   - Simulates the number of students ordering food  

3. Chef Status Publisher  
   - Topic: `mess/food/status`  
   - QoS: 1  
   - Retained message enabled  
   - Sends one of the following values:
     - Cooking
     - Ready
     - Out of Stock  
### Subscriber

A wildcard subscriber is implemented using the topic:
`mess/#`
This allows the system to subscribe to all subtopics under the `mess` hierarchy and display incoming messages in the debug panel.

## Dashboard Implementation
The Node-RED dashboard provides live visualization of the system:
- Gauge: Displays Food Temperature in °C  
- Line Chart: Displays Student Demand over time  
- Text Display: Shows the current Chef Status  

Dashboard URL:  
http://localhost:1880/ui  
The dashboard updates in real time as publishers send data to the MQTT broker.

## MQTT Concepts Demonstrated
### Publish–Subscribe Model
Publishers send data to topics without directly interacting with subscribers. Subscribers receive messages based on the topics to which they are subscribed.

### Wildcard Subscription
The topic `mess/#` is used to capture all messages under the `mess` topic hierarchy.
### Quality of Service (QoS)
- QoS 0 is used for temperature data to provide fast delivery without acknowledgment.  
- QoS 1 is used for demand and status data to ensure message delivery at least once.

### Retained Messages
The `mess/food/status` topic uses retained messages so that new subscribers immediately receive the last known status update.

## Technologies Used
- Node-RED  
- MQTT Protocol  
- HiveMQ Public MQTT Broker  
- Node-RED Dashboard
- 
## Project Files
- flow.json: Complete Node-RED flow configuration  
- README.md: Project documentation  
- Screenshots folder containing:
  - Node-RED flow screenshot  
  - Debug log screenshot  
  - Dashboard interface screenshot
  - 
## Demonstration
The video demonstration explains:
- The role of publishers and subscribers  
- Wildcard topic usage  
- QoS configuration  
- Retained message behavior  
- Live dashboard visualization
- 
## Conclusion
This project successfully implements a real-time MQTT-based publish–subscribe system using Node-RED. It demonstrates message routing through a broker, multiple publishers, a wildcard subscriber, QoS configurations, retained messages, and a live monitoring dashboard. The system can be extended for real-world smart campus or food monitoring applications.
