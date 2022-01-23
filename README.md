# Articles
Contains links and summaries for technical articles that I found interesting.


## January, 2022

#### 1. [Designing Whatsapp](http://highscalability.com/blog/2022/1/3/designing-whatsapp.html):
> Talks about the the high level design of Whatsapp. Describes two main services: a chat service
which forwards messages to recipients that are online and a transient service which stores messages for users that are offline. At the heart of both services are chat servers which
maintain connections with the users and forward and fetch messages for them. Also talks about how images are shared as well as several client-server communication models such as 
short-polling, long-polling and web sockets. Apart from that, there is also mention of how the “Last seen” feature is implemented.

  ---
  
#### 2. [Understanding UUIDs, ULIDs and String Representations](https://sudhir.io/uuids-ulids?utm_source=pocket_mylist):

> Numeric ID's used in databases are usually comprised of 4 or 8 bytes and are generated using sequencer objects which are typically monotonically increasing. One thing to note 
is that when a sequencer generates a new ID, it first saves the ID and only then hands it to the user. This is ensure that if the sequencer crashes and the recepient does not
receive the ID, the sequencer would still have updated itself and would generate a new ID next time. If it handed over the key first and saved it later, it
could lead to a scenario where the sequencer could crash and fail to store the newly generated key which would in turn cause it to generate the same key the next time as well. 
Hence, it is possible that a sequencer can skip over some ID's and why you should not assume that the latest ID is equal to the number of rows in the table. There are other 
limitations of using sequencer objects as well. Firstly, the amount of new information that can be inserted is limited by the rate at which the sequencer can generate new ID's,
secondly if you have a distributed system you need to ensure that the sequencers don't overlap, e.g. by having one sequencer generate only odd or even ID's and finally, the 
sequencer is coupled to the data so if you copy over a table, you need to copy the state of the sequencer as well as ensure that you don't reset the sequencer somehow. The 
solution to this is to use UUIDs (Univerally Unique Identifiers) which are 128 bit numbers, typically represented using hexadecimals. UUIDs confer several advantages. They can 
be generated at an unlimited rate, they can be generated simultaneoulsy in several places and it is possible to merge them into a single dataset. However, it is still possible for
collisions to occur and UUID's have no concept of locality e.g. if numeric IDs are being used then higher numbers indicate more recent information but this is not possible in the
case of UUID's which are randomly generated. This is where ULIDs (Universally Unique Lexicographically Sortable Identifier) are useful. The first 48 bits are used to represent a millisecond precise UNIX timestamp and the last 80 bits are used for randomness. This means that we only have to worry about collisions inside the same millisecond and it also makes it possible to sort the data.

   
