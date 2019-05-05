# Social_Network_Analysis

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

```{r}
friend<-read.csv("best.friends.csv", header=TRUE)
getOn<-read.csv("get.on.with.csv", header=TRUE)
workWith<-read.csv("work.with.csv", header=TRUE)
```

```{r}
# cleaning friend dataset
f.EDGE<-count(friend, from, to)
f.VERTEX<-unique(select(gather(friend, type, student, -gender.from, -layerID), 4))
f.GNEDER<-unique(select(friend, 2,4))

# cleaning friend getOn dataset
g.EDGE<-count(getOn, from, to)
g.VERTEX<-unique(select(gather(getOn, type, student, -layerID, -gender.from), 4))
g.GNEDER<-unique(select(getOn, 2,4))

# cleaning friend workWith dataset
w.EDGE<-count(workWith, from, to)
w.VERTEX<-unique(select(gather(workWith, type, student, -layerID, -gender.from), 4))
w.GNEDER<-unique(select(workWith, 2,4))

```

#### Visualize the Networks

Create a graph for each of the data sets. Visualize each of the graphs and color the nodes according to gender. Save pdfs of the graphs in this directory for upload to Github.

```{r}
# network for friend dataset
g1<-graph.data.frame(f.EDGE, vertices=f.VERTEX, directed=TRUE)

plot(g1, layout=layout.fruchterman.reingold, edge.arrow.size=0.1)
plot(g1, layout=layout.circle,edge.arrow.size=0.3,vertex.color=f.GNEDER$gender.from)

# network for getOn dataset
g2<-graph.data.frame(g.EDGE, vertices=g.VERTEX, directed=TRUE)

plot(g2, layout=layout.fruchterman.reingold, edge.arrow.size=0.1, vertex.color=g.GNEDER$gender.from)

# network for getOn dataset
g3<-graph.data.frame(w.EDGE, vertices=w.VERTEX, directed=TRUE)

plot(g3, layout=layout.fruchterman.reingold, edge.arrow.size=0.1, vertex.color=w.GNEDER$gender.from)

```

![friend](https://github.com/ab4499/Social_Network/blob/master/network%20for%20friend%20dataset.pngs=200)
![friend2](https://github.com/ab4499/Social_Network/blob/master/network%20for%20friend%20dataset2.png "github")



