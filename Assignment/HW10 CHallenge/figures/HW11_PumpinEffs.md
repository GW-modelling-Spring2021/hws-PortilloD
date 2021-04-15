# HW11 Effects of Pumping

#### Dalia Portillo


#### Model Description

The basic set scenario is as follows. There is a modeling-friendly mountain catchment, bounded by no flow boundaries on three sides. The downgradient boundary has been established as constant head based on the results of a larger-scale model. There is a municipal well in the basin. Some of the water used by the town is recharged after treatment, some is returned to the stream that runs through the basin. Recharge is associated with the mountain block. ET occurs in the basin floor and at a higher rate in the riparian area adjacent to the stream. An agricultural business has proposed to add a well and irrigate crops on a new field. You are to use the model to determine the risks of this in terms of agrochemicals reaching the stream, reduced streamflow, and additional drawdown in the town well. The model is run as three steady state conditions: No Town and No Ag (NTNA); Yes Town and No Ag (YTNA); and Yes Town and Yes Ag (YTYA). Some model parameters are known, others are unknown.

#### The Challenges

<b> 1. Describe the scenario being modeled based on the fixed parameter values and the base model parameter values. Who is the stakeholder? What is their definition of an MOC? </b>

Fixed param: 50 x 50, 3 layer model with csv elevation topo

This is a homogenous aquifer with constant porosity and hydraulic conductivity throughout. 
<br>
</br>
Base MOdel Param: 5 values for each param (not conts)

The conductivity can vary in the horizontal and vertical direction, but here Kv = Kh. There is also ET ocurring only in the riparian area on the surface of the domain. And recharge is applied from the mountians down into the valley.


The stakeholders are either city folk, farm folk, or environmentalists. For this anylsis, the stakeholder is the town which is downstream of the proposed ag well.

MOC (or model of concern) is a decision making criteria that basically alerts the stakeholder is a model(s) produces any information that exceeds a 'limitation' or suggests any concern for certain criteria. In this case, the town will look at parameters that will show if drawdwon at the town well exceeds a certain depth. In other words, if any of the YTYA models show additional drawdown due to the added ag well, then these models will be considered MOC. If analyze_ensemble produces models and few to none of the models are MOC, then good!! If every one is MOC, then no don't even think about the ag well!!


<b>What are the selected 'design' options of the ag facility and the town (return flow fraction, location, field location, etc)? Essentially, paint a picture of what is being represented by the model.</b>










   

  

  

**2. Construct an ensemble with 25 unique parameter sets chosen at random and generate output in current model output.**

I ran my first ensemble with 50 random models. 7 of which were identified as 'non-behavioral' .

**3. Based on your initial random ensemble, what is the most likely additional drawdown at the town well due to pumping the ag well? How confident are you in that response - explain/defend your answer.**

drawdown is most noticable by the farm and isn't greatly added by the town. 

The drawdown will only slightly increase at the town well. I am not totally confident.

<p float="left">
    <img src="figures\3rdrun_dwdn1.png"  width="650" />
    <img src="figures\3rdrun_HdsMOC.png"  width="650" />
</p>

**4. What is the likelihood that the reality (represented by the meager observed data) is best represented by an MOC?**

approximately 31 MOCs were identified by the town. 2 MOCs had the highest liklihoods. These had L = 0.064 and 0.062, respectively. Since only two MOC were liklely, this doesn't show that reality is best represented by MOCs. However, to test this, I input the second highest as a 'seed' and re-ran my test_run_ensemble.

<img src="figures\3rdrun_hgstliklihoods.png"  width="380" /><img src="figures\3rdrun_liklihoods.png"  width="490" />

**5. What is the most likely loss in streamflow at the outflow end of the domain? Justify your answer.**

A few models predicted the stream would go dry sooner than predicted by other models. Combinatin of ET, pumping wells, and insufficient recharge result in lower stream flow (which is of concern to the environmentalists).

<img src="figures\3rdrun_stmflw.png"  width="670" />
<img src="figures\3rdrun_meanstrmflw.png"  width="600" />

**6. Is it likely that either the town or ag well could be contaminated by the ag field? Justify your answer.**

<p float="left">
    <img src="figures\3rdrun_capt1.png"  width="650" />
    <img src="figures\3rdrun_capt2.png"  width="650" />
</p>

**7. Make a set of plots based on ensemble 2 and discuss how each of your answers to the first four questions changed due to adding the MOC-inspired parameter sets.**

<p float="left">
    <img src="figures\4thrun_MOC.png"  width="190" />
    <img src="figures\4thrun_nonbehav.png"  width="480" /></p>
<p float="left">
<img src="figures\4thrun_liklihoods.png"  width="480" />
</p>

Now for this second ensemble, I generated 10 additional models and added an MOC with high liklihood from the first ensemble. This results in 59 total models (not sure why since there should be 60). and we can see dramatic changes. Above in the liklhood, we see more MOCs with higher liklihoods. This means: DONT ADD THE AG WELL!

<img src="figures\4thrun_hgstliklihoods.png"  width="380" /><img src="figures\2ndrun_prevalence.png"  width="490" />

<p float="left">
    <img src="figures\4thrun_dwdn1.png"  width="650" />
    <img src="figures\4thrun_capt1.png"  width="650" />
    <img src="figures\4thrun_capt2.png"  width="650" />
</p>

<img src="figures\4thrun_strmflw.png"  width="670" />
<img src="figures\4thrun_stmflw1.png"  width="670" />

<img src="figures\4thrun_summliklihoods.png"  width="680" />

<p float="left">
    <img src="figures\leftbnd_xsec.png"  width="200" />
    <img src="figures\col20_xsec.png"  width="200" />
    <img src="figures\col48_xsec.png"  width="200" />
    <img src="figures\col49_xsec.png"  width="200" />
</p>

<img src="figures\topbnd_xsec.png"  width="200" />
<img src="figures\row20_xsec.png"  width="200" />
<img src="figures\row49_xsec.png"  width="200" />


```python

```
