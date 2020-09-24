# Indoor-Iot

The purpose of this project is to develop an IoT solution. The solution will be 2.4 GHz spread-spectrum
transceivers with a custom messaging scheme. Nodes will be created that both create and consume
data on the network. A bridge will also be constructed to allow the IoT network to interoperate with a 100-
Base-T Ethernet connection, with internet access. Services will also be created that extract data from
relevant Web sites and provide this information to nodes on the IoT network.

Communications protocol team:
The team is responsible to delivering a common API library for use in all nodes with transceivers that
allows messages to be sent and received on the network. The minimum requirements are as follows:
a. The solution must support a contention-free communication scheme using a frame/slot scheduled
transmission, except in the case when devices are being discovered into the network.
b. The scheduling scheme should optimize transmission times where possible to support sleep
modes for maximum battery life.
c. The baud rate, frame, and slot timing should support fast messages (e.g., a wall switch is
toggled)
d. The messaging must include support for
1. Broadcast Event message (weather is, time is, door is open)
2. Broadcast Discovery messages to invite un-joined nodes to join the network
3. A method for a node to respond to the Discovery message in a way that maximizes the
probability that the message, which may conflict with other devices, is sent without conflict.
4. A Join message to request devices join the network, assigning a node number, with 3-way
handshaking to ensure a device has joined the network. Once the node has a node number,
it should know when it can transmit and when it should listen (frame/slot).
5. Unicast Status message that enquires about the health of a node (battery low, are you there)
6. Provide SW for all nodes to store the node number
7. Provide SW for all nodes so that the node can send and receive messages.
The team shall also construct several simple nodes as a reference design to show the system in
operation. The team shall also construct a sync node that is used to define the reference timing for the
network.
A special node should be constructed that if used in diagnosing the IoT system in operation. The sniffer
should work in the following modes, at minimum:
a. Raw message decoder displaying the transmitted frame/slot, node information, and message
decoded
b. Timing analysis mode displaying the frame/slot and actually time of the message relative to the
sync message, and variance from expected time (used to diagnose timing when baud rates
increase).
c. A scrolling grid view of the messages, clearly showing the type of message or node sent in each
frame real time.
The goal will be for this sniffer output to display on the lab projectors for integration testing.


Bridge and services team:
A special node has an Ethernet connection and acts as the “bridge” to Internet connection through the
Ethernet jack. The solution should be based on the ENC28J60 and the class code. The minimum
requirements include the following:
a. Must support DHCP protocol and dynamic IP address assignment
b. Must support Netbios name services
c. Should forward the UDP message sent to port 1024 on the Ethernet port as a message on IoT
network using the protocol team API.
d. Must support a scheme allowing messages to be forwarded from the IoT network (using the
protocol team API) to an Ethernet address.
At least one service will create connections to Web sites and extract data for transmission to nodes on
the IoT network. The minimum requirements are:
a. Must implement TCP state machine to actively open an connection and terminate the connection
at the end
b. Issue an HTTP GET message and download the data file
c. Parse the data and provide it to the IoT network using the protocol team API
d. If using time services, make sure you follow network protocols for how often you access a site.
e. Send back the information as discussed in class.


Rules team:
This team will develop the rules code for all nodes.
a. Determine the format of the rules set message.
b. The rules will be stored in EEPROM of the node.
c. Support for at least 3 rules / node are required.
d. Provide SW for all nodes to react to messages and process rules


User interface:
The UI software must:
a. Connect to the bridge
b. Keep track of nodes that are joined to the IoT network
c. Keep track of all rules sent to nodes
d. Allow the user to display the current nodes
e. Allow the user to send a Discovery command and process the responses
f. Allow the user to send a Join command to a device and process he response
g. Allow the user to send an Event message
h. Allow the user to enter in a Rule for a node and send it to the device
i. Allow the user to query the Status of a node and display the results
