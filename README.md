# Practice Threading Event Handlers

The main class of this project starts up two threads using a stream of Event Listeners. It then creates a stream of input to the console

Every time a message is sent in, an event is pushed to the Event Tracker Singleton. The tracker will keep track of messages sent in. If a message has a Listener associated with it, there should be a response printed to the console.

### Event Tracker

* Singleton class that is synchronized between threads
* Implements the Tracker interface
* Stores the number of times a string has been sent into it
* Push increments the integer associated to the string passed in
* Has returns true if there is an integer asssociated with the string passed in and if the integer is greater than 0
* Handle takes in an event handler. After running the event handler's handle function it decrements the integer associated with the message passed in.
* Handle is the only way to decrement an integer in the map

### Event Listener

* Extends Thread
* Takes in a message to listen for and a reply to respond with
* Optionally can take in a custom tracker. Defaults to the EventTracker singleton class
* The run method uses a while loop that continues to run as long as "readyToQuit" returns false
* Ready to quit returns true if there is a "quit" event in the event tracker
* The should reply method returns true if the event tracker has a message the listener is listening for
* In the while loop, if should reply returns true, the Tracker has its "handle" method called passing in an instance of EventHandler. The Handler prints out the reply thread-event-handlers
