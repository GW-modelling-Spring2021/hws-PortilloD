# Transpire
Sembrar semillas hasta que crecen los raices

Using ET package in MODFLOW


##### Dalia Portillo


A flopy code is provided that recreates the 3D homogeneous box model with constant head boundary conditions. The aquifer is now defined as unconfined. Use this to explore the combined impacts of recharge, ET, and pumping on an unconfined aquifer.

The model that is provided is set up for a homogeneous medium. There is a well located at [0,15,15], but it is not being pumped. The background recharge rate is zero. There is a region of localized recharge in [6:10, 6:10] - in python terms - with a recharge rate of 5e-4 m/day. ET occurs over the entire domain at a rate of 5e-5 m/day and an extinction depth of 3 m. The left and right boundaries have constant heads of 15 and 5, respectively.

#### For the initial boundary head values and recharge and ET rates, establish the flow across the boundary versus y-distance along the left (15 m) and right (5 m) boundaries. Plot the equipotentials and flow vectors in plan view and outline (hand draw) the area that would be affected by recharge (i.e. if it were contaminated). Also show a contour plot of the steady state ET flux in plan view. No well is currently pumping.

<p float="left">
   <img src="BoxModel_vectors1.png" width="350" />
   <img src="ETCountrs.png"  width="340" />
   <img src="BndyFlows.png" width="310" />
</p>

*Figure 1 Flow vectors with local recharge and ET across entire domain*

*Figure 2 ET flux contours across the domain*

*Figure 3 Flow along left and right boundaries*

Immediately we notice the similarity between the contour head pattern and ET distribution pattern in figures 1 and 2. We can also see in figure s 1 and 3 that flow is increasing along hte lower left boundary to to compensate for any loss out of the right boundary.

#### Change the extinction depth. What impacts does this have?



<p float="left">
  <img src="head5.png" width="300" />
  <img src="head10.png"  width="300" />
  <img src="head15.png" width="300" />
    
</p>

<p float="left">
  <img src="ETCountrs1.png" width="320" />
  <img src="ETCountrs.png"  width="320" />
  <img src="ETCountrs5.png" width="320" />
  <img src="ETCountrs10.png" width="320" />
</p>

*Fig 4 Head Transect for Ext depth = 5m*

*Fig 5 Head Transect for Ext depth = 10m*

*Fig 6 Head Transect for Ext depth = 15m*

*Fig 7 ET flux for ext depth = 1m*

*Fig 8 ET flux for ext depth = 3m*

*Fig 9 ET flux for ext depth = 5m*

*Fig 10 ET flux for ext depth = 10m*


Immediately we notice how MODFLOW linearizes ET. As the extinction depth increases, we can see the rate of ET also increases across the domain. Anything above 10, however, doesn't converge. This is becasue anything below out saturated thickness or water table, we are 'drowning' our plants and transpiration cannot occur. Below explains why this is so.

#### Explain, conceptually, how MODFLOW is representing ET. How does this compare to your intuitive understanding of ET in the real world

<p float="left">
  <img src="headw_1.png" width="300" />
  <img src="transpire.png" width="320" />
</p>


*Fig 11 MODFLOW distribution of head from left to right boundaries for ext depth = 5m*

*Fig 12* Interpretation of Transpiration flux with depth below surface https://pubs.usgs.gov/tm/tm6a39/pdf/tm6a39.pdf*

Evaporation from subsurface occurs above the water table where there is enough energy to "pull" water up from the ground. Max potential evaporation is at the ground surface and decreases with depth - harder to evaporate deeper because the temperature is lower and requires more energy. Soil is very humid (~99 relative humidity in most cases). Deeper in the soil, there is essentially no evaporation, it drops off very sharply at the water table.  This is in real life - however, MODFLOW just assumes it decreases linearly with depth.
MODFLOW assumes extinction depth and transpiration rate is linear with extinction depth. So we set a transpiration rate for plants, set an extinction depth, and below that there is no transpiration. Output values from MODFLOW depend on model resolution (the number of grid cells and its respective thickness), but we only get to pick one number for the input. We know this is not physically true as seen in Figure 12. There are other variables that affect root uptake that MODFLOW ignores. The root uptake depends on water pressure - degree of wetness or dryness in the surropunding soil.


```python

```

#### Now start the well pumping, extracting 20 m3/day. How does the well change the zone that is affected by the recharge area? How does it affect the ET map? Write a mass balance for the well - how much water is coming from a boundary? How much is originating as recharge? How do you account for the impact of ET on this mass balance? At steady state, what are the effects of 'capture' by the well?


*Fig 13 Head transect for ext depth = 1*

*Fig 14 Head transect for ext depth = 3*

*Fig 15 Head transect for ext depth = 5*

*Fig 16 Head transect for ext depth = 10*

*Fig 17 ET flux with well for ext depth = 3*

*Fig 18 ET flux with well for ext depth = 5*

*Fig 19 ET flux with well for ext depth = 9*

*Fig 20 ET flux with well for ext depth = 10*

<p float="left">
  <img src="headw_1.png" width="300" />
  <img src="headw_3.png"  width="300" />
  <img src="headw_5.png" width="300" />
  <img src="headw_10.png" width="300" />
</p>
<p float="left">
  <img src="ETCountrs2.png" width="340" />
  <img src="ETCountrs5_w.png" width="320" />
  <img src="ETCountrs9_w.png"  width="320" />
  <img src="ETCountrs10_w.png" width="320" />
    
</p>


<p float="left">
  <img src="BoxModel_vectors1.png" width="390" />
  <img src="BoxModel_vectors2.png"  width="390" />
</p>

<p float="left">
  <img src="BoxModel_vectors2_9.png" width="340" />
   <img src="BoxModel_vectors2_10.png" width="340" />
</p>


*Fig 21 FLow Vectors with local recharge and ET everywhere*

*Fig 22 FLow Vectors with well pumping at (15,15)*

*Fig 23 FLow Vectors, Head Contours, well pumping for ext depth = 9m*

*Fig 24 FLow Vectors, Head Contours, well pumping for ext depth = 10m*

###### mass balance

The flow into the domina and flow are not the same. the way the model handles any loss is by increasing the inflow. This means that there is more volumetric flow leaving the system so the model tries to make up for that loss by supplying more water across the left  boundary to maintain the system's mass balance. But can we quantity how much is supplied by recharge and boundary? Can we quantify how much is lost to evapotransipration? Below we tackle this problem two ways. First we use a simple mass balance expressing the total change in storage is equal to all flow out minus all flow into the domain. 

$ \Delta S = Q_out - Q_{in} =  Q_{well} + Q_{ET} - (Q_{re} + Q_{bndy}) $ 

<img src="mass.png" width="330" />

We are given the discharge of the well (Q_well = 20 m^3/d) and we know the flux of recharge (rech = 5E-4) and the famring area (area = 400 x 400 m^2). So we can derive the volumetric flow supplied by the recharge zone. We can also calculate the volumetric flow across the left boundary. However, this situation is only concerned with the zone/area of which is supplied to the well - which we call the 'capture zone.' So we only sum the flow across this small area along the left boundary and this is approximately 50 m^3/day.


```python
Q_well = 20.        #m^3/d
Q_bndy = 49.47      #m^3/d               sum flux from rows 9 to 17 over the left boundary

# find Q_re
A_re = 400 * 400   #m^2                 area of recharge
recharge = 5E-4    #m/d

Q_re = recharge * (A_re *(1/5))       # assuming only 1/4 of the area is captured by the well

# find Q_Et
# By mass balnce
Q_ET = Q_re + Q_bndy - Q_well
print(str(Q_ET)+ ' m^3/d') 
```

    45.47 m^3/d
    


Similarly, we can also pull ET values from the ET array starting from the left boundary until column 15 (where the well is located) and sum each column into a single array. This will represent all the ET to the left of the well. If we add this last array and normalize over the area of the capture zone, we get <b> Q_ET = 1.625 m^3/d </b> which is completely different than solved above. <span style="color:blue"> This suggests that the simple mass balance equation above does not provide true to accuate values becasue we are not accounting for the loss in the domain over all. We know this value ahould be small, so Q_et pulled out from the array should provide a closer reading to the true flow taken out by ET.</span>


#### Team Discussions:

##### Team partner: Jill

Jill began with a comparative discussion of ET in the real world versus in MODFLOW. We discussed how MODFLOW interprets ET linearly as a function of head and is applied at the boundary/outside the domain.

I explained how to plot the ET contours and how the model responded to a changing the extinction depth. We tried a myriad of values but found that the model does not work for values less than one! This could be due to MODFLOW only taking in whole numbers or that it isn't possible to have an extinction depth in a fraction of a cell - in other words the model either has ET or doesn't. (I think)...

Mass balance proved to be difficult to understand, as well the 'convertible cells' that MODFLOW changes in response to our inputs.