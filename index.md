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

### How does the project work?

It uses the [5e API](https://www.dnd5eapi.co/) to pull the following data for each of the 319 spells: spell name, spell level, spell school, class, and subclass. It assigns the correct class to each subclass and the subclass "all" to each class. With the help of the pandas library, these data are then assembled into a dataframe.

```
df = pd.DataFrame({
    'Spell Name' : spellname,
    'Spell Level': spelllevel,
    'Spell School' : spellschool,
    'Class' : spellclass,
    'Subclass' : spellsubclass
})
```

In the SRD, each class has only one subclass. This was always going to make subclass data only moderately useful, but mid-project, it was discovered that subclass data in this API was unreliable: every single spell was designated "lore," the SRD bard subclass. This is due to the combination of a bard feature called "Magical Secrets," which gives bards limited access to every spell in the game, plus an error, which is attributing this only to the lore subclass rather than the bard class as a whole. This does preserve the integrity of the bard data—-spells tagged "bard" are all on the core bard spell list--but makes the subclass data less useful for this project's purposes. 

As such, the code filters the data to include only the data for the classes' spell lists:

```
classSpellLists = df[df['Subclass'] == 'all']

```

This forms the basis for the rest of the data manipulation, which is explained below.  


### What spells exist?

Before delving into the specifics of spell distribution across classes and schools of magic, it makes sense to look at how many spells exist at each level and within each school of magic.

First, a CSV file containing spell name, spell level, spell school, and class is available for download [here](/assets/class_spell_lists.csv). This only accounts for each class's basic spell lists and does not address bards' access to Magical Secrets, nor any subclass-specific access to spells.

<img src="assets/images/spell_level_graph.png" width="600">
<br>
<img src="assets/images/spell_school_graph-2.png" width="600">


To create these graphs, the code pulls the spell level data, counts the number of instances of each level, and sorts this information into a dataframe useable for creating a bar graph.

```
spellcounts = classSpellLists['Spell Level'].value_counts()
sortedspellcounts = spellcounts.sort_index()
```

Through a similar process, it pulls and sorts the number of spells that exist in each spell school.

```
spellcountsschool = classSpellLists['Spell School'].value_counts()
sortedspellcountsschool = spellcountsschool.sort_index()
```



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


To create these graphs, the code pulls only the rows containing bard spells, gathers the rest of the data for those rows, counts how many rows there are for each spell level, and sorts those data, yielding a dataframe that can be used to create a graph of how many spells of each level are on the bard spell list.

```
bard = classSpellLists['Class'] == 'bard'
bardSpells = classSpellLists[bard].value_counts('Spell Level').sort_index()
```

It does the same for the other classes, adding in null rows where no data exists:

```
paladinSpells = classSpellLists[paladin].value_counts('Spell Level').sort_index()
paladinSpells[int(0)] = 0
paladinSpells[int(6)] = 0
paladinSpells[int(7)] = 0
paladinSpells[int(8)] = 0
paladinSpells[int(9)] = 0
paladinSpells = paladinSpells.sort_index()
```

To create a dataframe that re-combines all of these data into the basis for a multiple bar graph setting the eight graphs alongside each other, the function ```pd.merge``` is used.


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

The original dataframe contains one row for each spell for each class, so to determine how many spells of each school are available to how many classes, the code counts how many times each spell name occurs: 

```
numberOfClasses = classSpellLists.value_counts('Spell Name')
```

...yielding the following data:

```
> Spell Name
> Detect Magic         7
> Dispel Magic         7
> Hold Person          6
> Locate Creature      6
> Locate Object        6
>                     ..
> Meld Into Stone      1
> Maze                 1
> Mass Healing Word    1
> Mass Heal            1
> Acid Arrow           1
> Name: count, Length: 319, dtype: int6
```

...which is then itself counted (for the number of spells available to exactly seven classes, etc.) and sorted. 

```
classesPerSpell = numberOfClasses.value_counts().sort_index()
```

The code then re-merges the numberOfClasses list with the spell name data and drops superfluous information to leave a dataframe containing spell name, the classes count for each spell, and the school of magic for each spell.

```
combined_df = pd.merge(numberOfClasses, classSpellLists, on='Spell Name')
combined_df = combined_df.drop_duplicates(subset=['Spell Name'])
combined_df = combined_df.drop(columns = ['Class', 'Subclass', 'Spell Level'])
```

It then pulls only the spells available to exactly one class and counts how many there are of each spell school, yielding a dataframe that can be used to create a graph of how many of the spells available to exactly one class belong to each school of magic. 

```
oneclass = combined_df['count'] == 1
oneSchool = combined_df[oneclass].value_counts('Spell School').sort_index()
```
It does the same for the rest of the data, again adding in null rows where no data exists:

```
fiveSchools = combined_df[fiveclasses].value_counts('Spell School').sort_index()
fiveSchools['illusion'] = 0
fiveSchools['necromancy'] = 0
fiveSchools = fiveSchools.sort_index()
```

Here, too, to create a dataframe that re-combines all of these data into the basis for a multiple bar graph setting the eight graphs alongside each other, the function ```pd.merge``` is used.


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


To create these graphs, the code pulls only the rows containing abjuration spells, gathers the rest of the data for those rows, counts how many rows there are for each class, and sorts those data, yielding a dataframe that can be used to create a graph of how many spells of each school each class has:

```
abjuration = classSpellLists['Spell School'] == 'abjuration'
abjurationClassSchool = classSpellLists[abjuration].value_counts('Class').sort_index()
```
Again,  to create a dataframe that re-combines all of these data into the basis for a multiple bar graph setting the eight graphs alongside each other, the function ```pd.merge``` is used.

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

To create these graphs, the code pulls only the rows containing cantrips, gathers the rest of the data for those rows, counts how many rows there are for each spell school, and sorts those data, yielding a dataframe that can be used to create a graph of how many spells of each school exist at each spell level:

```
cantrip = classSpellLists['Spell Level'] == 0
cantripSchools = classSpellLists[cantrip].value_counts('Spell School').sort_index()
```
Again,  to create a dataframe that re-combines all of these data into the basis for a multiple bar graph setting the eight graphs alongside each other, the function ```pd.merge``` is used.

Below is a version that shows the distribution of the spells in each class. Click [here](assets/images/all_lvls_graph.png) for a larger view. 

<img src="assets/images/all_lvls_graph.png" width="800">


