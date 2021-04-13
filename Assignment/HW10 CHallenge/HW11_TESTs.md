#### Model Description

The basic set scenario is as follows. There is a modeling-friendly mountain catchment, bounded by no flow boundaries on three sides. The downgradient boundary has been established as constant head based on the results of a larger-scale model. There is a municipal well in the basin. Some of the water used by the town is recharged after treatment, some is returned to the stream that runs through the basin. Recharge is associated with the mountain block. ET occurs in the basin floor and at a higher rate in the riparian area adjacent to the stream. An agricultural business has proposed to add a well and irrigate crops on a new field. You are to use the model to determine the risks of this in terms of agrochemicals reaching the stream, reduced streamflow, and additional drawdown in the town well. The model is run as three steady state conditions: No Town and No Ag (NTNA); Yes Town and No Ag (YTNA); and Yes Town and Yes Ag (YTYA). Some model parameters are known, others are unknown.

#### The Challenges

<b> 1. Describe the scenario being modeled based on the fixed parameter values and the base model parameter values. Who is the stakeholder? What is their definition of an MOC? What are the selected 'design' options of the ag facility and the town (return flow fraction, location, field location, etc)? Essentially, paint a picture of what is being represented by the model.</b>

Fixed param: 50 x 50, 3 layer model with csv elevation topo
- constant n
- if Sy > n, then Sy overwrites n in model

Base MOdel Param: 5 values for each param (not conts)
- k val in in vert or horiz
- et in riparian
- ratio streambed k to aquifer k


The stakeholders are: city folk, farm folk, and environmentalists. for this anylsis, the stakeholder is the town

MOC (model of concern) is a decision making criteria...if run/analyze model and few to none of the models are MOC, then good!!
if every one is MOC, then no don't even think about the ag well!!



**2. Construct an ensemble with 25 unique parameter sets chosen at random and generate output in current model output.**

I ran my first ensemble with 50 random models. 7 of which were identified as 'non-behavioral' .

**3. Based on your initial random ensemble, what is the most likely additional drawdown at the town well due to pumping the ag well? How confident are you in that response - explain/defend your answer.**

drawdown is most noticable by the farm and isn't greatly added by the town. We see from the capture zones that YTYA shows a capture zone affecting the stream near the middle of the domain and going dry to the right past column 40.

The drawdown will only slightly increase at the town well. I am not totally confident


```python

```

**4. What is the likelihood that the reality (represented by the meager observed data) is best represented by an MOC?**

approximately 11 MOCs were identified by the town. 2 MOCs had the highest liklihoods. These had L = 0.042 and 0.033, respectively. Since only two MOC were liklely, this doesn't show that reality is best represented by MOCs. However, to test this, I input the second highest as a 'seed' and re-ran my test_run_ensemble.

**5. What is the most likely loss in streamflow at the outflow end of the domain? Justify your answer.**

A few model predicted the stream would go dry sooner than predicted by other models. Combinatin of ET, wells, and insufficient recharge.

**6. Is it likely that either the town or ag well could be contaminated by the ag field? Justify your answer.**

I'm having trouble visualizing the location of the irrigation, recharge and other zones.

**7. Make a set of plots based on ensemble 2 and discuss how each of your answers to the first four questions changed due to adding the MOC-inspired parameter sets.**

<p float="left">
    <img src="figures\2ndrun_MOC.png"  width="190" />
    <img src="figures\nonbehav.png"  width="480" /></p>
<p float="left">
<img src="figures\2ndrun_liklihoods.png"  width="480" />
</p>

Now for this second ensemble, I generated 10 additional models and added an MOC with high liklihood from the first ensemble. This results in 59 total models (not sure why since there should be 60). and we can see dramatic changes. Above in the liklhood, we see more MOCs with higher liklihoods. This means: DONT ADD THE AG WELL!

<img src="figures\2ndrun_hgstliklihoods.png"  width="330" /><img src="figures\2ndrun_prevalence.png"  width="390" />

<p float="left">
    <img src="figures\2ndrun_dwdn1.png"  width="380" />
    <img src="figures\2ndrun_capt1.png"  width="380" />
    <img src="figures\2ndrun_dwdn2.png"  width="380" />
    <img src="figures\2ndrun_capt2.png"  width="380" />
</p>

<img src="figures\2ndrun_streamflow.png"  width="470" />
<img src="figures\2ndrun_stmflw1.png"  width="470" />
<img src="figures\2ndrun_stmflw2.png"  width="470" />

<img src="figures\2ndrun_summliklihoods.png"  width="480" />


```python

```
