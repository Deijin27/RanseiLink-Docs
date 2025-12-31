# Link to Exp Formula

To convert from link to exp, the game uses the following polynomial formula:


$E(L) = \left\lfloor \frac{2L^3 + 9L^2 + 15013L}{300} \right\rfloor$

Which is this code:


```c#
 var tmp = link * (link * (link * 2 + 9) + 0x3aa5);
 var exp =  tmp / 300;
```

The generated arm assembly uses a magic multiplier plus shift in order to do the divide, so the divide by 300 becomes:

```c#
var exp = ((0x1B4E81B5UL * tmp) >> 0x20) >> 0x5;
```

To convert back from exp to link, it just runs through link values from 0-100 until it finds the right one:

```c#
  uint expTemp;
  var link = 0;
  do {
    expTemp = ConvertLinkToExp(link + 1);
    if (exp < expTemp) {
      return link;
    }
    link++;
  } while (link < 100);
  return link;
```