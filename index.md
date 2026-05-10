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

<img src="assets/images/spell_level_graph.png" width="600">
<br>
<img src="assets/images/spell_school_graph-2.png" width="600">



### 1. Do some classes have access to more high-level spells than others?

These graphs show the number of spells of each level available to full casters. Level 0 signifies cantrips. 
<br>
<img src="assets/images/bard_graph-2.png" width="600">
<br>
<img src="assets/images/cleric_graph-1.png" width="600">
<br>
<img src="assets/images/druid_graph-1.png" width="600">
<br>
<img src="assets/images/sorcerer_graph-1.png" width="600">
<br>
<img src="assets/images/warlock_graph-1.png" width="600">
<br>
<img src="assets/images/wizard_graph.png" width="600">

And of course, our half-casters:
<br>
<img src="assets/images/paladin_graph-1.png" width="600">
<br>
<img src="assets/images/ranger_graph-1.png" width="600">

Below is a comparison between all eight spellcasting classes. 
![alt text](assets/images/class_spell_graph-1.png) Click [here](assets/images/class_spell_graph-1.png) for a larger view. 


I've also generated a set of graphs showing the schools of spells accessible to only one class, accessible to two classes, etc., going all the way up to seven classes (no spells were accessible to all eight casting classes).
<img src="assets/images/oneschool_graph-1.png" width="600">
<br>
<img src="assets/images/twoschools_graph-1.png" width="600">
<br>
<img src="assets/images/threeschools_graph-1.png" width="600">
<br>
<img src="assets/images/fourschools_graph-1.png" width="600">
<br>
<img src="assets/images/fiveschools_graph-1.png" width="600">
<br>
<img src="assets/images/sixschools_graph-2.png" width="600">
<br>
<img src="assets/images/sevenschools_graph-2.png" width="600">
<br>
<br>
This graph sets the data from the above graphs side-by-side, allowing for an overall view of the data. Click [here](assets/images/allschools_graph-2.png) for a larger view. 

<img src="assets/images/allschools_graph-2.png" width="800">


### 2. Are some schools of magic concentrated among specific classes?

These graphs show the number of spells from each school of magic available to each spellcasting class. 

<img src="assets/images/abjuration_graph-2.png" width="600">
<br>
<img src="assets/images/conjuration_graph-1.png" width="600">
<br>
<img src="assets/images/divination_graph-1.png" width="600">
<br>
<img src="assets/images/enchantment_graph-1.png" width="600">
<br>
<img src="assets/images/evocation_graph-1.png" width="600">
<br>
<img src="assets/images/illusion_graph-1.png" width="600">
<br>
<img src="assets/images/necromancy_graph-1.png" width="600">
<br>
<img src="assets/images/transmutation_graph-1.png" width="600">
<br>
<br>
Below is a comparison between the different spell schools grouped by class. Click [here](assets/images/combined_graph-1.png) for a larger view. 

<img src="assets/images/combined_graph-1.png" width="800">
<br>

### 3. Is there a relationship between spell level and school of magic?

These graphs show the distribution of spell schools at each spell level.

<img src="assets/images/cantrips_schools-1.png" width="600">
<br>
<img src="assets/images/lvl1_schools-1.png" width="600">
<br>
<img src="assets/images/lvl2_schools-1.png" width="600">
<br>
<img src="assets/images/lvl3_schools-1.png" width="600">
<br>
<img src="assets/images/lvl4_schools-1.png" width="600">
<br>
<img src="assets/images/lvl5_schools-1.png" width="600">
<br>
<img src="assets/images/lvl6_schools-1.png" width="600">
<br>
<img src="assets/images/lvl7_schools-1.png" width="600">
<br>
<img src="assets/images/lvl8_schools-1.png" width="600">
<br>
<img src="assets/images/lvl9_schools-1.png" width="600">
<br>
<br>
Below is a version that shows the distribution of the spells in each class. Click [here](assets/images/all_lvls_graph.png) for a larger view. 

<img src="assets/images/all_lvls_graph.png" width="800">


