# Data Visualization Project

## Data

The data I propose to visualize for my project comes from the **NYPD Motor Vehicle Collision databases**. The NYPD keeps a record of all reported collisions involving vehicles where someone is injured or killed, or where there is at least $1000 worth of damage. One dataset, [Motor Vehicle Collisions – Crashes](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95/about_data), contains details such as the **date and time of the collision**, **location**, and the number of people injured or killed. Complementing this is the [Motor Vehicle Collisions – Vehicles](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Vehicles/bm4k-52h4/about_data) dataset, which records information about the **vehicles involved**, including make, model, and year. By combining these datasets using their shared collision ID, it is possible to uncover a variety of insights into crash patterns and vehicle involvement across NYC.

## Questions & Tasks

The following tasks and questions will drive the visualization and interaction decisions for this project. The main question here would be:
 * Under what conditions is it most dangerous to drive in NYC?

But this could be broken down into multiple questions
 * What time during the day do most accidents occur?
 * What time of the year do most accidents occur?
 * Are there certain burroughs in NYC that are more dangerous than other when driving?
 * Are there certain vehicles which are more likely to be in accidents than others?

## Sketches

Some sketches of potential visualization include:
image.png

This visualization highlights the number of vehicles involved in collisions using a standard bar chart. The x-axis represents the different vehicle makes, while the y-axis shows the frequency of accidents associated with each make. This chart helps address the question posed earlier and offers insight into which vehicle brands are more frequently involved in crashes—potentially pointing to patterns worth further investigation or caution. Another potential representation of the same data could be seen below:

image.png

Although this implementation covers the same data, it is more difficult to determine the relative quantities amongst the different car makes. The bar chart would be better in this scenario, but the bubble chart could be a potential pick.


## Prototypes

I’ve created a proof of concept visualization of this data. It's a stacked bar chart highlighting the number of accidents at the different hours of the data. The stacked bar chart includes accidents in which an injury has been reported, a death has been reported, or simply $1000 worth of damage has been caused. Although we cannot see anything corresponding to the number of deaths for each hour, the bar is there but much smaller than the others. From the visualization, we can see that the number of accidents peak at around 4-5pm, which makes sense as people are mostly leaving work at this time. The "safest" time to drive based off this chart is around 2-5 am.

[![image](https://user-images.githubusercontent.com/68416/65240758-9ef6c980-daff-11e9-9ffa-e35fc62683d2.png)](https://vizhub.com/JoseMorales7/8f5a29dbad174b1a90e7671b09b654e2)



## Open Questions

One uncertainty I have about the third subquestion is how best to implement an interactive map of the New York City boroughs in a way that is both effective and visually appealing. I assume I would need to rely on pre-made geographic assets for the borough boundaries, but ensuring the interactivity is intuitive and well-executed feels like a potential sticking point.


## Milestones

In week 1, I’ll focus on getting the data set up and cleaned, merging the two datasets on collision ID, and doing some basic analysis like looking at crashes by time of day, day of week, borough, and vehicle make. I’ll also sketch out some quick draft plots just to confirm that the questions I want to answer can actually be supported by the data.  

In week 2, I’ll build my first set of static visualizations in Python to tackle each of the subquestions, like crashes by time of day, seasonal trends, borough comparisons, and vehicle makes. Alongside that, I’ll figure out which chart types feel the most effective and start drafting short explanations to go with each one.  

In week 3, I’ll start moving from static plots into interactive prototypes using D3 and React. At least two of these will get some basic interactivity like filters, hover tooltips, or zooming. This is also when I’ll spend more time refining the look and feel of the visuals and testing them on a couple of people to see if they make sense.  

In week 4, I’ll work on the interactive borough map. That means finding or preparing the geographic assets for NYC’s boroughs, hooking them up with the crash data, and making the map interactive so people can hover, click, or filter by borough. I expect this step might need some debugging, especially with handling a large dataset.  

In week 5, I’ll bring everything together into a single report. I’ll make sure the design looks consistent across all the charts, add clear labels, legends, and annotations, and check that each research question has at least one visualization addressing it. I’ll also start writing down the methods I used and decisions I made along the way.  

In week 6, I’ll focus on polishing everything. This includes cleaning up my code and repo, making sure the visuals are fully finished, and checking for clarity and accessibility.  

