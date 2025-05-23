# twobladebotdoc
Documentation of the socket.io interface that twoblade.com s global chat uses.


## First login
The server will send you information like `0{"sid":"(CENSORED FOR PRIVACY)","upgrades":[],"pingInterval":25000,"pingTimeout":20000,"maxPayload":1000000}`
To log in, the client must send `40{"token":"(CENSORED FOR PRIVACY)"}`

### Heartbeat
Periodically, the server will send you a simple `2`.
The client must return a simple `3` to stay logged in.

## Messages
This part, I would personally consider it to be tricky
### Sending a message
To send a message, send the following info `42["message","(PUT YOUR MESSAGE HERE)"]`
### Hearing Messages
Here is the information sent by the server after message has been sent, with usernames etc. censored and helpful descriptions given for certain parts: `42["message",{"id":"(CENSORED)","text":"test","fromUser":"(CENSORED)#twoblade.com","fromIQ":(IQ, no its not in a string),"timestamp":"(year)-(month)-(day)T(hours, 24 hour time):(minutes):(seconds).(miliseconds)Z"}]`

## User count
The server will periodically send info similar to: `42["users_count",37]`
You do not need to respond to it.
