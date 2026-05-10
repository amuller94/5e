This project uses data from a [Dungeons & Dragons API](https://www.dnd5eapi.co/) to create visualizations of some of the different patterns in spell distribution within the game system, specifically its 5th edition (2014). 

D&D is the most popular tabletop roleplaying game (TTRPG) on the market. This is due in part to its Open Gaming License, which gives third parties blanket permission to create their own game supplements based on the D&D's fundamental mechanics. These fundamental mechanics are detailed in something called the System Reference[System Reference Document](https://www.dndbeyond.com/srd), or SRD. 

This project looks specifically at the spells portion of that content. There are 319 spells in the SRD, each with its own set of rules, including which of the eight included spellcasting class(es) (i.e. wizard, cleric, druid, etc.) can cast that spell; what school of magic (i.e. transmutation, illusion, necromancy, etc.) the spell belongs to; and how powerful the spell is, i.e. its numbered level (0-9). It uses visualizations to explore several questions:

> **1. Do some classes have access to more high-level spells than others?**
>
> **2. Are some schools of magic concentrated among specific classes?**
>
> **3. Is there a relationship between spell level and school of magic?**
>
<br>

## What spells exist?

Before delving into the specifics of spell distribution across classes and schools of magic, it makes sense to look at how many spells exist at each level and within each school of magic.

First, a CSV file containing spell name, spell level, spell school, and class is available for download [here](/assets/class_spell_lists.csv). This only accounts for each class's basic spell lists and does not address bards' access to Magical Secrets, nor any subclass-specific access to spells.

![alt text](spell_level_graph.png)
![alt text](spell_school_graph.png)

## 1. Do some classes have access to more high-level spells than others?

These graphs show the number of spells of each level available to full casters. Level 0 signifies cantrips. 

![alt text](bard_graph-1.png)
![alt text](cleric_graph.png)
![alt text](druid_graph.png) 
![alt text](sorcerer_graph.png) 
![alt text](warlock_graph.png) 
![alt text](wizard_graph.png) 

And of course, our half-casters:
![alt text](paladin_graph.png)
![alt text](ranger_graph.png)  

Below is a comparison between all eight spellcasting classes. 
![alt text](class_spell_graph.png)

## 2. Are some schools of magic concentrated among specific classes?

These graphs show the number of spells from each school of magic available to each spellcasting class. 
![alt text](abjuration_graph.png)
![alt text](conjuration_graph.png) 
![alt text](divination_graph.png) 
![alt text](enchantment_graph.png)
![alt text](evocation_graph.png)
![alt text](illusion_graph.png)  
![alt text](necromancy_graph.png)
![alt text](transmutation_graph.png)

Below is a comparison between the different spell schools grouped by class.
![alt text](combined_graph.png)   

## 3. Is there a relationship between spell level and school of magic?



---



#### Header 4
##### Header 5
###### Header 6
### There's a horizontal rule below this.

* * *

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
