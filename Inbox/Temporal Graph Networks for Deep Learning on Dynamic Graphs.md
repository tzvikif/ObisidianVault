

27-10-2024 15:26

Status: #in_progress

Tags: #video, #consume, #paper

# Temporal Graph Networks for Deep Learning on Dynamic Graphs



![[Temporal Graph Networks for Deep Learning on Dynamic Graphs.png]]

## Memory
![[Temporal Graph Networks for Deep Learning on Dynamic Graphs-1.png]]

- Capture the state for each node
- it is a *compressed representation* of all past interactions of a node.
- the memory is not a parameter, thus can be updated at test time. for example if a new node was added to the graph.

**Moduels for updating the memory:**
### Message Function

given an interaction (i,j), computes messages for *source* and *destination* 
$m_{i}(t)=msg_{s}(S_{i}(t^{-}),(S_{j}(t^{-}),t,e_{ij}(t))$
$m_{i}(t)=msg_{d}(S_{j}(t^{-}),(S_{i}(t^{-}),t,e_{ij}(t))$
![[Temporal Graph Networks for Deep Learning on Dynamic Graphs-2.png]]

### Message Aggregator
The Purpose of  *Message Aggregator* is to aggregate messages $i\to j$ which have different timestamps.
$\bar{m}_{i}(t)=agg(m_{i}(t_{1}),\dots,m_{i}(t_{b}))$
![[Temporal Graph Networks for Deep Learning on Dynamic Graphs-3.png]]
$m_{2}(t_{1}),m_{2}(t_{2})$ appears in the same batch, we need to aggregate them, ending with a single message.

### Memory Updater
Updates the memory using the *new message* and the *previous memory*.
$S_{i}(t)=mem(\bar{m}_{i}(t),S_{i}(t^{-}))$
![[Temporal Graph Networks for Deep Learning on Dynamic Graphs-4.png]]
The *mem* function is *RNN* .

## Node Embedding
### embedding
- computes the *temporal embeddings* of a node (which can be then used for prediction) using the graph
-  Solves the *staleness problem*
	- when a user is not
## References

- https://arxiv.org/abs/2006.10637
- videos
	- https://www.youtube.com/watch?v=0tw66aTfWaI
	- [Paper Explained by the Author](https://www.youtube.com/watch?v=W1GvX2ZcUmY&t=1045s)
- [github repo](https://github.com/twitter-research/tgn)

