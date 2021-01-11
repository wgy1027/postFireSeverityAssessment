
# National Burned Area Emergency (BAER)
## BAER Team
### Mission

The National Burned Area Emergency Response Coordinators Group exists to provide program recommendations and guidelines for implementing Burned Area Emergency Stabilization and Rehabilitation programs. They accomplish this by functioning as a seamless interagency group to coordinate program issues, implementation, training, oversight, sharing of information, and evaluation.

### Who

While many lands sustaining wildfire are naturally stimulated and recover to healthy conditions, some catastrophic fire can damage the land, causing threats to human life, property, and biological and cultural resources downstream. In these situations, land managers may decide to apply "first-aid" immediately after the wildfire to help stabilize and repair the landscape.

BAER teams are staffed by specially trained professionals: hydrologists, soil scientists, engineers, biologists, vegetation specialists, archeologists, and others who evaluate the burned area and prescribe emergency stabilization treatments. A BAER assessment usually begins before the wildfire has been fully contained.

The interdisciplinary teams determine the need for, prescribe, and sometimes implement, emergency treatments to minimize threats to life or property or to stabilize and prevent further unacceptable degradation to natural and cultural resources resulting from the effects of wildfire. Based on the assessments written by team specialists, treatment recommendations are made to affect agencies for the protection of human life, health and safety, critical cultural and natural resources, and infrastructure.

### Objectives

The objectives set for the BAER team will largely be determined by land management standards, which apply to the area impacted by the fire and the severity of the fire on that area. When the need for a BAER team is recognized and assembled, its mission in the fire area must coordinate with the incident management team and safe integration with the ongoing strategies and tactics.

## Method
This soil burn severity dataset was derived from Sentinel 2 data and field validated by a Forest Service Burned Area Emergency Response (BAER) team. It is based upon an initial Burned Area Reflectance Classification (BARC) dataset created by analyzing satellite imagery. A pre-fire and post-fire Sentinel 2 scene were processed to develop a differenced Normalized Burn Ratio (dNBR) image. The dNBR image attempts to portray the variation of burn severity within a fire and captures the combined effects of the fire to vegetation and soil components of the ecosytem. The preliminary BARC dataset was assessed by a Forest Service BAER team and modified, if necessary, based on field conditions. Purpose: These data were created by the USDA Forest Service Geospatial Technology and Applications Center (GTAC) to support Burned Area Emergency Response (BAER) teams.

Process Description: These data products are derived from Sentinel 2 data. Pre-fire and post-fire scenes are analyzed to create a differenced Normalized Burn Ratio (dNBR) image. The dNBR image portrays the variation of burn severity within the fire. The pre- and post-fire images are terrain corrected and further processed to convert top of atmosphere reflectance. The Normalized Burn Ratio (NBR) is computed for the pre- and post-fire images using the following formula: (NIR Band - SWIR Band) / (NIR Band + SWIR Band) = NBR

The Differenced NBR is computed to determine severity by subtracting the post-fire NBR from the pre-fire NBR: (PreNBR - PostNBR) = dNBR
            
One example of BARC threshold set is:
Original BARC thresholds:
Unburned/Low threshold = 76
Low/Moderate threshold = 118
Moderate/High threshold = 217

General descriptions of the severity classes are below:
(1) Unburned / Very low: The area after the fire was indistinguishable from pre-fire conditions. This does not always indicate the area did not burn (i.e. canopy may be occluding the burn signal).

(2) Low:      Areas of surface fire with little detected change in cover and little detected mortality of the dominant vegetation. Little to no change in the soil color, structure and condition occured.

(3) Moderate: This severity class is between low and high and means there is a mixture of detected effects on the dominant vegetation.

(4) High:     Areas where the canopy has high to complete consumption. Changes to soil structure, color and condition are significant and hydrophobicity may have occured.

[Online Linkage](https://fsapps.nwcg.gov/baer/baer-imagery-support-data-download)

# Rapid Assessment of Vegetation Condition after Wildfire (RAVG) program
The Rapid Assessment of Vegetation Condition after Wildfire (RAVG) program assesses post-fire vegetation condition for large wildfires on forested National Forest System (NFS) lands. RAVG data are produced by the USFS Geospatial Technology and Applications Center (GTAC) by way of a multispectral change detection process. Standard products are calculated using regression equations that relate derivatives of Landsat or other similar imagery to three estimates of burn severity: percent change in basal area (BA), percent change in canopy cover (CC), and a standardized composite burn index (CBI).

Standard thematic products include 7-class percent change in basal area (BA-7), 5-class percent change in canopy cover (CC-5), and 4-class CBI (CBI-4). National mosaics of each thematic product are prepared annually.

RAVG data are produced to assist in post-fire vegetation management planning. They are intended to enhance decision-making capabilities and reduce planning and implementation costs associated with post-fire vegetation management. RAVG analysis provides a first approximation of areas that may require reforestation treatments after a fire. This initial approximation may be followed by site-specific diagnosis and development of a silvicultural prescription to more precisely identify reforestation needs.
## Method
RAVG burn severity data are derived from multi-spectral imagery. A Relative Differenced Normalized Burn Ratio (RdNBR) image, which portrays the variation of burn severity within a burn area, is derived from a pair of multi-spectral images: a post-fire scene and a corresponding pre-fire scene. Whenever possible, the RAVG project uses Landsat images that have been geometrically rectified, terrain corrected, and converted to top-of-atmosphere (at-satellite) reflectance. The following process was developed for Landsat imagery but applies to other multi-spectral satellite imagery that includes a near-infrared (NIR) band and a short-wave infrared (SWIR) band (approximately 2.2 micrometers).

The Normalized Burn Ratio (NBR) is computed for each image using the NIR and SWIR bands:

NBR = (NIR - SWIR) / (NIR + SWIR)

The Differenced NBR (dNBR) is computed as the change in NBR, scaled by 1000 (for representation as integer values):

dNBR = (PreNBR - PostNBR)*1000

The Relative dNBR (RdNBR) includes an additional scale factor designed to reduce the correlation with pre-fire vegetation density. It also includes an offset calculated from the dNBR in an unburned area in the vicinity of the fire having vegetation cover similar to that of the burned area. The offset is intended to account for seasonal or interannual differences between the two images.

RdNBR = (dNBR - offset)/sqrt(abs(PreNBR/1000))

RdNBR is the index used for vegetation burn severity assessments in the RAVG program. Higher RdNBR values are correlated with more severe burns.

Three burn severity indices form the complement of RAVG products: Composite Burn Index (CBI), percent change in basal area (BA), and percent change in canopy cover (CC). Values are estimated from RdNBR via regression models, which were developed from field data and Landsat imagery, both acquired approximately one year post-fire. The field data were collected from a number of fires that burned in the Sierra Nevada and Klamath Mountains in California between 1999 and 2006. RdNBR values were derived from post-fire imagery acquired at approximately the same time, and seasonally matching imagery from before each fire.

The CBI is a composite linear combination of fire effects experienced at a site and encompasses all vegetation strata from the forest floor to the upper canopy. The composite value ranges from 0 to 3. Thematic CBI-based severity classes were "calibrated" from field data collected about one year post-fire, meaning that field data collected on a given fire or fires that occurred in similar vegetation types were used to classify burn severity as unchanged, low, moderate or high severity. CBI values of 0.1, 1.25, and 2.25 were selected as the breakpoints between the successive classes, which are defined as follows:

Unchanged: Areas indistinguishable from pre-fire conditions. This does not necessarily indicate that the area was unburned.

Low: Areas of surface fire with little change in cover and little mortality of the structurally dominant vegetation.

Moderate: Areas between low and high severity, with a mixture of effects on the structurally dominant vegetation.

High: Areas where the dominant vegetation has high to complete mortality.

Percent change in basal area was calibrated through regression analysis of the RdNBR index to basal area change as measured in the same field plots where the CBI data were collected. For this measure, a tree with no green foliage one year post-fire was defined as being dead. Percent change in canopy cover was likewise calibrated through regression analysis of the RdNBR index to measured or calculated tree canopy cover change. Pre-fire canopy cover was determined through photo interpretation of pre-fire digital orthophotos or by way of the Forest Vegetation Simulator (FVS) (https://www.fs.fed.us/fmsc/fvs/).

The following models were used for extended assessments; that is, assessments based on post-fire imagery acquired during the growing season one year after the fire:

CBI = (1/0.6124)*LN((RdNBR + 123.3)/196.8) [2016 and earlier]
CBI = (1/0.3890)*LN((RdNBR + 369.0)/421.7) [2017 and later]
BA Percent Change = 100*(SIN((RdNBR-166.5)/389))^2
CC Percent Change = 100*(SIN((RdNBR-161.0)/392.6))^2

Calibrated thresholds for initial assessments were derived through regression modeling of satellite reflectance values from imagery collected one year post-fire to imagery acquired immediately post-fire. Application of the calculated correction factor yields the following initial assessment models:

CBI = (1/0.6124)*LN((RdNBR/1.1438 + 123.3)/196.8) [2016 and earlier]
CBI = (1/0.3890)*LN((RdNBR/1.1438 + 369.0)/421.7) [2017 and later]
BA Percent Change = 100*(SIN((RdNBR/1.1438-166.5)/389))^2
CC Percent Change = 100*(SIN((RdNBR/1.1438-161.0)/392.6))^2

A thematic version of each continuous burn severity raster was created based on the following class breaks:

Four-category severity classification based on CBI:
0 = outside perimeter
1 = unchanged (0 &lt;= CBI &lt; 0.1)
2 = low severity (0.1 &lt;= CBI &lt; 1.25)
3 = moderate severity (1.25 &lt;= CBI &lt; 2.25)
4 = high severity (2.25 &lt;= CBI &lt;= 3.0)
9 = unmappable

Seven-category percent change in basal area (BA):
0 = outside perimeter
1 = 0% BA loss
2 = 0% &lt; BA loss &lt; 10%
3 = 10% &lt;= BA loss &lt; 25%
4 = 25% &lt;= BA loss &lt; 50%
5 = 50% &lt;= BA loss &lt; 75%
6 = 75% &lt;= BA loss &lt; 90%
7 = BA loss &gt;= 90%
9 = unmappable

Five-category percent change in canopy cover (CC):
0 = outside perimeter
1 = 0% CC loss
2 = 0% &lt; CC loss &lt; 25%
3 = 25% &lt;= CC loss &lt; 50%
4 = 50% &lt;= CC loss &lt; 75%
5 = CC loss &gt;= 75%
9 = unmappable

When a perimeter for a given fire was available from the incident management team or local unit, it was used as the initial approximation for the RAVG burned area perimeter. In many cases, supplied perimeters were edited to account for obvious discrepancies with the visible burned area (based on the post-fire imagery). If no perimeter was provided, the burned area boundary was delineated from the dNBR and post-fire reflectance imagery. Open water and areas obscured by clouds, shadows, active fire, smoke, or snow were masked and identified as "unmappable".

Note that derived burn severity products represent a snapshot in time and that the models are applied to the entire extent of each burned area without regard to vegetation type. Factors such as delayed mortality, resprouting, the presence of non-tree vegetation, and the occurrence of non-fire disturbances can contribute to errors in the burn severity estimates.


# other
The stand-replacing fire is a fire in which most or all overstory trees are killed.


Fire behaviour refers to the manner in which fuel ignites, flame develops and fire spreads. In wildland fires, this behaviour is influenced by how fuels (such as needles, leaves and twigs), weather and topography interact. Once a fire starts, it will continue burning only if heat, oxygen and more fuel are present. Together, these three elements are said to make up the “fire triangle.” To put out a fire requires eliminating one or more of the fire triangle’s elements. Firefighters work to do that by: (1) cooling fuels below the combustion temperature through the use of water, foam, retardant or dirt; (2) cutting off the oxygen supply through the use of water, retardant or dirt; (3) removing fuel by clearing a swath of trees and brush ahead of the advancing fire.


There are three basic types of forest fires: (1) Crown fires burn trees up their entire length to the top. These are the most intense and dangerous wildland fires. (2) Surface fires burn only surface litter and duff. These are the easiest fires to put out and cause the least damage to the forest. (3) Ground fires (sometimes called underground or subsurface fires) occur in deep accumulations of humus, peat and similar dead vegetation that become dry enough to burn. These fires move very slowly, but can become difficult to fully put out, or suppress. Occasionally, especially during prolonged drought, such fires can smoulder all winter underground and then emerge at the surface again in spring.

For more than four decades, Canadian Forest Service researchers have been developing and refining several national systems for identifying where and when the risk of wildland fire is greatest. This work has played a crucial role in protecting Canadians, their property and forest resources. Among these, the main national system is the Canadian Forest Fire Danger Rating System (CFFDRS). Tools developed to support the CFFDRS include:
- Canadian Forest Fire Weather Index System (FWI) — a system used across Canada to assess day-to-day changes in the potential for fires to ignite and spread;
- Canadian Forest Fire Behavior Prediction (FBP) System — a system used to estimate potential fire spread rate, fuel consumption and fire intensity for a range of forest fuel types in Canada;
- Canadian Fire Effects Model (CanFIRE) — an extension model of the CFFDRS used to analyze the immediate physical effects of fire on stands and the resulting ecological effects on forest vegetation.

As well, government and university researchers have developed several fire occurrence prediction models for predicting the number of lightning-caused and human-caused forest fires in a given area.


higher slopes increase the rate of spread and intensity, but usually reduce the residence time of fire. Burn severity is expected to be more severe in coniferous forests
than in broadleaved forests [[Fernandes et al. 2010](#Fernandes2010)]. The pre-fire tree species composition could play an important role in determining post-fire reflectance and recovery and, subsequently, burn severity [[Dragozi et al., 2016](#Dragozi2016)]. Even more, the season of the year when each fire takes place is expected to influence the initial fire severity, and delayed vegetation response [[Fernandes et al., 2017](#Fernandes2010)].


## Life Zone
Although not widely used except in the Southwest, Merriam's Life Zones are useful to quickly characterize the different biotas seen at different elevations. Although the desert proper falls entirely within the Lower Sonoran Life Zone, mountain islands within the desert or bounding it often support one or more higher-elevation zones. Following is a brief (overly brief) rundown.

Lower Sonoran Life Zone—Encompasses what we normally consider desert and also desert grassland. El Paso is in the Lower Sonoran Life Zone. Typical plants include Black Grama (Bouteloua eriopoda), Lechuguilla (Agave lechuguilla), Creosotebush (Larrea tridentata), Tarbush (Flourensia cernua), and Ocotillo (Fouquieria splendens). Some typical mammals include Merriam's Kangaroo Rat (Dipodomys merriami) and Mearns Grasshopper Mouse (Onychomys arenicola).

Upper Sonoran Life Zone—Encompasses cooler grasslands (such as those in northern New Mexico) and woodland. Woodlands are usually open (that is, of widely spaced trees) forests of short trees or tree-like shrubs, usually less than 30 feet tall. The most common woodland in our area is pinyon-juniper woodland. However, pinyon-juniper-oak and oak-pine woodlands also occur within the boundaries of the Chihuahuan Desert Region. Generally, woodlands occur on shallower and topographically more diverse soils than the Upper Sonoran grasslands, though overgrazing and other mistreatments of the grasslands may result in invasion by woodlands. Some typical plants include Blue Grama grass (Bouteloua gracilis) and several species of piñon (Pinus) and juniper (Juniperus), the species involved varying with the geographic area. Some common mammals include the Pronghorn (Antilocapra americana), sometimes wrongly called antelope, the Cliff Chipmunk (Tamias dorsalis), and Black-tailed Prairie Dog (Cynomys ludovicianus).


Transition Life Zone—In the northern Chihuahuan Desert, generally Ponderosa Pine forest, though other pines occur at similar elevations farther south. The zone often includes Gambel Oak, particularly where burned or logged off, and Douglas Fir is an ingredient in the higher portions.

Canadian Life Zone—Spruce-fir forest, similar in overall appearance to the trans-Canadian spruce-fir forest, or taiga. Aspen replaces Gambel Oak as the main disturbance tree. This forest essentially is a boreal (northern) forest extending far south along the higher elevations of the Rockies and, south of the Rocky Mountains, into the northern desert region at high elevations of the Basin and Range mountains, such as Sierra Blanca and the Sacramento Mountains.

Hudsonian Life Zone—This and the following life zone occurs almost entirely north of our region at high elevations. As one nears the climatic timberline (either at high elevations or in the Far North), the coniferous forest trees become stunted (and a few different taxa appear). Sierra Blanca is considered by some to have a small representation of this zone.

Arctic-Alpine Life Zone—In the Southwest, this is the area above timberline (in the arctic, the area north of timberline), inhabited by grasses, sedges, and various herbs. We do not have representatives of this zone nearby (the nearest are in northern New Mexico). We frequently, as on Sierra Blanca, see extensive meadows without trees (balds), but these are not above true timberline (such balds usually are on westerly slopes—on north and northeastern slope, trees continue to the top of the mountains, indicating that cold temperatures are not limiting tree growth, as would be the case with true arctic-alpine conditions).

For more information, please go to [Merriam’s Life Zones definition in Radford University](https://php.radford.edu/~swoodwar/biomes/?page_id=317).


在遥感影像解译中，反演就是不知道影像上的地面物体是什么，而根据光谱信息等反求地面物体。

# Reference:

<span id="Valor2017">[Valor2017] Valor, T., Olabarria, J., Pique, M., Casals, P., 2017. The effects of burning season and severity on the mortality over time of Pinus nigra spp. salzmannii (Dunal) Franco and P. sylvestris L. For. Ecol. Manag. 406, 172–183.</span>

<span id="Fernandes2010">[Fernandes2010] Fernandes, P.M., Luz, A., Loureiro, C., 2010. Changes in wildfire severity from maritime pine woodland to contiguous forest types in the mountains of northwestern Portugal. For. Ecol. Manag. 260, 883–892. https://doi.org/10.1016/j.foreco.2010.06.008. </span>

<span id="Dragozi2016">[Dragozi2016] Dragozi, E., Gitas, I.Z., Bajocco, S., Stavrakoudis, D.G., 2016. Exploring the relationship between burn severity field data and very high resolution GeoEye images: the Case of the 2011 Evros wildfire in Greece. Rem. Sens. 8. https://doi.org/10.3390/rs8070566. </span>
