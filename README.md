<img src="https://cdn-icons-png.flaticon.com/512/2316/2316073.png" alt="article-icon" width="75" height="75"/> Contains links and summaries for technical articles that I found interesting.

![alt text](https://camo.githubusercontent.com/76109812f3127b0f86940373897b04ac8943cb3c0f057f90046444480f61bafd/68747470733a2f2f692e696d6775722e636f6d2f77617856496d762e706e67)

</br>
<details>
   <summary> <b>Designing Whatsapp </b></summary>
   
> There are two microservices at the heart of Whatsapp: the chat service and the transient service. The chat service is responsible for messages sent by active users. The service first checks if the recipient is online or not and if they are, forwards the message directly to the user. Otherwise, the message will be handled by the transient service which is responsible for storing the messages (text or image) sent to offline users. When the recipient comes online, the service will forward the message to them. Media such as images or videos are uploaded to a file server and then served to the sender and receiver. Transfer of data between a user and the server occurs over web-sockets which offer a two-way communication channel. Clients also send heartbeats to the server over this channel which tells Whatsapp whenever a user was last active for their “Last seen at” feature.  
> [Read the article](http://highscalability.com/blog/2022/1/3/designing-whatsapp.html)
   
</details>


<details>
   <summary> <b>Understanding UUIDs, ULIDs and String Representations </b></summary>
   

> Numeric ID's used in databases are usually comprised of 4 or 8 bytes and are generated using sequencer objects which are typically monotonically increasing. Sequencers though have some limitations; firstly, the amount of new information that can be inserted is limited by the rate at which the sequencer can generate new ID's,
secondly, if you have a distributed system you need to ensure that the sequencers don't overlap, e.g. by having one sequencer generate only odd or even ID's and finally, the 
sequencer is coupled to the data so if you copy over a table, you need to copy the state of the sequencer as well as ensure that you don't reset the sequencer somehow. The 
solution to this is to use UUIDs (Univerally Unique Identifiers) which are 128 bit numbers, typically represented using hexadecimals. UUIDs confer several advantages. They can 
be generated at an unlimited rate, they can be generated simultaneoulsy in several places and it is possible to merge them into a single dataset. However, it is still possible for
collisions to occur and UUID's have no concept of locality e.g. if numeric IDs are being used then higher numbers indicate more recent information but this is not possible in the case of UUID's which are randomly generated. This is where ULIDs (Universally Unique Lexicographically Sortable Identifier) are useful. The first 48 bits are used to represent a millisecond precise UNIX timestamp and the last 80 bits are used for randomness. This means that we only have to worry about collisions inside the same millisecond and it also makes it possible to sort the data.  
> [Read the article](https://sudhir.io/uuids-ulids?utm_source=pocket_mylist)
   
</details>

<details>
   <summary> <b>Reading postmorterms </b></summary>
   

> Some of the most common cases of errors that have lead to large outages and failures at companies include:
> 1. **Error Handling:** Most critical failures are as a result of bad error handling. This includes simply ignoring errors, catching the wrong exceptions and having incomplete TODOs in the error handling code. A significant portion of errors are easily detectable where “the error handling logic of a non-fatal error was so wrong that any statement coverage testing or more careful code reviews by the developers would have caught the bugs”. 
> 1. **Configuration:** A disproportionate number of outages are caused by configuration bugs. 
> 1. **Hardware:** Every part of a machine can fail and many components can also cause data corruption, often at rates that are much higher than advertised e.g. DRAM error rates.
> 1. **Humans:** Outages and downtime due to human error are also common to the point where there are protocols in places to mitigate human risk e.g. having multiple people watch or confirm a risky operation before starting or having ops people standing by in case of disaster. The best way to reduce this kind of error though is automation. 
> 1. **Monitoring:** The lack of proper monitoring can also serve as a serious contributing factor towards bad outages.  
>  [Read the article](https://danluu.com/postmortem-lessons/)
   
</details>


<details>
   <summary> <b>Where does my validation live? </b></summary>
   
> The author talks about validating data at different layers of an application including the controller layer, the service layer and the domain layer. The controller layer validates the structure of the data, the properties and their types e.g., all required fields in a JSON object are present and are of the correct types. Converting the raw data to DTOs (Data Transfer Objects) is a good practice in this regard. The service layer should convert the DTOs into VOs [(Value Objects)]( https://enterprisecraftsmanship.com/posts/value-objects-explained/) where the property types are converted into valid domain concepts e.g., a payment type is converted from a string to a PaymentMethod which is a more meaningful concept. Finally, the domain layer validates the data by enforcing business rules e.g., preventing users from withdrawing sums larger than their account balance.   
>  [Read the article](https://blog.frankdejonge.nl/where-does-validation-live/)
   
</details>


   
