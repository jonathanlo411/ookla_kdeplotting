# Ookla Server KDE Plotting
This notebook was created to map Ookla server locations as a [**Kernel Density Estimation (KDE)**](https://en.wikipedia.org/wiki/Kernel_density_estimation) geographic map plot. Currently, it maps server locations in the contiguous United States and World Map at varying levels of granularity.

## Running Notebook
The notebook using [Geopandas](https://geopandas.org/en/stable/) and [Geoplot](https://residentmario.github.io/geoplot/). This means that you will need to set up a virtual environment. Personally, I used [this](https://medium.com/analytics-vidhya/fastest-way-to-install-geopandas-in-jupyter-notebook-on-windows-8f734e11fa2b) Medium article by [Tanish Gupta](https://tanish-gupta.medium.com/) to set up my environment. 

To run the notebook:
1. Activate conda virtual env that has Geopandas by running the following command in Anaconda Prompt
 ```
 conda activate yourenv
```
2. Launch notebook menu using:
```
jupyter notebook
```
3. Navigate to notebook and run

## Details
One of things you'll notice when you look at this repository is the folders `world` and `world_transparent` that contain KDE geoplots of only continents. This is caused by the inability to control the granularity when plotting a KDE geoplot using Geoplot. To remedy this, I...
1. Plotted points continent by continent and saved the figs to `.png` files.
2. Drew [transparencies](https://en.wikipedia.org/wiki/Transparency_(graphic)) everywhere on the image except for the mapped area and country borders.
3. Overlay the images and create a legend/scale using [Figma](https://www.figma.com/).

An issue I faced when doing this was the scale. When I plotted continent by continent, each continent would have the same max level of density (regardless of actual density relative to each other).
![](https://cdn.discordapp.com/attachments/579707526610681857/941869510544220160/unknown.png)

> Notice how Africa has the same density as Europe and other continents

To fix this, I created individual color scales based on the number of servers on each continent relative to the continent that has the most servers (South America). This allowed the scale to be accurate.
![](https://cdn.discordapp.com/attachments/579707526610681857/941930535377313852/unknown.png)
> Africa is considerably less intense compared to before

## Potential Improvements
1. The world map could have a higher level of granularity. However, this would mean plotting a KDE geoplot for every single country and following the process listed above.
2. Due to convenience of the packages, I filtered out some countries (Kosovo (XK), East Timor (TL), etc.) . It would be possible to hard code these situations.
