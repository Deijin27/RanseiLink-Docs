
# Types

Pokemon conquest uses the same types and matchup chart as the gen5 games.

The table is stored in arm9.bin at 0x20AE3E4. With rows of attacking type, and columns of defending type, the table uses numeric values to represent effectiveness:

- 0 = Neutral
- 1 = Immune
- 2 = Not Very Effective (0.5x)
- 3 = Super effective (2x)

The following is extracted and mapped from that table: (left = attacking type, top = defending type)

| | Normal | Fire | Water | Electric | Grass | Ice | Fighting | Poison | Ground | Flying | Psychic | Bug | Rock | Ghost | Dragon | Dark | Steel |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Normal | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | <span style="color:red">½</span> | <span style="color:blue">0</span> | 1 | 1 | <span style="color:red">½</span> |
| Fire | 1 | <span style="color:red">½</span> | <span style="color:red">½</span> | 1 | <span style="color:green">2</span> | <span style="color:green">2</span> | 1 | 1 | 1 | 1 | 1 | <span style="color:green">2</span> | <span style="color:red">½</span> | 1 | <span style="color:red">½</span> | 1 | <span style="color:green">2</span> |
| Water | 1 | <span style="color:green">2</span> | <span style="color:red">½</span> | 1 | <span style="color:red">½</span> | 1 | 1 | 1 | <span style="color:green">2</span> | 1 | 1 | 1 | <span style="color:green">2</span> | 1 | <span style="color:red">½</span> | 1 | 1 |
| Electric | 1 | 1 | <span style="color:green">2</span> | <span style="color:red">½</span> | <span style="color:red">½</span> | 1 | 1 | 1 | <span style="color:blue">0</span> | <span style="color:green">2</span> | 1 | 1 | 1 | 1 | <span style="color:red">½</span> | 1 | 1 |
| Grass | 1 | <span style="color:red">½</span> | <span style="color:green">2</span> | 1 | <span style="color:red">½</span> | 1 | 1 | <span style="color:red">½</span> | <span style="color:green">2</span> | <span style="color:red">½</span> | 1 | <span style="color:red">½</span> | <span style="color:green">2</span> | 1 | <span style="color:red">½</span> | 1 | <span style="color:red">½</span> |
| Ice | 1 | <span style="color:red">½</span> | <span style="color:red">½</span> | 1 | <span style="color:green">2</span> | <span style="color:red">½</span> | 1 | 1 | <span style="color:green">2</span> | <span style="color:green">2</span> | 1 | 1 | 1 | 1 | <span style="color:green">2</span> | 1 | <span style="color:red">½</span> |
| Fighting | <span style="color:green">2</span> | 1 | 1 | 1 | 1 | <span style="color:green">2</span> | 1 | <span style="color:red">½</span> | 1 | <span style="color:red">½</span> | <span style="color:red">½</span> | <span style="color:red">½</span> | <span style="color:green">2</span> | <span style="color:blue">0</span> | 1 | <span style="color:green">2</span> | <span style="color:green">2</span> |
| Poison | 1 | 1 | 1 | 1 | <span style="color:green">2</span> | 1 | 1 | <span style="color:red">½</span> | <span style="color:red">½</span> | 1 | 1 | 1 | <span style="color:red">½</span> | <span style="color:red">½</span> | 1 | 1 | <span style="color:blue">0</span> |
| Ground | 1 | <span style="color:green">2</span> | 1 | <span style="color:green">2</span> | <span style="color:red">½</span> | 1 | 1 | <span style="color:green">2</span> | 1 | <span style="color:blue">0</span> | 1 | <span style="color:red">½</span> | <span style="color:green">2</span> | 1 | 1 | 1 | <span style="color:green">2</span> |
| Flying | 1 | 1 | 1 | <span style="color:red">½</span> | <span style="color:green">2</span> | 1 | <span style="color:green">2</span> | 1 | 1 | 1 | 1 | <span style="color:green">2</span> | <span style="color:red">½</span> | 1 | 1 | 1 | <span style="color:red">½</span> |
| Psychic | 1 | 1 | 1 | 1 | 1 | 1 | <span style="color:green">2</span> | <span style="color:green">2</span> | 1 | 1 | <span style="color:red">½</span> | 1 | 1 | 1 | 1 | <span style="color:blue">0</span> | <span style="color:red">½</span> |
| Bug | 1 | <span style="color:red">½</span> | 1 | 1 | <span style="color:green">2</span> | 1 | <span style="color:red">½</span> | <span style="color:red">½</span> | 1 | <span style="color:red">½</span> | <span style="color:green">2</span> | 1 | 1 | <span style="color:red">½</span> | 1 | <span style="color:green">2</span> | <span style="color:red">½</span> |
| Rock | 1 | <span style="color:green">2</span> | 1 | 1 | 1 | <span style="color:green">2</span> | <span style="color:red">½</span> | 1 | <span style="color:red">½</span> | <span style="color:green">2</span> | 1 | <span style="color:green">2</span> | 1 | 1 | 1 | 1 | <span style="color:red">½</span> |
| Ghost | <span style="color:blue">0</span> | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | <span style="color:green">2</span> | 1 | 1 | <span style="color:green">2</span> | 1 | <span style="color:red">½</span> | <span style="color:red">½</span> |
| Dragon | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | <span style="color:green">2</span> | 1 | <span style="color:red">½</span> |
| Dark | 1 | 1 | 1 | 1 | 1 | 1 | <span style="color:red">½</span> | 1 | 1 | 1 | <span style="color:green">2</span> | 1 | 1 | <span style="color:green">2</span> | 1 | <span style="color:red">½</span> | <span style="color:red">½</span> |
| Steel | 1 | <span style="color:red">½</span> | <span style="color:red">½</span> | <span style="color:red">½</span> | 1 | <span style="color:green">2</span> | 1 | 1 | 1 | 1 | 1 | 1 | <span style="color:green">2</span> | 1 | 1 | 1 | <span style="color:red">½</span> |

