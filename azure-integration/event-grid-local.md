# Test Event Grid Local

It is possible to test the event grid trigger locally. To do this one can set up a rest client with the function adress. As headers one needs to set the content type to application/json and the aeg-event-type to Notification. When this is done a post request can be send to the endpoint. 