
**Project Title:** (De)coding the Spellbook: A Comparative Look at Spell Distribution in D&D 5th Edition


**Project Description:** This project draws on an API to create visualizations of some of the different patterns in spell distribution within the 5th Edition (2014) Dungeons & Dragons game system. The [API](https://www.dnd5eapi.co/) is built from the D&D [System Reference Document](https://www.dndbeyond.com/srd) (SRD), the game's most fundamental rule set, designed to be used as a no-license-needed base for third-party content. 

This project looks specifically at the spells portion of that content, which consists of 319 individual items. Each spell has its own set of rules, including which class(es) (i.e. wizard, cleric, druid, etc.) can cast that spell, what school of magic (i.e. transmutation, illusion, necromancy, etc.) the spell belongs to, and what numbered level (0-9) the spell belongs to. This project explores three major questions using visualizations of various data:

1. Do some classes have access to more high-level spells than others?
2. Are some schools of magic concentrated among specific classes?
3. Is there a relationship between spell level and school of magic?



**Rationale Statement:** The primary rationale behind the project is simply that I've always been interested in what these types of comparisons within the D&D ruleset would show, and now I have the skillset to find out. While the SRD's content is also available on a number of GUI-based websites, it would've been an enormous amount of work to pull each piece of information manually and collate it all into an Excel document. With Python and an API, that takes just a handful of lines of code, so my time and effort can be put into arranging the data into specific subsets for comparison and creating visualizations. I've been tremendously excited to see the outcomes.


**Workflow:** The code uses the *requests* library to gather data from the API and the *matplotlib* library to make some minor adjustments to graph layout to improve readability. It also uses the library *pandas* for data analysis and manipulation.

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

In the SRD, each class has only one subclass. This was always going to make subclass data only moderately useful, but mid-project, I discovered that subclass data in this API was unreliable: every single spell was designated "lore," the SRD bard subclass. This is due to the combination of a bard feature called "Magical Secrets," which gives bards limited access to every spell in the game, plus an error, which is attributing this only to the lore subclass rather than the bard class as a whole. This does preserve the integrity of the bard data—-spells tagged "bard" are all on the core bard spell list--but makes the subclass data less useful for this project's purposes. 

As such, the code filters the data to include only the data for the classes' spell lists:

```
classSpellLists = df[df['Subclass'] == 'all']

```

This forms the basis for the rest of the data manipulation.

At this point, the code also exports a csv file containing all the spell information minus subclass data:
```
classSpellLists.to_csv('class_spell_lists.csv')
```

Next, the code pulls spell data pertaining to the relationship between class and school of magic. 

First, it pulls only the rows containing abjuration spells, then only the rows containing conjuration spells, etc., repeating this for each school of magic. Then it gathers the rest of the data for those rows, counts how many rows there are for each class, and sorts those data, yielding a dataframe for each school of magic that can be used to create a graph of how many spells of each school each class has:

```
abjuration = classSpellLists['Spell School'] == 'abjuration'
abjurationClassSchool = classSpellLists[abjuration].value_counts('Class').sort_index()
```

It adds null rows where no data exists (rangers have no necromancy spells, and paladins have no illusion spells--this was determined through evaluation of errors in a first pass at this code without the null rows):

```
necromancyClassSchool['ranger'] = 0
illusionClassSchool['paladin'] = 0
```

It graphs the data using code like this, then saves the graph as a .png file:

```
abjurationGraph = abjurationClassSchool.plot(kind = "bar", title = "Number of Abjuration Spells", color = "#006aff")

x = abjurationGraph.get_figure()
fig = x.get_figure()
fig.tight_layout()
fig.savefig('abjuration_graph.png')
```

Then, to create a dataframe that re-combines all of these data into the basis for a multiple bar graph setting the eight graphs alongside each other, the function ```pd.merge``` is used:

```
combined_df = pd.merge(abjurationClassSchool, conjurationClassSchool, on='Class')
combined_df = pd.merge(combined_df, divinationClassSchool, on='Class')
combined_df.columns = ['Abjuration', 'Conjuration', 'Divination']
combined_df = pd.merge(combined_df, enchantmentClassSchool, on='Class')
combined_df.columns = ['Abjuration', 'Conjuration', 'Divination', 'Enchantment']
combined_df = pd.merge(combined_df, evocationClassSchool, on='Class')
combined_df.columns = ['Abjuration', 'Conjuration', 'Divination', 'Enchantment', 'Evocation']
combined_df = pd.merge(combined_df, illusionClassSchool, on='Class')
combined_df.columns = ['Abjuration', 'Conjuration', 'Divination', 'Enchantment', 'Evocation', 'Illusion']
combined_df = pd.merge(combined_df, necromancyClassSchool, on='Class')
combined_df.columns = ['Abjuration', 'Conjuration', 'Divination', 'Enchantment', 'Evocation', 'Illusion', 'Necromancy']
combined_df = pd.merge(combined_df, transmutationClassSchool, on='Class')
combined_df.columns = ['Abjuration', 'Conjuration', 'Divination', 'Enchantment', 'Evocation', 'Illusion', 'Necromancy', 'Transmutation']

combinedGraph = combined_df.plot(kind = "bar", figsize = (15, 5), width = 0.8, title = "For each class, which schools of magic are most common?", color = ["#006aff", "#c749d7", "#ff3d94", "#ff6e55", "#e3a32e", "#adcd4c","#69eb98","#00fff0"])
plt.ylabel('Number of Spells')
legend = plt.legend(bbox_to_anchor=(1.02, 1), loc='upper left', prop={'size': 11})
legend.set_title("School of Magic")

x = combinedGraph.get_figure()
fig = x.get_figure()
fig.tight_layout()
fig.savefig('combined_graph.png')
```

Next, the code pulls the spell level data, counts the number of instances of each level, and sorts this information into a dataframe useable for creating a bar graph.

```
spellcounts = classSpellLists['Spell Level'].value_counts()
sortedspellcounts = spellcounts.sort_index()

levelGraph = sortedspellcounts.plot(kind = "bar", title = "Number of Spells of Each Level")
```
It then saves the bar graph. Similar code is used each time a graph is saved, so that code will not be duplicated here.

Through a similar process, the code pulls and sorts the number of spells that exist in each spell school.

```
spellcountsschool = classSpellLists['Spell School'].value_counts()
sortedspellcountsschool = spellcountsschool.sort_index()

schoolGraph = sortedspellcountsschool.plot(kind = "bar", title = "Number of Spells Within Each Magic School", color = "purple")
```

Next, the code pulls data pertaining to the relationship between class and spell level. 

First, it pulls only the rows containing bard spells, then only the rows containing cleric spells, etc., repeating this for each school of magic. Then it gathers the rest of the data for those rows, counts how many rows there are for each spell level, and sorts those data, yielding a dataframe for each school of magic that can be used to create a graph of how many spells of each level are on the bard spell list. 

```
bard = classSpellLists['Class'] == 'bard'
bardSpells = classSpellLists[bard].value_counts('Spell Level').sort_index()

bardGraph = bardSpells.plot(kind = "bar", title = "Bard Spells by Level", color = "#0eff58")
plt.ylim(0, 25) 
```
(It also sets a y axis limit that avoids the y-axis labels from being broken down into 0.5s.)

It does the same for the other classes, adding in null rows where no data exists:

```
paladinSpells = classSpellLists[paladin].value_counts('Spell Level').sort_index()
paladinSpells[int(0)] = 0
paladinSpells[int(6)] = 0
paladinSpells[int(7)] = 0
paladinSpells[int(8)] = 0
paladinSpells[int(9)] = 0
paladinSpells = paladinSpells.sort_index()

paladinGraph = paladinSpells.plot(kind = "bar", title = "Paladin Spells by Level", color = "#ff752d")
```

To create a dataframe that re-combines all of these data into the basis for a multiple bar graph setting the eight graphs alongside each other, the function ```pd.merge``` is again used. The combined data is then plotted to create a multiple bar graph. The code will not be repeated here for space reasons. 

Next, the code pulls data pertaining to the relationship between spell level and spell school. First, it pulls only the rows containing cantrips, then only the rows containing 1st-level spells, etc., repeating this for each spell level. Then it gathers the rest of the data for those rows, counts how many rows there are for each spell school, and sorts those data, yielding a dataframe for each school of magic that can be used to create graphs of how many spells of each school exist at each spell level.

```
cantrip = classSpellLists['Spell Level'] == 0
cantripSchools = classSpellLists[cantrip].value_counts('Spell School').sort_index()
```
Again,  to create a dataframe that re-combines all of these data into the basis for a multiple bar graph setting the eight graphs alongside each other, the function ```pd.merge``` is used.


Next the code pulls data on how many classes can cast each spell.The original dataframe contains one row for each spell for each class, so to determine how many classes can cast each spell, the code counts how many times each spell name occurs: 

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

In order to determine how many spells of each school are available to how many classes, the code then re-merges the numberOfClasses list with the spell name data and drops superfluous information to leave a dataframe containing spell name, the classes count for each spell, and the school of magic for each spell.

```
combined_df = pd.merge(numberOfClasses, classSpellLists, on='Spell Name')
combined_df = combined_df.drop_duplicates(subset=['Spell Name'])
combined_df = combined_df.drop(columns = ['Class', 'Subclass', 'Spell Level'])
```

It then pulls only the spells available to exactly one class and counts how many there are of each spell school, yielding a dataframe that can be used to create a graph of how many of the spells available to exactly one class belong to each school of magic. 

```
oneclass = combined_df['count'] == 1
oneSchool = combined_df[oneclass].value_counts('Spell School').sort_index()

oneSchoolPlot = oneSchool.plot(kind = "bar", title = "Spells Accessible to Exactly One Class", color = "#005177")
```
It does the same for the rest of the data, again adding in null rows where no data exists (and setting a y-limit on the graph to avoid half-integer labels):

```
fiveSchools = combined_df[fiveclasses].value_counts('Spell School').sort_index()
fiveSchools['illusion'] = 0
fiveSchools['necromancy'] = 0
fiveSchools = fiveSchools.sort_index()

fiveSchoolsPlot = fiveSchools.plot(kind = "bar", title = "Spells Accessible to Exactly Five Classes", color = "#f95882")
plt.ylim(0, 5) 
```

Here, too, to create a dataframe that re-combines all of these data into the basis for a multiple bar graph setting the eight graphs alongside each other, the function ```pd.merge``` is used.

Lastly, the code gathers similar information for the _total_ number of classes with access to each spell. The code is nearly identical, but begins with ```oneclasstotal = combined_df['count'] >= 1``` and similar instead of ```oneclass = combined_df['count'] == 1``` and similar.



**Further Uses:** I'd love to see this work expanded upon. The code could be used as a template for how one might compare other aspects of spells (i.e. range, damage type, casting time, etc.). It could also be used as a starting point for creating a dynamic version of these graphs, where various data types could be selected and unselected to allow for more focused comparisons between a smaller number of categories. Above all, I'd love to see the code used to compare the 2014 and 2024 versions of spells with each other, exploring how the various attribute distributions changed from one version of the game to the next. As the 2024 API is still under construction, this was not yet something I could do.



**Files List:** 

- Muller_Final_Project.ipynb - The project's code.
- classes_per_spell.csv - A list of how many classes each of the 319 spells is available to.
- class_spell_lists.csv - The overall dataframe of spell information.

- Graph of number of spells at each level:
  - spell_level_graph.png  

- Graph of number of spells within each magic school:
  - spell_school_graph.png 

- Graphs showing the number of spells of each school available at each spell level:
  - cantrips_schools.png
  - lvl1_schools.png
  - lvl2_schools.png
  - lvl3_schools.png
  - lvl4_schools.png
  - lvl5_schools.png
  - lvl6_schools.png
  - lvl7_schools.png
  - lv8_schools.png
  - lvl9_schools.png
  - all_lvls_graph.png

- Graph showing the number of classes that can access each spell:
  - classes_per_spell_graph.png

- Graphs showing how many classes (exact) can access each spell:
  - oneschool_graph.png
  - twoschools_graph.png
  - threeschools_graph.png
  - fourschools_graph.png
  - fiveschools_graph.png
  - sixschools_graph.png
  - sevenschools_graph.png
  - allschools_graph.png

- Graphs showing how many classes (total) can access each spell:
  - oneschooltotal_graph.png
  - twoschooltotal_graph.png
  - threeschooltotal_graph.png
  - fourschooltotal_graph.png
  - fiveschooltotal_graph.png
  - sixschooltotal_graph.png
  - sevenschooltotal_graph.png

- Graphs showing the number of spells available to each class at each spell level:
  - bard_graph.png
  - druid_graph.png
  - cleric_graph.png
  - paladin_graph.png
  - ranger_graph.png
  - sorcerer_graph.png
  - warlock_graph.png
  - wizard_graph.png

- A bar graph with the 10 spell levels (0-9) on the x axis, each with a set of bars representing the number of spells of that level available to each class:
  - class_spell_graph.png

- Graphs showing the number of spells of each spell school available to each class:
  - abjuration_graph.png
  - conjuration_graph.png 
  - divination_graph.png
  - enchantment_graph.png
  - evocation_graph.png 
  - illusion_graph.png
  - necromancy_graph.png
  - transmutation_graph.png
  - combined_graph.png

