# Regional Differences

Pokémon Conquest was released in different countries, and as it goes with nds games, there is region specific versions of the roms

| Game Code | Region        |
| --------- | ------------- |
| VPYJ      | Japan         |
| VPYT      | North America |
| VPYP      | Europe        |


VPYT and VPYP are mostly the same, only difference I’ve noticed so far is two text changes:

```xml  hl_lines="5 6 11 12" title="Difference between NA (before), and EU (after)"
<changelist>
  <type name="Messages">
    <object name="Block_2_Msg_43">
      <property name="Text">
        <before>Sort by kingdom</before>
        <after_>Sort by Pokédex No.</after_>
      </property>
    </object>
    <object name="Block_17_Msg_190">
      <property name="Text">
        <before>Pokemari brings peace to people's hearts. Ohh, if everyone played it, the world would be a much better place!</before>
        <after_>Pokémari brings peace to people's hearts. Ohh, if everyone played it, the world would be a much better place!</after_>
      </property>
    </object>
  </type>
</changelist>
```

VPYJ is of course in a different language so all the text and many images are changed, but also the block positioning of certain text is changed.
There is also less bytes allocated for names in many of the data files.

