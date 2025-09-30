# Sample Lua Scripts

RanseiConsole supports scripting using Lua. You can run a lua script by:

`dotnet RanseiLink.Console.dll lua "C:\path\to\script.lua"`

As a brief rundown, you have access to the following:

- service (an [IDataService](https://github.com/Deijin27/RanseiLink/blob/master/Core/Services/IDataService.cs), a collection of services with the ability to retrieve and save data)
- [enums](https://github.com/Deijin27/RanseiLink/tree/master/Core/Enums) (provides you with the ids pokemon, moves, etc.)
- lists of all enum items (under then name: \<name\>s e.g. PokemonId -> PokemonIds)

To start with scripting you need to first select or create a mod via the console. You can view your currently selected mod with

`dotnet RanseiLink.Console.dll current mod`

create a mod with

`dotnet RanseiLink.Console.dll create mod "C:\path\to\rom.nds" --name MyMod --author Mia`

when you're done you can write to the rom file with

`dotnet RanseiLink.Console.dll commit mod "C:\path\to\rom.nds"`

## Change Ability

The following script will change umbreon's ability to blaze

```lua
local umbreon = service.Pokemon:Retrieve(5)
umbreon.Ability1 = AbilityId.Blaze
service.Pokemon:Save()
```

all the services follow a similar pattern of `Retrieve` and a single call to `Save` when you're done

## Swap Atk with Def for all pokemon

```lua
for poke in luanet.each(service.Pokemon:Enumerate()) do
    local atk = poke.Atk
    poke.Atk = poke.Def
    poke.Def = atk
end
service.Pokemon:Save()
```
Enumerate method on services returns an IEnumerable of all of the items. Use luanet.each to convert a C# IEnumerable to a lua enumerator.

## Randomize the type of moves

To randomize the type of all moves, we first need a random choice function

```lua
function randomChoice(items)
    return items[math.random(#items)]
end
```

then we can go through each move and set it to a random type

```lua
for move in luanet.each(service.Move:Enumerate()) do
    move.Type = randomChoice(TypeIds)
end

service.Move:Save()
```