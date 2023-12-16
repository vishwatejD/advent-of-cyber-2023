# Day 2
## task name
O Data, All Ye Faithful 
### Learning
JUPYTER NOTEBOOKS:- Jupyter Notebooks are open-source documents containing code, text, and terminal functionality. They are popular in the data science and education communities because they can be easily shared and executed across systems. Additionally, Jupyter Notebooks are a great way to demonstrate and explain proof of concepts in Cybersecurity.

We first open the python 3 notebook to write the code.
Then we write the following code, 

```python
import pandas as pd
import matplotlib.pyplot as plt
```
___
QUESTION 1:- 

How many packets were captured (looking at the PacketNumber)?
This question can be answered in two ways , we can open the network_traffic.csv and scroll down to see the number of rows present ,i.e, 100.
The other method is we write the following code and get the output.

![image](https://github.com/vishwatejD/advent-of-cyber-2023/assets/141154035/4c6c6797-2131-4ead-ac39-8af19e940f22)
___
QUESTION 2:- 

What IP address sent the most amount of traffic during the packet capture?
For this we write the following code, ``` # dataframe.groupby(['name of the column']).size()```

![image](https://github.com/vishwatejD/advent-of-cyber-2023/assets/141154035/08425058-8b4d-4419-8abd-9354bb74629c)

From the obtained information we can conclude that 10.10.1.4 has the highest traffic.
___
QUESTION 3:-

What was the most frequent protocol?

![image](https://github.com/vishwatejD/advent-of-cyber-2023/assets/141154035/29d196a8-f736-4ed7-9fea-44535d530229)

Similar to the previous question we use the groupby command and then size() to know how many times a protocol has occured.
From the obtained statistics we can conclude that ICMP has the highest occurence.

