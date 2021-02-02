# Challenge #3: Box Model - Flopy

#### Dalia Portillo

For this assignment, we used Flopy to model a homogeneous 'box' with a low k inclusion at the center making the entire model heterogenous.

##### Explain why the values are not constant along the boundary (relate to the definition of a Type I boundary). Explain why the flow distributions are the same for the left and right boundaries.

<img src="noundary_fluxes.JPG" alt="Drawing" style="width: 307px;"/>

*Figure 1 Flow along the left and right boundaries*


In a Type I boundary, the head is specified at that boundary. When the K is known within the model, the flux will adjust to meet the boundary conditions and the K distribution. In this case, we see flow at the top and bottom to be the same value. In the middle, however, the flow decreases dramatically. This is because the low K inclusion in the center allows for the flow to continue around these zones pushing only a small amount at a lower rate. So what does this look like at the center?

##### Add a plot of the left-to-right flow along a line that passes through the center of the inclusion. What can you learn from comparing this distribution to that seen on the boundaries?

<img src="fluxes.JPG" alt="Drawing" style="width: 300px;"/>

*Figure 2 Fluxes at the boundaries and down the center*

In figure 2 the flow pattern differs greatly from figure 1. This illustrates how the flow moves around the low permeable zones. Flow increases because the flow path is now longer as flow moves along and around the low K zone and we see a dramaticallylower flux within the zone as flow struggles to find an easier route. This influeces the dip we see in Figure 1 which a smaller flux as a result of the low k zones.

##### Calculate the total flow into (and out of) the domain.
##### Use this to calculate the Keq of the heterogeneous system with the K values as given in the starter code. Repeat this calculation for the following K values for the inclusion (keeping the background K as it is given): 0.01, 0.1, 1, 10, 100.

qin = qout

The estimated total flow is approximately 100 cubic meters/d (when averaged between all changes of K inclusion). The following are the calculated values for Keq for each K inclusion:


|K inclusion (m/d) |Keq (est. m/d)|
|------|-------|
|0.01|0.9487|
|0.1|0.9664|
|1|1.0416|
|10|1.1168|
|100|1.1338|

##### Can you draw any general conclusions about the impact of high or low K heterogeneities on the equivalent K for the flow system examined? 

##### Does the equipotential distribution depend on the absolute or relative K values for the background and the inclusion (e.g. K_background = 1 and K_inclusion = 0.1  vs  K_background = 10 and K_inclusion = 1?)? How would you use the model to test your answer?

On orders of 10, there isn't a ton of change for Keq. This suggests that media with heterogeneity of three orders of magnitude difference will likley shift the Keq of the system than a difference of one order of magnitude. This could also mean that Keq will liklely ignore small, subtle differences in miganitudes of the hydraulic conductivies. Does this depend on the size of distribution of the K inclusion?? Probably not, but I don't know...yet.

I think the equipotential contours depends on the relative K rather than absolute. We see this by comparing the head distributions for each change of K inclusion.

<img src="K_arth.JPG" alt="Drawing" style="width: 320px;"/><img src="khasrm.JPG" alt="Drawing" style="width: 310px;"/>
*Figure 3 Comparison between Keq and K arithmetic* *Figure 4 Comparison between Keq and K harmonic mean*


```python

```
