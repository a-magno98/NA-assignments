# Network-analysis-assignments

The 1st assignment requires the analysis of a "realistic" graph.

Before starting the analysis on your graph, I recommend to do some practice with a small synthetic graph like those we discussed during lectures (e.g. random graphs, small world graphs, power law networks). Once you know how to use the library of your choice, move to a larger realistic model.

The "realistic" graph can be:

produced by using public APIs, see for example the list of APIs at http://www.programmableweb.com/apis/directory/1?sort=mashups
already published in online repository, see for example the repositories suggested in the first lecture
If the graph is large, but not too large, you can visualize it with Gephi. In order to use Gephy you should create a text file in a format that Gephi supports (see https://gephi.org/users/supported-graph-formats/).

You can select any domain and you can use the programming language/framework of your choice although I strongly recommend you to use Python libraries, for their simplicity.

Once built the graph, you should compute the metrics we discussed in class and draw some conclusions on the type of the network you have chosen. Examples of questions you can answer are the following:

(1) Does the graph have the same characteristics of a random or a power-law network?
(2) Which are the most important nodes, with respect to a given centrality measure?
(3) Are the paths short with respect to the size of the network?
(4) Is the network dense?
(5) Is the network assortative?
(6) And so on

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

In this 2nd assignment you will investigate the robustness of networks by simulating random failures and target attacks. The assignment is composed of two parts.

Part 1: Use small graphs
(there are 2 options, number 1 and number 2, select only one of the two)

2) Conspiracy in Social Networks
In a Big Brother society, the thought police wants to follow a "divide and conquer" strategy by fragmenting the social network into isolated components. You belong to the resistance and want to foil their plans. There are rumours that the police wants to detain individuals that have many friends and individuals whose friends tend to know each other. The resistance puts you in charge to decide which individuals to protect: those whose friendship circle is highly interconnected or those with many friends. To decide you simulate two different attacks on your network, by removing (i) the nodes that have the highest clustering coefficient and (ii) the nodes that have the largest degree. 

Study the size of the giant component in function of the fraction of removed nodes for the two attacks on the following networks:

A network with N = 104 nodes generated with the configuration model (https://en.wikipedia.org/wiki/Configuration_model) and power-law degree distribution with  γ = 2.5.
A network with N = 104 nodes generated with the hierarchical model (https://en.wikipedia.org/wiki/Hierarchical_network_model).
Which is the most sensitive topological information, clustering coefficient or degree, which, if protected, limits the damage best? Would it be better if all individuals' information (clustering coefficient, degree, etc.) could be kept secret? Why?

Part 2: Use the large graph of the 1st assignment
Repeat the same steps described in Part 1 with the realistic graph you have chosen for the 1st assignment.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Third assignment: The SIR model (mandatory for the exam)
In this 3rd assignment you will map the SIR model into a network. As usual, I recommend to start with a small graph and then, when your code works, to run it on your larger graph used in the other two assignments.

This assignment is a variation of the exercise on social contagion. Here we have 3 different states, S, I, and R, and several parameters (the disease transmission probability p, the minimum amount of time a node remains infected TI, the recovery probability q). We assume discrete time, and use integer numbers to represent distinct, separate "points in time".

Steps:

Take a graph (first a small one and then your graph).

Label all nodes as S (e.g., Susceptible).

Color all S nodes in a color you like (you can take inspiration from https://ncase.me/covid-19/ which is a recommended lecture).

As in exercise num. 8 on social contagion, fix the position of the nodes. Remember that each time you draw a graph with Networkx you get a different layout since drawing algorithms start by placing nodes in random positions and then apply some computational steps to optimize the initial positioning. For more details you can see Graph Layout.

Define the model parameters:
the disease transmission probability p
the duration of the infection. For simplicity, assume that each node spends a minimum of TI time steps in compartment I and after that it can move to compartment R with a given probability q
the number of individuals initially infected, i0

Select i0 nodes to start the diffusion of the virus: change the labels of these nodes into I (Infected), change their color, track the time step at which the infection starts for them.

Repeat the recovery / contagion until all nodes are in compartment R (e.g., Recovered / Removed)
From I to R: for each infected node, if a minimum of TI time steps have elapsed, move the node to the compartment R with probability q, e.g., sample a random number and, if the result is less than q, move the node to the compartment R. Change node label and color, keep track of the time step at which the infection stops.

From S to I: for each infected node, look at their neighbors and spread the contagion with probability p, e.g., for each neighbor of an infected node, sample a random number and, if the result is less than p, a contagion occurs and the neighbor moves to the compartment I. Again, remember to change node label and color. Keep track of the time step at which the infection starts.

Draw the network and save an image to build an animation (see exercise num. 8).

Run your experiment for different values of the parameters and then write a short report describing your choices. Finding the "right" parameters is not easy, we are not domain experts. As a suggestion, since R = p*k, you might start from a known R value, compute the mean degree of your network, and then get p. But this is only a suggestion, any number is fine, the goal here is to see how things evolve, not to estimate the right parameters of the model.
