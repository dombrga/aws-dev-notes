## OSI model
1. Open systems interconnection.
2. consists of 7 layers.
3. model for engineers to design and organize data networking protocols and their order of operations.
4. how messages are constructed and send thru the data network so receiving device can understand the msg.
5. the model
   1. application
   2. presentation
   3. session
   4. transport
   5. network
   6. data link
   7. physical
6. mnemonic is "please do not throw sausage pizza away".

### application layer 7
1. client-server model.
2. in http in web, client is web browser and server is an http server.

### presentation layer 6 and session layer 5
1. layer 6 is responsible for encrypting data
2. layer 5 is for for building a session between client and server.
3. TLS occurs between layer 6 and 5.
4. you only need to know encryption happens after layer 7

### transport layer 4
1. where TCP (transport control protocol) operates.
2. tcp actually operates between layers 4 and 5.
3. allows to keep track of data we send.
4. SYN-ACK message.
5. creates session between client-server.
6. TCP is going to send a message to server called SYN. Server replies with SYN ACK msg. Client then sends an ACK msg. Then we can send actual msg to the server and process it. But before that, server sends a message to the client saying "i got your msg".

### network layer 3
1. where we have Internet Protocol (IP).
2. addressing and infrastructure.
3. internet and routers come into play.
4. router look at the destination ip addr.
5. like a roadmap to connect client to server.

### data link layer 2
1. more local.
2. ethernet protocol.
3. move message from one device to the nearest device.
4. works with network layer.

### physical leyer 1
1. creates the signal.
2. responsible for converting info in the data link layer into signal that can be propagated through a copper, glass, or wireless.
3. also responsible for converting information back in a form that the data link layer can read.

### osi according to comptia
1. layer 7
   - protocol definition like http, data formatting, emulation.
2. layer 6
   - encryption, compression, conversion of ascii to ebcidic.
3. session
   - establish and termination network conns.
4. transport
   - divides data into distinct parts (segments)
   - error correction
5. network
   - logical addressing
   - packet creation
   - routing
6. data link
   - formats data into frames
   - mac addressing
7. physical
   - electrical signal
   - bits
   - digital to analog conversion and vv

8. http, tls, tcp, ip, ethernet, signals/media