# Assignment-8 CS361 Microservice
# Sending
To request data the client would need to input a dictionary into a json file.
    Formatting for this would be {"Min value": the min value they decide to select, "item": qty, "item": qty..., "item": qty}.
They would then need to connect to the zmq server and send the json file.

# EX callout:
Connecting: 
    socket = context.socket(zmq.REQ)
    socket.connect("tcp://localhost:5555")
Sending json: 
    json_dict = {"Min Value": 10, "Carrot": 34, "Apple": 9, "Pineapple": 5}
    json_file = json.dumps(json_dict)
    socket.send_json(json_file)

# Receiving
They wil then receive the data via json file containing all the items that are less in qty then the "Min Value" they submitted.

# EX callout:
Receiving: 
    message = socket.recv_json()
    print(f"Received reply [ {message} ]")
Output: 
    Received reply [ {"Apple": 9, "Pineapple": 5} ]
    
# UML sequence diagram
![image](https://user-images.githubusercontent.com/130004542/236644171-fae020b1-3210-4ff1-8634-ec8af32dcffe.png)
