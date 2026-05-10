This project uses data from a [Dungeons & Dragons API](https://www.dnd5eapi.co/) to create visualizations of some of the different patterns in spell distribution within the game system, specifically its 5th edition (2014). 

D&D is the most popular tabletop roleplaying game (TTRPG) on the market. This is due in part to its Open Gaming License, which gives third parties blanket permission to create their own game supplements based on the D&D's fundamental mechanics. These fundamental mechanics are detailed in something called the System Reference[System Reference Document](https://www.dndbeyond.com/srd), or SRD. 

This project looks specifically at the spells portion of that content. There are 319 spells in the SRD, each with its own set of rules, including which of the eight included spellcasting class(es) (i.e. wizard, cleric, druid, etc.) can cast that spell; what school of magic (i.e. transmutation, illusion, necromancy, etc.) the spell belongs to; and how powerful the spell is, i.e. its numbered level (0-9). It uses visualizations to explore several questions:
<br>

> **1. Do some classes have access to more high-level spells than others?**
>
> **2. Are some schools of magic concentrated among specific classes?**
>
> **3. Is there a relationship between spell level and school of magic?**
>
<br>

### What spells exist?

Before delving into the specifics of spell distribution across classes and schools of magic, it makes sense to look at how many spells exist at each level and within each school of magic.

First, a CSV file containing spell name, spell level, spell school, and class is available for download [here](/assets/class_spell_lists.csv). This only accounts for each class's basic spell lists and does not address bards' access to Magical Secrets, nor any subclass-specific access to spells.

<img src="spell_level_graph.png" width="600">
<br>
<img src="spell_school_graph-2.png" width="600">



### 1. Do some classes have access to more high-level spells than others?

These graphs show the number of spells of each level available to full casters. Level 0 signifies cantrips. 
<br>
<img src="bard_graph-2.png" width="600">
<br>
<img src="cleric_graph-1.png" width="600">
<br>
<img src="druid_graph-1.png" width="600">
<br>
<img src="sorcerer_graph-1.png" width="600">
<br>
<img src="warlock_graph-1.png" width="600">
<br>
<img src="wizard_graph-1.png" width="600">

And of course, our half-casters:
<br>
<img src="paladin_graph-1.png" width="600">
<br>
<img src="ranger_graph-1.png" width="600">

Below is a comparison between all eight spellcasting classes. 
![alt text](class_spell_graph-1.png)

I've also generated a set of graphs showing the schools of spells accessible to only one class, accessible to two classes, etc., going all the way up to seven classes (no spells were accessible to all eight casting classes).
<img src="oneschool_graph-1.png" width="600">
<br>
<img src="twoschools_graph-1.png" width="600">
<br>
<img src="threeschools_graph-1.png" width="600">
<br>
<img src="fourschools_graph-1.png" width="600">
<br>
<img src="fiveschools_graph-1.png" width="600">
<br>
<img src="sixschools_graph-2.png" width="600">
<br>
<img src="sevenschools_graph-2.png" width="600">
<br>
<br>
This graph sets the data from the above graphs side-by-side, allowing for an overall view of the data.

<img src="allschools_graph-2.png" width="800">


### 2. Are some schools of magic concentrated among specific classes?

These graphs show the number of spells from each school of magic available to each spellcasting class. 

<img src="abjuration_graph-2.png" width="600">
<br>
<img src="conjuration_graph-1.png" width="600">
<br>
<img src="divination_graph-1.png" width="600">
<br>
<img src="enchantment_graph-1.png" width="600">
<br>
<img src="evocation_graph-1.png" width="600">
<br>
<img src="illusion_graph-1.png" width="600">
<br>
<img src="necromancy_graph-1.png" width="600">
<br>
<img src="transmutation_graph-1.png" width="600">
<br>
<br>
Below is a comparison between the different spell schools grouped by class.

<img src="combined_graph-1.png" width="800">
<br>

### 3. Is there a relationship between spell level and school of magic?

These graphs show the distribution of spell schools at each spell level.

<img src="cantrips_schools-1.png" width="600">
<br>
<img src="lvl1_schools-1.png" width="600">
<br>
<img src="lvl2_schools-1.png" width="600">
<br>
<img src="lvl3_schools-1.png" width="600">
<br>
<img src="lvl4_schools-1.png" width="600">
<br>
<img src="lvl5_schools-1.png" width="600">
<br>
<img src="lvl6_schools-1.png" width="600">
<br>
<img src="lvl7_schools-1.png" width="600">
<br>
<img src="lvl8_schools-1.png" width="600">
<br>
<img src="lvl9_schools-1.png" width="600">
<br>
<br>
Below is a version that shows the distribution of the spells in each class. Click [here](/allschools_graph-3.png) for a larger view. 

<img src="allschools_graph-3.png" width="800">



#### Header 4
##### Header 5
###### Header 6
### There's a horizontal rule below this.

* * *

