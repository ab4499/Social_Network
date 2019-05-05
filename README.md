# Social_Network_Analysis

![sna1](https://github.com/ab4499/Social_Network/blob/master/graphs/sna1.png "github")

In this project I will generate and analyzing three social networks (also known as graphs or sociograms) based on three different measures. I will be using data from:

Representing Classroom Social Structure. Melbourne: Victoria Institute of Secondary Education, M. Vickers and S. Chan, (1981)

Available from the Index of Complex Networks ([ICON](https://icon.colorado.edu/#!/))

The data were collected by Vickers & Chan from 29 seventh grade students in a school in Victoria, Australia. Students were asked to nominate their classmates on a number of relations including the following three "layers":  

1. Who do you get on with in the class?  
2. Who are your best friends in the class?  
3. Who would you prefer to work with?  

There is a dataset for each of these questions.

#### Data Wrangling

Manipulate each of the data sets so that it is suitable for building a social network using iGraph.


#### Visualize the Networks

Create a graph for each of the data sets. Visualize each of the graphs and color the nodes according to gender. Save pdfs of the graphs in this directory for upload to Github.


![friend](https://github.com/ab4499/Social_Network/blob/master/graphs/Friend.png "github") 
![friend2](https://github.com/ab4499/Social_Network/blob/master/graphs/Friend2.png "github")
![geton](https://github.com/ab4499/Social_Network/blob/master/graphs/Geton.png "github") 
![workwith](https://github.com/ab4499/Social_Network/blob/master/graphs/Workwith.png "github")

#### Centrality Measures

Who in the class has the highest degree centrality for each measure?

Measure Degree Centrality
![centrality](https://github.com/ab4499/Social_Network/blob/master/graphs/centrality.png "github")

In friend dataset, the 8th student has the highest degree centrality 1.
In getOn dataset, the 11th student has the highest degree centrality 1.
In workWith dataset, the 14th student has the highest degree centrality 1.

Who in the class has the highest closeness centrality?

Measure Closeness Centrality
![closeness](https://github.com/ab4499/Social_Network/blob/master/graphs/Closeness.png "github")

How does **betweeness centrality** differ from **degree centrality**?

Betweeness Cntrality cares how critical anode is to a network in its functioning as a bridge point between other nodes in the network. It quantifies the number of times a node acts as a bridge along the shortest path between two other nodes. Degree centrality using eigen vector will calculate both the number of nodes a node is connected to and the sifnificance of nodes this node is connected to.

#### Simple structures

Count the number of dyads and the number and type of triads.

[Documentation](http://igraph.org/r/doc/dyad_census.html)

Within the existing connections, getOn has more mutual connections than the asymmetric connections. This indicates that when it comes to friendship and work partnership, there tend to be more asymmetric connections.

[Documentation](http://igraph.org/r/doc/triad_census.html)

A similar aspect in the triad metrics is that there are more complete graph (A<->B<->C, A<->C) in getOn set compared with two other groups.

#### Cliques

The following steps are done with [clique functions](http://igraph.org/r/doc/cliques.html)

What is the size of the largest clique(s) in each of the three networks?
```{r}
clique_num(g1)
clique_num(g2)
clique_num(g3)
```

Find the cutpoints (articulation points) for each of the three networks. 
```{r}
articulation_points(g1)
articulation_points(g2)
articulation_points(g3)
```
Both friend and WorkWith network has 13 as the articulation point. This means that if we remove this point, the graph will become 2 separate components.

#### Putting it all together

In general, no student is completely separated in any of the three networks, showing a relatively good overall connection within the class. Particularly, students like 8th, 11th, 14th, 16th, 20th, 21st, 22nd, 23rd have quite high degree centrality in all the networks, indicating that these students serve as important connecting bridges to other students/cliques. There are more mutual and asymmeric dyads in getOn dataset than the other two. And the largest clique in each of the network is around 10 people. We also see a few students that do not have a very close connection with larger groups compared with others (like the 18th and 25th students, both of them only connect to the 13th student and one another in friend and workWith networks). Teachers may want to taking advantage of cliques and students with high degree centrality to make them spread good behaviral impact/important information among other students. Also, teachers should pay more attention to students that are less connected with others, and help them to establish stronger relationship in cooperation/friendship with other students. 

I would also want to know the accumulated centrality of students with the three layers together, and order the different layers (I would regard friendship as the closest relationship, and can work with as the second level, and get on well as the third level) to evaluation how students connect with each other on different level of layers. I would also like to distinguish the "from" and "to" in the network analysis to see who receive/send the most connection (degree in/degree out). 

This did remind me of my middle school, where there are many small cliques, close circle among my classmates, and there are certain popular students who are close to many others. 
