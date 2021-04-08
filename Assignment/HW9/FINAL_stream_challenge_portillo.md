# Streams

#### Dalia Portillo

This flopy code simulates flow in a single layer model including a stream that runs along the center column. There is uniformly distributed recharge over part of the domain. There is no ET. The aquifer is unconfined. Let's explore stream-aquifer exchange.

### Model Description

​The model is set up for a homogeneous medium. However, the streambed conductivity changes within *three zones* along the stream. The single-layer domain is 51x51 cells. The cells are 10 m in lateral and vertical extent. Recharge occurs at a rate of 5e-5 m/day in the first 26 rows. The left and right boundaries have defined heads to represent a lake and a river, respectively.

### The Challenges

<b> a) Use these figures to describe the nature (direction/magnitude) of stream/aquifer exchange along the stream. In particular, explain why the leakage changes magnitude or direction where these values change.</b>


<p float="left">
   <img src="flow_hds_lkd.png"  width="625" />
   <img src="pot_surf.png"  width="325" />
</p>

This is give us some insight into what is going on between stream flow and the underlying aquifer below. There is a connection between the stream and aquifer in the middle reach, between rows 20 to ~40. This is where the leakeage to the aquifer is seen increasing in value exponentially. The leakage is influenced by the recharge which supplies additinal flow into the aquifer. The effects of recharge decrease down stream so around row 45, the leakage is zero.




<b> b) Use the head distribution to describe the movement of water across the boundaries and into/out of the stream. </b>

Using the same figures above, we can get a general sense of the movement of water in this system. From the left to the stream (columns 0:25), we have flow into the stream.<span style="color:blue"> This is the 'gaining' portion of the srtream where conductance is low. The head gradient is down from left to right and top to bottom. As we walk along from the top to the bottom, we see the lower part of the river is a losing stream where the cunductance is higher. This means the river is dry and there is little to no connection witht hte aquifer beyond row 43.</span> The lower right corner is like a sink and drawing in the water.





```python

```

<b> c) Choose two things to explore (e.g. impact of streambed K or inflow into the river or recharge rate). Produce a plot for each to compare to the base plots and use the plots to explain the impact of the hydrologic change. </b>

1. I changed the area over which recharge occurs from the top 26 rows to the a small corner in the right. This is simulate a system where rain ocurs in the northest part of the domain. I also reduced the sediment thickness of the stream and decreased the width of the stream from 20 to 8.
This results in NO CONNECTION between the stream and the aquifer. why? Well the river is now too high that flow is almost negligble across the bounds between stream and aquifer. Yet the head contours remain reltivley unchanged as shown by the crossection figures starting from row 10 to row 50.

<p float="left">
    <img src="ibnd.png"  width="225" />
    <img src="xsect_rivrch10.png"  width="280" />
    <img src="xsect_rivrch26.png"  width="280" />
    <img src="xsect_rivrch50.png"  width="280" />
</p>

<left><img src="flow_hds_lkd_riv_rch.png"  width="615" />


```python

```

2. Now I want to know what is the smallest value or combination of parameters that the stream needs to leak into the aquifer without recharge. there are more changes I can make to force a connection but, what I did was decrease the sediment thickness, the stream botom level, and the stream conductance.

Again the head contours doesn't really change dramatically. But this does illustrate that there is a small connectin which allows the water to leak into the aquifer across a small reach of the stream. This occurs around row 20 where we see flow nearly stop and the heads reach approximately 8.1 meters. The river goes dry early on in the middle of the domain. The aquifer on the other hand is still drawing water from the left.

<p float="left">
    <img src="riv3.png"  width="500" />
</p>
<p float="left">
<img src="flow_hds_lkd_riv.png"  width="600" /><img src="3DHead.png"  width="320" /></p>  


