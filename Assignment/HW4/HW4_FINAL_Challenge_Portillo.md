# Challenge #4 Well, Well
### *Influences of wells in our models*

### Dalia Portillo

#### Move the location of a well around the domain and analyze what changes. For the initial well location, plot the flow into the left (constant head = 20) and out of the right (contant head = 10) boundaries. Explain why the values are not constant along the boundary (relate to the definition of a Type I boundary). Explain the shapes of the flow distributions and why they are not the same for the left (inflow) and right (outflow) boundaries.

<!--<p float="left">
  <img src="well1_bndyFlow.JPG" width="292" />
  <img src="well2_bndyFlow.JPG"  width="299" />
  <em>Figure 1 Flow along boundaries for well loacted at 10,15</em>
    
  <em>Figure 2 Flow along boundaries for well loacted at 12,12</em>
</p>This is commented out. -->


<p>
  <figure><img src="well1_bndyFlow.JPG" width="292"/><figcaption>Figure 1 Flow along boundaries for well loacted at 10,15</figcaption></figure>
  <figure><img src="well2_bndyFlow.JPG" width="299"/><figcaption>Figure 2 Flow along boundaries for well loacted at 12,12</figcaption></figure>
</p>

In Figures 1 and 2, we see an intereting dfference between how the flux changes along the left and right boundaries. Firstly, the lines aren't straight. Why? This is because the model tries to iteravely solve and the resulting solution must meet the specified boundary conditions (i.e. H_left =20 and H_right =10 and no flow boundaries). These curves form assuming steady state conditions have been achieved and that flow is perfectly horizontal. The well creates a low pressure point so that water flows from high to low pressure and is able to draw in from what we call a zone of influence which is the extent to which water is influenced to move towards the well. We can also calcuate how much the well is pumping out by the area between the two curves. Figures 1 and 2 should ideally have the same pumping rate.

#### Add a series of the left-to-right flow along a line that passes through the center of the domain [:,12]. How do you interpret the flow along this transect? Hint, also look at the flow along a transect just upgradient from the well [:,11].

<!--<p float="left">
  <img src="well1_bndyFlows.JPG" width="292" />
  <img src="well1_bndyFlows11.JPG"  width="299" />
</p>

<p float="left">
  <em>Figure 3 Flow along boundaries for well loacted at 10,15 column 12</em>
    
  <em>Figure 4 column 11</em>
</p> This is commented out. -->


<p float="left">
  <img src="well2_bndyFlows11.JPG" width="288" />
  <img src="well2_bndyFlows.JPG"  width="299" />
</p>

*Figures 3 & 4 Flow for well located at 12,12 through center columns*

The main difference here is Figure 4 displays flow dropping (green line) after increasing dramatically. Flow doesn't actually stop, but reaches a stagnant point that represents flow is drawn into the well, but some part of the flow still goes around the well since flow is perfectly horizontal.

#### Then, look at the plot of equipotentials and flow vectors. Describe how water flows through the domain. To aid in your description, draw a line through all of the flow vectors that terminate in the well. This approximates the capture zone of the well. Use this to refine your description of the flow system, being as specific as possible about where water that ends up being extracted by the well originates on the inflow boundary.


<img src="well2_headcontours.JPG"  width="370" />

*Figure 5 Equipotential contours and flow vectors throughout the domain*

By mass balance, water coming in is equal to the water going out. This applies to the macroscale (the overall domain) and through each cell (the microscale). So here in our model, water flows in from the left and right boundaries and is parallel to the no-flow boundaries on the top and bottom. However, in our vector plot, we see flow coming in perfectly horizontal to the boundary but only a small part of that terminates into the well. This is called the capture zone which water pulled from storage flows directly into the well, and otherwise will flow horizontally from high hydraulic gradient to low hydraulic gradient as we can see from the vectors.


#### Then, look at the plan view drawdown plot. Why aren't the drawdown contours circles? Either explain why this is correct, or fix the plot.


<img src="well2_dwdwn.JPG" alt="Drawing" style="width: 270px;"/>

*Figure 6 Drawdown contours*


Drawdown isn't perfectly a circle because the no-flow boundaries cause and elliptical shape - flow needs to be parallel to these boundaries and head gradient is perpendicular to no-flow sides. Ideally, flow is perpendicular to each of these contours. The distance from the boundary also affects the system: close to the well, we see small contour changes, but father away the contours tend to be affected by the boundaries. The shape is due to the stretching and compressing in one direction than the other. It is compressing due to the no flow boundaries and stretching along laterally towards the constant head boundary. The diamond shape in center is lkely due to low resolution, or not enough data to interolate from to create a smooth curve.

#### Move the well to [0,5,5]. Use all plots necessary to describe fully how water is flowing through the domain with the well in this location. Be sure to include the drawdown plot in your discussion - compare this plot to the equipotentials and flow vectors. Something is not right about how the well location is shown. Fix it and explain what was wrong!

<!--<img src="well3_bndyFlow.JPG" alt="Drawing" style="width: 288px;"/>
<img src="well3_bndyFlows.JPG" alt="Drawing" style="width: 288px;"/>
<img src="well3_dwdwn.JPG" alt="Drawing" style="width: 288px;"/>
<img src="well3_headcontours.JPG" alt="Drawing" style="width: 288px;"/>
 This is commented out. -->

<p float="left">
  <img src="well3_bndyFlow.JPG" width="288" />
  <img src="well3_bndyFlows.JPG"  width="288" /> 
  <img src="well3_dwdwn5.JPG" width="288" />
  <img src="well3_headcontours.JPG" width="375" />
</p>

*Figure 7 Well at 5,5 boundary flows*

*Figure 8 Well at 5,5 boundary flows and flow at center of domain*

*Figure 9 Drawdown Contours*

*Figure 10 Equipotential contours and flow vectors for well at 5,5*

Moving the well to [5,5] is a perfect example to see how boundaries and wells influence flow. From Figure 9, we can see the drawdown is distorted by the no-flow boundary and the constant head boundaries. When the contours are closer together, this indicates a high gradient and faster flow, and the opposite when the contours are further apart (columns >10).
Figures 7 and 8 show the faster flux from the left around row 5 (or Ly =~500). Becuase the well is closer to the corner or to the left boundary in this scenario, we see a greater influence from the well on the aquifer storage from this capture zone. Additionaly, the boundaries are mathematically made up by artifically placing an image the exact same distance across the boundary. Meaning another well pumping at the same rate is placed 10 units vertically from our current well inducing a no-flow boundary (since flow is equal and opposite, ideally q=0). Similarly we can apply an image well across the left boundary that is injecting at the same rate for a continous supply of water.
While flow at the boundary increases since it is next to the well, further away we see no response in flux. Here flow continues unbothered from left to right. This tells us that the extent to which the well influences flow is likley small. If the well didn't exist, we'd see flux in to the domain equal to flux out, and the value would be constant.


```python

```
