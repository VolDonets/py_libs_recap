# National Hydro Network, Canada, Level 1

# Data Model

# Edition 1.0

# 2004-08

Gouvernement du Canada

Ressources naturelles Canada

Centre canadien de la cartographie et d’observation de la Terre

# Service à la clientèle de GéoGratis

Téléphone : +01-819-564-4857

1-800-661-2638 (Canada et États-Unis)

Télécopieur : +01-819-564-5698

Courriel : geoginfo@RNCan.gc.ca

URL : www.GeoGratis.gc.ca

Canada
# Copyright Notice

© Her Majesty the Queen in Right of Canada, Department of Natural Resources.

All rights reserved.

GeoBase®
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# REVISION HISTORY

|Date|Version|Description|
|---|---|---|
|September 2002|Draft 01|First draft for discussion with Nova Scotia|
|January 2003|Draft|Second draft after discussion with Nova Scotia and major review of the hydro network model through: • Proposal of options|
|March 2003|Alpha|Draft version after discussion and decisions made concerning NHNC1 scope and content with Nova Scotia and British Columbia|
|July 2003|Draft 02|Draft version after discussion and decisions made concerning the detailed NHNC1 model and content with Nova Scotia, British Columbia, and the Yukon. Meeting in Victoria, May 2003.|
|December 2003|Draft|Integration of UML model for both LRS and Segmented views of the NHNC1.|
|February 2004|Draft|English review; Remove the UML model for the Segmented view.|
|May 2004|Draft|Update from the March Workshop comments.|
|August 2004|2004.1|The object metadata attribute « date » is renamed « validity_date » in section 3.1.6.2 and at all other parts referring to object metadata. A new Feature type value is added for inland water (see section 3.1.5)|

# FUTURE WORK

|Key word|Description|
|---|---|
|GeoBase®| |
# National Hydro Network, Data Model – Edition 1.0

2004-06

# TABLE OF CONTENTS

1. OVERVIEW ............................................................................................................................................ 6
2. LRS ........................................................................................................................................................ 6
1. LRS MODEL ...................................................................................................................................... 7
3. MODEL .................................................................................................................................................. 8
1. LRS MODEL ...................................................................................................................................... 9
1. Logical view ............................................................................................................................... 9
2. Hydro network .......................................................................................................................... 10
3. Hydro events ............................................................................................................................ 11
4. Hydrographic ........................................................................................................................... 14
5. Toponymy (external package) ................................................................................................. 18
6. Metadata .................................................................................................................................. 19

GeoBase®
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# ABBREVIATIONS

|Abbreviation|Meaning|
|---|---|
|LRM|Linear Reference Method|
|LRS|Linear Reference System|
|NHNC1|National Hydro Network, Canada, Level 1|
|NID|National Identifier|
|NRCan|Natural Resources Canada|

# TERMS AND DEFINITIONS

GeoBase®
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 1 Overview

The data model can (and must) extend beyond the smallest common denominator obtained with the partners. The model must therefore contain two levels of information: mandatory data (black boxes) and optional data (grey boxes). Data homogeneity will thereby be ensured by a minimum set of data. Beyond the minimum level, the model serves as a target for all partners. Over the years, we will therefore work towards raising the minimum and redefining new targets. Minimum content will be defined for attributive and geometric data (see Figure 1 – Specifications expansion).

|Quantity of phenomenon|Number of characteristics|
|---|---|
|Mandatory|Optional|
| |Optional|

# 2 LRS

The Linear Reference System (LRS) is considered the most viable approach for managing and distributing geospatial information when several distinct organizations are involved (distributed approach).

This method makes it possible to divide a standard spatial object into two parts: the geometric and attribute parts. The geometric part (Network Linear Component in the NHNC1) describes the position of the feature without describing its nature. The attribute part (or event) describes specific information observed along its linear geometric representation. Event information does not alter the geometric representation in any way. The event's position is given relatively from the beginning of the linear geometric representation. A Point Event is determined by a specific location, while a Linear Event is defined by a starting and ending measurement. Several Linear Methods (LRMs) can be used. (They are not discussed in this document). By using this approach we can share a common geometry while each application can add their set of attributes (events) in relationship with the Water Network geometry.

GeoBase®
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 2.1 LRS model

Four packages constitute the NHNC1: Hydro Network, Hydrographic, Hydro Events and Metadata. The Hydro Network package contains the set of classes that form the linear network. The Hydrographic package contains the set of classes that form the graphical representation of features related to the linear network. The Hydro Event package contains attributive information that are referenced to Hydro Network geometry. The Metadata package contains information that describes the data themselves (date, accuracy, and so on). The portion of toponymy associated to Hydro feature data is part of the National Toponymy Model. This model associates geometries with official names and the classes used from the Toponymy Model are described in an external package called Toponymy for better understanding (issues involving text placement on paper or computer screen are excluded from consideration at this point).

|Hydro Network|Hydro Events|
|---|---|
|Toponymy (external model)|Metadata|
| |Hydrography|

# Figure 2 – Packages in the NHNC1 LRS model

GeoBase®

7
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 3 Model

The model presented below include descriptions of five packages, including the description of relationships between classes belonging to different packages and the toponymy external package.

GeoBase®

8
# National Hydro Network, Data Model – Edition 1.0  2004-06

# 3.1 LRS model

# 3.1.1 Logical view

| |Global LRS Model| |
|---|---|---|
|Network|Littoral|Deliciem|
|Hydro Events|Shoreline|Ponevents|
|BounjarEnjyy|Luel ene| |
|Nanajfeute|ToponymCollection|HydroTraversal|
|NamejLireFeaue|Poiyon MD| |
|NamejFolygonFeatune|Ccelist| |
|GeoBase®| | |

# Logical View

|ndonphk| |
|---|---|
|Coaslire|Kyoographicotsa elireEntty|
|HydpgraphicobsacefolygorEntity| |
| |HydpgraphicObsacePointEntity|
|ManMatehyorogracn -ineEnttydehydrograch|PointEntity|
|Manva|Kopgraphkentty|
|NanNajehyargephicEntity| |
|HopgrphrOnsa #Entity| |
|Iaanj| |
|WaterioY| |
# National Hydro Network, Data Model – Edition 1.0

2004-06

# 3.1.2 Hydro network

|Name:|Hydro Network|
|---|---|
|Author:|NRN/NHN Team|
|Version:|1.0|
|Created:|2003-03-07 08:42:38|
|Updated:|2004-06-02 17:00:40|

# Network Abstract Model:

NetworkComponent

- + nid: DT_UUID

# LR_Element

starts

- 0..*

1 Network Abstract Model:

# NetworkPointElement

ends

- 1

# NetworkLinearElement

- + geometry: GB_Point
- 0..*
- 1
- + geometry: GB_Curve [0..1]

# HydroJunction

- «spatialDescriptiveEvol»
- «spatialDescriptiveEvol»
- - JunctionType: CL_JunctionType
- - Isolated: boolean
- - LevelPriority: CL_LevelPriority
- - NetworkFlowType: CL_Network Flow Type
- - FlowDirection: CL_DirectionFlag

# Delimiter

- - DelimiterType: CL_DelimiterType
- - Waterbody1NID: DT_UUID
- - Waterbody2NID: DT_UUID
- - IslandNID: DT_UUID

# Shoreline

- - ShorelineWaterLevel: CL_Shoreline Water Level

# Code List

# CodeList::CL_Water

# CodeList::CL_JunctionType

|None = 0:|Network Linear Flow = 1:|
|---|---|
|Network Linear Flow and Shoreline Element = 2:|Water Boundary Element = 3:|
|Start and End of Network Linear Flow = 4:|NavProvTer = 5:|
|Network Linear Flow and Delimiter = 6:|Start of Network connected to Bank = 7:|
| |Tidal River = 7:|
| |Liquid Waste = 8:|
| |Pond = 9:|

# CodeList::CL_DelimiterType

|Unknown = -1:|None = 0:|
|---|---|
|Contiguous Water Region = 1:|Tidal = 2:|
|Coastline = 3:|Water Region Limit at ProvTerr Limit = 4:|
|Working Unit Region Limit = 5:| |

# CodeList::CL_Permanency

|Unknown = -1:|None = 0:|
|---|---|
|Permanent = 1:|Intermittent = 2:|
|Inferred = 2:|Constructed = 3:|

# CodeList::CL_DirectionFlag

|Unknown = -1:|None = 0:|
|---|---|
|same direction = 1:|opposite direction = 2:|

# CodeList::CL_LevelPriority

Primary = 1:
Secondary = 2:

GeoBase®
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 3.1.3 Hydro events

# cd Hydro Events

|Name|Hydro Events|
|---|---|
|Author|NRN/NHN Team|
|Version|1.0|
|Created|2003-03-07 08:42:58|
|Updated|2004-06-02 17:00:52|

# LR_Element

|«type»|NetworkComponent|
|---|---|
|LRS Abstract Model::Event|references|
|0..*|0..1|
|+ nid: DT_UUID|NetworkLinearElement|
|+ geometry: GB_Curve [0..1]| |

# «type»

|LRS Abstract Model::LinearEvent|LRS Abstract Model::PointEvent|
|---|---|
|+ startPosition: LR_PositionExpression|+ atPosition: LR_PositionExpression|
|+ endPosition: LR_PositionExpression| |

# descriptiveEvolution

Line Events::HydroLineEvent
PointEvents::HydroPointEvent
GeoBase®

11
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 3.1.3.1 Point Events

# cd PointEvents

|Name:|PointEvents|
|---|---|
|Author:|NRN/NHN Team|
|Version:|1.0|
|Created:|2004-03-30 09:48:28|
|Updated:|2004-06-02 17:01:04|

# LR_Element

# NetworkComponent

|«type»|«type»|
|---|---|
|LRS Abstract|Network Abstract Model::NetworkLinearElement|
|Model::Event|references|
|+ geometry:|GB_Curve [0..1]|
|+ nid:|DT_UUID 0..*|
|0..1| |

# «type»

# LRS Abstract Model::PointEvent

+ atPosition:
LR_PositionExpression
# «descriptiveEvolution»

# HydroPointEvent

# «descriptiveEvolution»

# ManMadePointEvent

# ExternalGeometryEvent

|- HydrographicEntityClassName:|char|
|---|---|
|- ExternalAgency:|char|
|- ExternalID:|DT_UUID|
|- ManMadeHydrographicEntityNID:|UUID|
|- ManMadeStatus:|CL_Manmade Status|
|- ManMadeType:|CL_Manmade Type|

# Code List

# «CodeList»

# CodeList::CL_Manmade Type

+ Unknown = -1:+ None = 0:+ Dam = 1:+ Dock = 2:+ Wharf = 3:+ Breakwater = 4:+ Dike/Levee = 5:+ Lock Gate = 6:+ Boat Ramp = 7:+ Fish Ladder = 8:+ Slip = 9:
# «CodeList»

# CodeList::CL_Obstacle Type

+ Unknown = -1:+ Falls = 1:+ Rapids = 2:+ Reef = 3:+ Rocks = 4:+ Disappearing stream = 5:+ Exposed shipwreck = 6:+ Ford = 7:+ Other = 8:
# «CodeList»

# CodeList::CL_Manmade Status

|«descriptiveEvolution»|«descriptiveEvolution»| | |
|---|---|---|---|
|+ Unknown = -1:| | | |
|+ None = 0:| | | |
|+ Operational = 1:| | | |
|+ Abandoned = 2:| | | |

# ExternalPointEvent

# ObstaclePointEvent

|- ExternalAgency:|char|
|---|---|
|- ExternalID:|DT_UUID|
|- EventName:|char|
|- HydrographicEntityClassName:|char|
|- HydrographicObstacleEntityNID:|UUID|
|- ObstacleType:|CL_Obstacle Type|

# GeoBase®

# 12
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 3.1.3.2 Line Events

# cd LineEvents

|Name:|LineEvents|Line Events|
|---|---|---|
|Package:|LineEvents| |
|Version:|1.0| |
|Author:|NRN/NHN Team| |

# LR_Element

|«type»|references|NetworkComponent|
|---|---|---|
|LRS Abstract Model::Event|0..*|0..1|
|«type»|Network Abstract Model::|NetworkLinearElement|
|+ nid:|DT_UUID| |
|+ geometry:|GB_Curve [0..1]| |

# «type»

|LRS Abstract Model::LinearEvent| | |
|---|---|---|
|+ startPosition:|LR_PositionExpression| |
|+ endPosition:|LR_PositionExpression| |

# «descriptiveEvolution»

|HydroLineEvent| | |
|---|---|---|
|«descriptiveEvolution»|ObstacleLineEvent|ExternalLineEvent|
|- HydrographicEntityClassName:|char| |
|- HydrographicObstacleEntityNID:|UUID| |
|- ObstacleType:|CL_ObstacleType| |
|- ExternalAgency:|char| |
|- ExternalID:|DT_UUID| |
|- EventName:|char| |

# «descriptiveEvolution»

|Flow PropertyEvent| | |
|---|---|---|
|ManMadeLineEvent| | |
|- WaterDefinition:|CL_WaterDefinition| |
|- HydrographicEntityClassName:|char| |
|- ManMadeHydrographicEntityNID:|UUID| |
|- ManMadeStatus:|CL_ManmadeStatus| |
|- ManMadeType:|CL_ManmadeType| |

# Code List

|«CodeList»|CodeList::CL_ObstacleType| |
|---|---|---|
|CodeList::CL_WaterDefinition| | |
|+ Unknown = -1:|+ None = 0:| |
|+ Canal = 1:|+ Falls = 1:| |
|+ Conduit = 2:|+ Rapids = 2:| |
|+ Ditch = 3:|+ Reef = 3:| |
|+ Rocks = 4:|+ Disappearing stream = 5:| |
|+ Lake = 4:|+ Exposed shipwreck = 6:| |
|+ Reservoir = 5:|+ Ford = 7:| |
|+ Watercourse = 6:|+ Other = 8:| |
|+ Tidal River = 7:|+ Liquid Waste = 8:| |
|+ Pond = 9:| | |

# «CodeList»

|CodeList::CL_ManmadeType| | |
|---|---|---|
|+ Unknown = -1:|+ None = 0:| |
|+ Dam = 1:|+ Dock = 2:| |
|+ Wharf = 3:|+ Breakwater = 4:| |
|+ Dike/Levee = 5:|+ Lock Gate = 6:| |
|+ Boat Ramp = 7:|+ Fish Ladder = 8:| |
|+ Slip = 9:| | |

# GeoBase®

# 13
# National Hydro Network, Data Model – Edition 1.0

2004-06

# 3.1.4 Hydrographic

There are implied associations with all hydrographic features and the Hydro Network could be defined explicitly through spatial analysis.

|Name:|Hydrographic|
|---|---|
|Author:|NRN/NHN Team|
|Version:|1.0|
|Created:|2003-03-07 08:43:42|
|Updated:|2004-06-02 17:01:27|

# HydrographicEntity

+is described by

- NID: DT_UUID 1..2

# ManMadeHydrographicEntity

- ManMadeType: CL_Manmade Type
- ManMadeStatus: CL_Manmade Status

# Coastline

- ShorelineWaterLevel: CL_Shoreline Water Level

# Shoreline

# HydrographicObstacleEntity

- ObstacleType: CL_Obstacle Type
- WaterDefinition: CL_Water Definition
- Permanency: CL_Permanency
- Isolated: boolean
- geometry: GB_Curve

# Island

- CoastalIsland: boolean
- SandIsland: CL_SandIsland
- geometry: GB_Surface

+ Island() : GM_Ring

Island polygons are formed according to WaterBoundaryFeatures from the Network package.

# WaterBody

- Isolated: boolean
- Permanency: CL_Permanency
- WaterDefinition: CL_Water Definition
- geometry: GB_Surface

+ nid: DT_UUID

+ validity_date: DT_Date

+ acquisitionTechnique: CL_AcquisitionTechnique [0..1]

+ datasetName: Char(50)

+ planimetricAccuracy: Int

+ provider: CL_Provider

+ completelyCover: Boolean

# CreationMetadata

# RevisionMetadata

WaterRegion polygons are formed according to WaterBoundaryFeatures from the Network package.

# Code List

|CL_Manmade Type|CL_Obstacle Type|CL_Permanency|CL_Water Definition|CL_SandIsland|
|---|---|---|---|---|
|+ Unknown = -1:|+ Unknown = -1:|+ None = 0:|+ Canal = 1:|- Unknown = -1:|
|+ None = 0:|+ Falls = 1:|+ Permanent = 1:|+ Conduit = 2:|- None = 0:|
|+ Dam = 1:|+ Rapids = 2:|+ Intermittent = 2:|+ Ditch = 3:|- No = 1:|
|+ Dock = 2:|+ Reef = 3:|+ Unknown = -1:|+ Lake = 4:|- Yes = 2:|
|+ Wharf = 3:|+ Rocks = 4:|+ None = 0:|+ Reservoir = 5:| |
|+ Breakwater = 4:|+ Disappearing stream = 5:| | | |
|+ Dike/Levee = 5:|+ Unknown = -1:| | | |
|+ Lock Gate = 6:|+ None = 0:| | | |
|+ Boat Ramp = 7:|+ Operational = 1:| | | |
|+ Fish Ladder = 8:|+ Abandoned = 2:| | | |
|+ Slip = 9:| | | | |

GeoBase®

14
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 3.1.4.1 Hydrographic Water Areas

# cd Hydrographic Water Areas

|Name:|Hydrographic Water Areas|
|---|---|
|Author:|NRN/NHN Team|
|Version:|1.0|
|Created:|2004-04-21 12:57:35|
|Updated:|2004-05-05 13:29:57|
|NID:|DT_UUID|

# «spatialDescriptiveEvol»

# WaterBody

- Isolated: boolean
- Permanency: CL_Permanency
- WaterDefinition: CL_Water Definition
- geometry: GB_Surface
- + WaterBody() : GM_SurfaceBoundary

# «spatialDescriptiveEvol»

# Island

- CoastalIsland: boolean
- SandIsland: CL_SandIsland
- «inner bound»
- geometry: GB_Surface
- + Island() : GM_Ring

# «outer bound»

# Code List

|LR_Element|NetworkComponent|
|---|---|
|«type»|Hydro Network:: WaterBoundaryEntity|
|CodeList:: CL_Permanency|CodeList:: CL_Water Definition|

# Network Abstract Model:: NetworkLinearElement

- + geometry: GB_Curve [0..1]

# Code List

|+ Unknown = -1:|+ None = 0:|
|---|---|
|+ None = 0:|+ Canal = 1:|
|+ Permanent = 1:|+ Conduit = 2:|
|+ Intermittent = 2:|+ Ditch = 3:|
|+ Lake = 4:|+ Reservoir = 5:|
|+ Watercourse = 6:|+ Tidal River = 7:|
|+ Liquid Waste = 8:|+ Pond = 9:|

# GeoBase®

15
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 3.1.4.2 Hydrographic Obstacle

|Name:|HydrographicObstacleEntity|Hydrographic Obstacle Entity|
|---|---|---|
|Author:|NRN/NHN Team| |
|Version:|1.0| |
|Created:|2004-04-06 10:49:50| |
|Updated:|2004-06-02 17:01:44| |

# «spatialDescriptiveEvol» HydrographicEntity

- - NID: DT_UUID

# «spatialDescriptiveEvol» HydrographicObstacleEntity

- - ObstacleType: CL_Obstacle Type Code List

# «CodeList» CodeList::CL_Obstacle Type

# «spatialDescriptiveEvol» HydrographicObstaclePointEntity

- + geometry: GB_Point

# «spatialDescriptiveEvol» «spatialDescriptiveEvol» HydrographicObstacleLineEntity

- + geometry: GB_Curve

# HydrographicObstaclePolygonEntity

- + geometry: GB_Surface

# Obstacle Types

- + Unknown = -1:
- + Falls = 1:
- + Rapids = 2:
- + Reef = 3:
- + Rocks = 4:
- + Disappearing stream = 5:
- + Exposed shipwreck = 6:
- + Ford = 7:
- + Other = 8:

# GeoBase®

16
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 3.1.4.3 Manmade Hydrographic

cd ManmadeHydrographicEntity

Name:         ManmadeHydrographicEntity                     ManmadeHydrographic
Author:       NRN/NHN Team
Version:      1.0
Created:      2004-04-06 10:38:27
Updated:      2004-06-02 17:01:53               «spatialDescriptiveEvol»
HydrographicEntity
-   NID: DT_UUID                                         Code List«CodeList»
CodeList::
CL_Manmade Type

+   Unknown = -1:
+   None = 0:
+   Dam = 1:
«spatialDescriptiveEvol»                                +   Dock = 2:
ManMadeHydrographicEntity                                  +   Wharf = 3:
+   Breakwater = 4:
-   ManMadeType: CL_Manmade Type                                  +   Dike/Levee = 5:
-   ManMadeStatus: CL_Manmade Status                              +   Lock Gate = 6:
+   Boat Ramp = 7:
+   Fish Ladder =8:
+   Slip = 9:

«spatialDescriptiveEvol»                                   «spatialDescriptiveEvol»
ManMadeHydrographicPointEntity                          ManMadeHydrographicPolygonEntity
+   geometry: GB_Point                                                                                  «CodeList»
+  geometry: GB_Surface                    CodeList::
CL_Manmade Status

+   Unknown = -1:
«spatialDescriptiveEvol»                              +   None = 0:
ManMadeHydrographicLineEntity                               +   Operational = 1:
+   Abandoned = 2:
-   geometry: GB_Curve

GeoBase®                                                                                                                                  17
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 3.1.5 Toponymy (external package)

# cd Toponymy Model

|Name:|Toponymy Model|
|---|---|
|Author:|Michelle Poirier|
|Version:|1.0|
|Created:|2004-04-13 14:49:26|
|Updated:|2004-08-30 12:04:08|

# ToponymyCollection

|- NID:|DT_UUID|
|---|---|
|- Feature_ID:|DT_UUID|
|- DB Name:|Int|
|- AssociationDate:|DT_Date|
|- NominalScale:|Int|
|- MinScale:|Int|
|- MaxScale:|Int|

# Relationships

|+is defined by|1..*|+is defined by|1..*|+is defined by|1..*|
|---|---|---|---|---|---|
|+defines|1..*| | | | |

# Hydrographic::HydrographicEntity

|- NID:|DT_UUID|
|---|---|
|- FeatureType:|CL_Feature Type|
|- RelatedNID:|DT_UUID|

# Traversal

+defines
1..*
# HydroTraversal

+is described by
1..2
# NamedPointFeature

+ geometry:
GB_Point
# NamedLineFeature

+ geometry:
GB_Curve
# NamedPolygonFeature

- geometry:
GB_Surface
# Object MD::ObjectMetadata

|- NID:|UUID|
|---|---|
|- geometry:|GB_CompositeCurve|

# NetworkComponent

|+ geometry:|GB_Curve [0..1]|
|---|---|
|+ describes| |
|+ nid:|DT_UUID|
|+ validity_date:|DT_Date|
|+ acquisitionTechnique:|CL_AcquisitionTechnique [0..1]|
|+ datasetName:|Char(50)|
|+ planimetricAccuracy:|Int|
|+ provider:|CL_Provider|
|+ completelyCover:|Boolean|

# Hydro Network::NetworkLinearFlow

|- Isolated:|boolean|
|---|---|
|- LevelPriority:|CL_LevelPriority|
|- NetworkFlowType:|CL_Network Flow Type|
|- FlowDirection:|CL_DirectionFlag|

# Code List

|«CodeList»|CodeList::CL_Feature Type|
|---|---|
|+ MarineWaterbody|= 1: Int|
|+ FaultLine|= 2: Int|
|+ Landscape|= 3: Int|
|+ MassIce|= 4: Int|
|+ Mountains|= 5: Int|
|+ ProjectionOfLand|= 6: Int|
|+ UnderseaFeature|= 7: Int|
|- InlandWater|= 8: Int|

# GeoBase®

18
# National Hydro Network, Data Model – Edition 1.0

# 2004-06

# 3.1.6 Metadata

# 3.1.6.1 Polygon Metadata

cd Polygon MD

# Polygon Metadata

|Field|Type|
|---|---|
|nid|UUID|
|geometry|GB_Surface|
|validityDateOfGeometry|DateInterval|
|resultantPlanimetricAccuracy|AccuracyInterval|
|resultantAltimetricAccuracy|AccuracyInterval [0..1]|
|provinceName|ProvinceName|
|StandardVersion|Char(6)|
|comments|Char (256) [0..1]|

# Concerned Features

|Field|Type|
|---|---|
|FeatureName|Char(256)|

# 3.1.6.2 Object Metadata

cd NHN LRS Profile Global Model

# Object Metadata

|Field|Type|
|---|---|
|nid|DT_UUID|
|validity_date|DT_Date|
|acquisitionTechnique|CL_AcquisitionTechnique [0..1]|
|datasetName|Char(50)|
|planimetricAccuracy|Int|
|provider|CL_Provider|
|completelyCover|Boolean|

GeoBase® 19
