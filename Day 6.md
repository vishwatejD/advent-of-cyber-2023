# Day 6
## Task name
Memories of Christmas Past

### Learnings
What is buffer overflow? 

Buffers are memory storage regions that temporarily hold data while it is being transferred from one location to another. A buffer overflow (or buffer overrun) occurs when the volume of data exceeds the storage capacity of the memory buffer. As a result, the program attempting to write the data to the buffer overwrites adjacent memory locations.

Using the TAB key opens the Debug dialog box where we can see the hex values assigned for each variable as playername, coins, etc

We notice that the player name has space for only 12 bytes , if we try to assign it values more that 12 they flow into the coins column. 
