

23-10-2024 00:23

Status: #in_progress

Tags: #consume, #video

# Temporal Graph Networks (TGN) from scratch

the lecture is based on [[Temporal Graph Networks for Deep Learning on Dynamic Graphs]] paper.

Static graph
![[Temporal Graph Networks (TGN) from scratch static graph.png]]

Dynamic graph
![[Temporal Graph Networks (TGN) from scratch dynamic graph.png]]

## Dynamic graph examples

- *movie recommendation platform*. we can different recommendation based on our interest of movies at the current time. our "taste" in movies can change over time.
- *Pandemic*. Nodes represent people that can take the following status:
	- Susceptible
	- infected
	- recovered
	at fist all the people are susceptible. Then their can change over time to infected and recovered, of a result of the interaction between the people.
- *Ecommerce*.  a person changes its status: login -> searching -> add to cart ->...
- *Social network*

the TGN can be divided into 
- *discreet*. the structure of the graph is the same the features/labels are changing over time.
- *continuous*. every time stamp there might be a different graph structure.

## Main Concept

![[Temporal Graph Networks (TGN) from scratch encoder decoder.png|400]]

The *Encoder* create the Embeddings $Z(t)=(z_{1}(t)\dots,z_{n}(t))$ , $z_{i}(t)$ for every node.
Using the *Decoder* and time $t$ it can execute the following tasks:
- Node classification
- Edge prediction
- Graph classification

## Core modules of TGN
### Memory
this module stores all the history of  the nodes in the graph. and their events.
an event is if a node appears or disappears.
**Memory state**: $S_{i}(t)$ - the state of node $i$ of time $t$
### Message Function
![[Temporal Graph Networks (TGN) from scratch Message Function.png|400]]

#### Edge wise event
$\large m_{i}(t)=msg_{s}(S_{i}(t-1),S_{j}(t-1),\Delta t,e_{ij}(t))$
$\large m_{j}(t)=msg_{d}(S_{j}(t-1),S_{i}(t-1),\Delta t,e_{ij}(t))$
**Remark**
$S_{i}(t)$ is the memory of node $i$ at time $t$
$S_{i}(t-1)$ is the memory of node $i$ at time $t-1$
#### Node wise event
???
### Message Aggregator
aggregating node in time with an *aggregation function* to one single message.

for example we can take the *recent message* & *mean message* (mean of the messages so far)
$m_{i}(t)=agg(m_{i}(t_{1}),\dots,m_{i}(t_{b}))$
where $t_{1},\dots,t_{b}$ are $b$ previous times to $t$
$agg$ can be a simple function like mean or *RNN*
### Memory updater
the *memory updater* is responsible for maintaining and updating the historical information of the  nodes.
>Whenever an event involving a node occurs, the memory of that node gets updated.
>Node remembers the new information from the event along with what it already knows.
#### Update Process



### Embedding
$Z_{i}(t)$ - temporal embedding of $i$ at $t$
>Solves memory staleness???

## Simple example with numbers
43:00
## References

https://www.youtube.com/watch?v=OstnUeqoKLg