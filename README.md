# 3DMark Score - The Optimal Build

<p align="center">
<img src="https://github.com/Huski-Git/3DMark-Score/blob/master/Logo.png" width="350">
</p>


## Background Information
In the world of technology, PCs have been a widely used device for a number of reasons, one of which is used for gaming. PC Gaming has been rapidly increasing over the coming decades due to the versatility of the different builds of a computer. Prices of gaming computers can range from around £500 all the way up to north of £15,000 and nowadays PCs are being custom built by individuals or are being built by comissioners.

Once the PC is built they may be content with the completed build however, they may come to the realisation that they may not be able to play a particular game ( E.g. Dark Souls 3 ) due to the fact that the CPU/GPU may not be performing as well as they had hoped and therefore they must purchase a brand new component and waste the original component. Things such as GPU's and RAM cards may be re-used and re-sold, but things such as the CPU, Motherboards tend not to be something that people will sell as it is very difficult to remove the CPU from the Motherboard once inserted due to the fact that the pins that connect the two together are very fragile and as soon as one of the pins are damaged/bent , they cannot be used again.

Certain PC builds will be run certain games smoothly (over 60 frames/sec) and some may not and we are able to have a good idea of whether it does or not by running 3DMark.

3DMark is a benchmarking tool that is run on a particular PC and runs a simulation. This simulation primarily takes into account the GPU and the CPU and sees the different kind of intensities they are able to handle with ease. At the end of the simulation, it provides a 3DMark Score where the higher value indicates that it has a higher average performance throughout all different graphic settings.

The 3DMark Score can be calculated by the following:

<p align="center">
<img src="http://www.sciweavers.org/tex2img.php eq=3DMark%5C%20Score%20%3D%20%20%5Cfrac%7B1%7D%7B%20%5Cfrac%7B0.85%7D%7BGraphics%5C%20Score%7D%2B%20%5Cfrac%7B0.15%7D%7BCPU%5C%20Score%7D%7D%20&bc=White&fc=Black&im=png&fs=12&ff=arev&edit=0" align="center" border="0" alt="3DMark\ Score =  \frac{1}{ \frac{0.85}{Graphics\ Score}+ \frac{0.15}{CPU\ Score}}" width="325" height="75" />
</p>

## Aim
In this project, I will be attempting to predict the 3DMark Score a particular computer build will have and thus we will be able to have an idea of whether they will be running smoothly or not. 

## Motivation 
I am an aspiring data scientist who is all about new tech! I try to keep myself up to date with the latest gadgets that the public has access to. As someone who uses computers on a daily basis for both gaming and work, I like my software running as smoothly/fast as possible , within reason.

## The Data
This data set was kindly provided by [UL](https://benchmarks.ul.com/?_ga=2.90438675.845709998.1584355578-1822667800.1580462866). This data set contains 260,000+ computers of different varieties that took the same 3DMark TimeSpy Extreme simulation

## EDA

I inspected all the variables within the dataset and removed any abnormalities where there were physical limitations. I also removed any simulations that had a 3DMark Score of 0 as it may have indicated that the simulation was interrupted midway / malfunctions. I noticed that there was a linear correlation between the CPU's that were used and the CPU score (a component of the 3DMark Score)

## Count Vectorising

Count vectorising is a method in which we convert word in a row into values instead so we know how many times a particular word has come up in a given PC build. I noticed that Nvidia and Intel were coming up the most frequently, the businesses that currently dominate their respective markets. However, as of 2019, I am aware that AMD are starting to take over Intel and may start to see more AMD CPUs over next decade.

## Modelling

I ran 4 different models : LinearRegression, ElasticNet , DecisionTreeRegressor & RandomForest along with GridSearchCV in order to find the best parameters as well as generalising the data more. I also AdaBoosted all the models in order to improve the model by taking into account the weak classifiers aswell as the strong ones:

<center>
  
|             Model              | Train Score |  Test Score  |
|:------------------------------:|:-----------:|:------------:|
|LinearRegression                |  0.919047   |-7.848261e+14 |
|ElasticNetCV                    |  0.918063   |  0.9185638   |
|AdaBoosted DecisionTreeRegresor |  0.872963   |  0.8723586   |
|Adaboosted RandomForestRegressor|  0.848886   |  0.8473644   |

</center>

I inspected the top 5 coefficients and feature importances to see which one affected the 3DMark Score the most:

![](https://github.com/Huski-Git/3DMark-Score/blob/master/Coefficients_and_features.png)

As expected, we can see that the 2080 ti ( The most powerful GPU to date ) comes up the most frequently throughout all the models. However, it seems that number of GPUs seems to be a larger factor when trying to maximise the FPS ( frames per second ).

## Credits
Special thanks to *P. Virtanen* for helping by giving me insights on what I should look out for.
