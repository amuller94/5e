
**Project Title:** (De)coding the Spellbook: A Comparative Look at Spell Distribution in D&D 5th Edition

**Project Description:** This project draws on an API to create visualizations of some of the different patterns in spell distribution within the 5th Edition (2014) Dungeons & Dragons game system. The [API](https://www.dnd5eapi.co/) is built from the D&D [System Reference Document](https://www.dndbeyond.com/srd) (SRD), the game's most fundamental rule set, designed to be used as a no-license-needed base for third-party content. 

This project looks specifically at the spells portion of that content, which consists of 319 individual items. Each spell has its own set of rules, including which class(es) (i.e. wizard, cleric, druid, etc.) can cast that spell, what school of magic (i.e. transmutation, illusion, necromancy, etc.) the spell belongs to, and what numbered level (0-9) the spell belongs to. These are the three factors that this project focuses on:
1. The distribution of spell schools across spell levels, using a combined visualization as well as one for each level to explore whether more powerful spells are concentrated within any particular school;
2. The spells available to each class, using a combined visualization and as well as one for each class to explore whether certain classes have access to more powerful spells than others;
3. The schools of magic available to each class, using a combined visualization as well as one for each school to explore whether some schools of magic are concentrated in specific spell classes; and
4. The number of spells that exist at each level, offering a visual representation of the spread of (base) levels across all existing (SRD) spells.

**Rationale Statement:** The primary rationale behind the project is simply that I've always been interested in what these types of comparisons within the D&D ruleset would show, and now I have the skillset to find out. While the SRD's content is also available on a number of GUI-based websites, it would've been an enormous amount of work to pull each piece of information manually and collate it all into an Excel document. With Python and an API, that takes just a handful of lines of code, so my time and effort can be put into arranging the data into specific subsets for comparison and creating visualizations. I've been tremendously excited to see the outcomes.

**Workflow:** The code uses the *requests* library to gather data from the API and the *matplotlib* library to make some minor adjustments to graph layout to improve readability. It also uses the library *pandas* for data analysis and manipulation. 

The code's primary interaction with the API is to gather the full list of 319 spells and their corresponding details into a dataframe. It focuses on spell name, spell level, spell school, and spell classes (i.e. the classes associated with the spell). 

It is able to gather subclass information from the API, but these lines of code are currently commented out for two reasons. First, because the SRD makes only one subclass available within each class (as opposed to the much larger number of subclasses available in the *Player's Handbook*). As a result, the subclass data is more of an example set than the broadly representative one I'd hoped for. The second reason I am not using subclass data is that doing so skews the overall data set due to a bard feature called "Magical Secrets." Bards technically have access to all spells in the game through this feature, which the API has erroneously attached to the Lore bard subclass specifically. This means that the exclusion of the Lore subclass leaves only the core bard spell list tagged as bard. As a result, when I encountered this roadblock, I decided to narrow my focus from spells *available* to each class to spells on each class's core spell list. At present, this offers the best representation of the "flavor" of each class's magic.

After pulling data from the API, my code filters it into some smaller dataframes, which it sorts and graphs. I've had to add a few lines of code here and there to ensure that data categories with a zero-count total still show up on the graphs (i.e. paladins don't have any spells above level 5). My code then recombines these dataframes into a basis for a large comparative graph. It does all of this several times using different criteria and exports the graphs as pngs.

**Further Uses:** I'd love to see this work expanded upon. The code could be used as a template for how one might compare other aspects of spells (i.e. range, damage type, casting time, etc.). It could also be used as a starting point for creating a dynamic version of these graphs, where various data types could be selected and unselected to allow for more focused comparisons between a smaller number of categories. Above all, I'd love to see the code used to compare the 2014 and 2024 versions of spells with each other, exploring how the various attribute distributions changed from one version of the game to the next. As the 2024 API is still under construction, this was not yet something I could do.

**Files List** *(to be refined):*
- *muller_5e_project.ipynb* - The project's code.
- *spells final.csv* - The full spell list as initially imported.
- *spells sorted.csv* - The full spell list sorted by class, then spell school, then spell level.
- *abjuration_graph.png, conjuration_graph.png, divination_graph.png, enchantment_graph.png, evocation_graph.png, necromancy_graph.png, transmutation_graph.png* - One graph for each spell school, showing the number of spells of that school available to each class.
- *combined_graph.png* - A bar graph with the eight spellcasting classes on the x axis, each with a set of bars representing the number of spells available to that class in each of the eight spell schools.
- *spell_level_graph.png* - A bar graph of the number of spells of each level.
- *bard_graph.png, cleric_graph.png, druid_graph.png, paladin_graph.png, ranger_graph.png, sorcerer_graph.png, warlock_graph.png, wizard_graph.png* - One graph for each class, showing the number of spells available at each spell level.
- *class_spell_graph.png* - A bar graph with the 10 spell levels (0-9) on the x axis, each with a set of bars representing the number of spells of that level available to each class.
- *class_spells_sorted_by_school.csv* - The full spell list sorted by spell school, then spell level.
- *cantrips_schools.png, lvl1_schools.png, lvl1_schools.png, lvl2_schools.png, lv31_schools.png, lvl4_schools.png, lvl5_schools.png, lvl6_schools.png, lvl7_schools.png, lvl8_schools.png, lvl9_schools.png* - One graph for each spell level, showing the number of spells of each school available at that level. 
- *level_school_graph.png* - A bar graph with the 10 spell levels (0-9) on the x axis, each with a set of bars representing the number of spells of that level from each school.
- *classes_per_spell.csv* - A list of how many classes each of the 319 spells is available to.
- https://amuller94.github.io/5e/ - A github site presenting the information.