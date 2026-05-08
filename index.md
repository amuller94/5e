# (De)coding the Spellbook: A Comparative Look at Spell Distribution in D&D 5th Edition

---
layout: default
---


This project uses data from a [Dungeons & Dragons API](https://www.dnd5eapi.co/) to create visualizations of some of the different patterns in spell distribution within the game system, specifically its 5th edition (2014). 

D&D is the most popular tabletop roleplaying game (TTRPG) on the market. This is due in part to its Open Gaming License, which gives third parties blanket permission to create their own game supplements based on the D&D's fundamental mechanics. These fundamental mechanics are detailed in something called the System Reference[System Reference Document](https://www.dndbeyond.com/srd), or SRD. 

This project looks specifically at the spells portion of that content. There are 319 spells in the SRD, each with its own set of rules, including which of the eight included spellcasting class(es) (i.e. wizard, cleric, druid, etc.) can cast that spell; what school of magic (i.e. transmutation, illusion, necromancy, etc.) the spell belongs to; and how powerful the spell is, i.e. its numbered level (0-9). It uses visualizations to explore several questions:

> **1. Do some classes have access to more high-level spells than others?**
>
> **2. Are some schools of magic concentrated among specific classes?**
>
> **3. Is there a relationship between spell level and school of magic?**
>


## How many spells are there of each level?

Before delving into the specifics of spell distribution across classes and schools of magic, it makes sense to begin with a visualization of 
<img width="640" height="480" alt="spell_level_graph" src="https://github.com/user-attachments/assets/a08bf697-7f05-4f26-91d7-187607eb57a9"/>



### Header 3
<img width="640" height="480" alt="abjuration_graph" src="https://github.com/user-attachments/assets/3db91fb3-3c36-4963-99d3-ba31880b462d" />

<img width="640" height="480" alt="conjuration_graph" src="https://github.com/user-attachments/assets/57cb7549-cd92-4882-b5b2-a27e0d77f236" />

<img width="640" height="480" alt="divination_graph" src="https://github.com/user-attachments/assets/f548d3be-e8e0-4608-b481-54c9fe0e730c" />

<img width="640" height="480" alt="enchantment_graph" src="https://github.com/user-attachments/assets/bba4f480-a5c6-4f90-b1d1-8de2cb71129f" />

<img width="640" height="480" alt="evocation_graph" src="https://github.com/user-attachments/assets/c8a85202-5ad9-465c-993c-7c345be39343" />

<img width="640" height="480" alt="illusion_graph" src="https://github.com/user-attachments/assets/50335ba6-6c55-4385-8af9-1fd422ff558f" />

<img width="640" height="480" alt="necromancy_graph" src="https://github.com/user-attachments/assets/698541dc-6f76-4288-956b-781fd9a95e9e" />

<img width="640" height="480" alt="transmutation_graph" src="https://github.com/user-attachments/assets/c71d95b0-db0e-4ac8-ae09-252888ec7dad" />

<img width="1500" height="500" alt="combined_graph" src="https://github.com/user-attachments/assets/665f88fd-2e7b-47a0-8c2d-b96395a4da23" />


<img width="640" height="480" alt="bard_graph" src="https://github.
com/user-attachments/assets/f855b9c7-76ea-43c0-b7b9-d421a232dd1e" />
<img width="640" height="480" alt="cleric" src="https://github.com/user-attachments/assets/42224eef-2086-4c0c-b6b2-b48ae25fcdc1" />
<img width="640" height="480" alt="druid_graph" src="https://github.com/user-attachments/assets/bd18c45d-ec0f-400e-a9ea-82c5196e5aae" />
<img width="640" height="480" alt="paladin_graph" src="https://github.com/user-attachments/assets/58f7282d-795b-4174-9702-070906352ab4" />
<img width="640" height="480" alt="ranger_graph" src="https://github.com/user-attachments/assets/cf2e2141-31b3-43a8-834a-17bc2d34a95a" />
<img width="640" height="480" alt="sorcerer_graph" src="https://github.com/user-attachments/assets/bc81cdb5-66b7-454d-9df8-8aedc3fd920b" />
<img width="640" height="480" alt="warlock_graph" src="https://github.com/user-attachments/assets/f93af046-e874-42b6-a660-db9950a8c212" />
<img width="640" height="480" alt="wizard_graph" src="https://github.com/user-attachments/assets/e4995687-237f-4797-803f-a96f3c69c290" />
<img width="1500" height="500" alt="class_spell_graph" src="https://github.com/user-attachments/assets/0d37acd4-beb1-448a-b053-b3c0427b9917" />
<img width="640" height="480" alt="cantrips_schools" src="https://github.com/user-attachments/assets/51b073da-4429-47be-8a84-8a20fe43ae3b" />
<img width="640" height="480" alt="lvl1_schools" src="https://github.com/user-attachments/assets/d8ef1d90-34bf-49df-99f6-3de6ecb3fe55" />
<img width="640" height="480" alt="lvl2_schools" src="https://github.com/user-attachments/assets/b9094d08-31e8-416c-a128-f18bfc787058" />
<img width="640" height="480" alt="lvl3_schools" src="https://github.com/user-attachments/assets/ae02fbf9-ec66-4155-b428-fc58ec0102ff" />
<img width="640" height="480" alt="lvl4_schools" src="https://github.com/user-attachments/assets/839b6547-ad1b-4971-ba7d-83595e9ff8de" />
<img width="640" height="480" alt="lvl5_schools" src="https://github.com/user-attachments/assets/2a492dfd-949a-494c-acef-483516cc4f8d" />
<img width="640" height="480" alt="lvl6_schools" src="https://github.com/user-attachments/assets/dbf42670-44ba-4a29-8d0d-89e871433744" />
<img width="640" height="480" alt="lvl7_schools" src="https://github.com/user-attachments/assets/00d0be33-8658-4699-af7c-5e43eed1a414" />
<img width="640" height="480" alt="lvl8_schools" src="https://github.com/user-attachments/assets/e0320ea7-0380-4065-b4bd-281da9a74ab5" />
<img width="640" height="480" alt="lvl9_schools" src="https://github.com/user-attachments/assets/afa47b72-0580-4e74-8b81-cd49840e34f8" />
<img width="1500" height="500" alt="all_lvls_graph" src="https://github.com/user-attachments/assets/498d07ef-1bfc-4808-9a4a-fdb7879ad73a" />
<img width="640" height="480" alt="classes_per_spell_graph" src="https://github.com/user-attachments/assets/f71adacb-7539-4961-bb98-e63735e515f7" />
<img width="640" height="480" alt="oneschool_graph" src="https://github.com/user-attachments/assets/2624e244-7c78-492f-ad0b-92ee1d305e1b" />
<img width="640" height="480" alt="twoschools_graph" src="https://github.com/user-attachments/assets/2d2d9b32-a594-4f3f-b7d5-927a833be48c" />
<img width="640" height="480" alt="threeschools_graph" src="https://github.com/user-attachments/assets/84f6031a-1d08-4b02-ad20-a8b65becc14c" />
<img width="640" height="480" alt="fourschools_graph" src="https://github.com/user-attachments/assets/7d68d783-db3f-4722-b586-fcd327da6c86" />
<img width="640" height="480" alt="fiveschools_graph" src="https://github.com/user-attachments/assets/545afac2-f218-4a5f-93df-66fe43f6c38c" />
<img width="640" height="480" alt="sixschools_graph" src="https://github.com/user-attachments/assets/72aaae67-bc5f-4a6b-8304-64c5003c85a7" />
<img width="640" height="480" alt="sevenschools_graph" src="https://github.com/user-attachments/assets/8a5300d8-10be-4ce8-b326-f9ac85d93bb0" />
<img width="1500" height="500" alt="allschools_graph" src="https://github.com/user-attachments/assets/4df60fb0-2dcb-427f-9ef7-bc63e854f4e8" />
---
```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

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
