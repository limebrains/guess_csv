Task is to create csv parser that returns using heuristic approach characters representing `separator`, `decimal separator`, `thouseds separator`.

Implement:
1. guess_csv func that takes input of string and return named tuple [1]
2. implement unit tests covering following test cases [2]

[1] - Seps = namedtuple('seps', ['sep', 'decimal', 'thousands'])

[2]
Test case 1
```
            "Ai  ;    B;  C;          D;    E;    F;  G;      H; I\n"
            "aaaa; 3,14; 22; 10.000.000; 29,7; 3,14; 24; 42.000; 29,7\n"
            "aaaa; 3,14; 22; 10.000.000; 29,7; 3,14; 24; 42.000; 29,7\n"
            "aaaa; 3,14; 22; 10.000.000; 29,7; 3,14; 24; 42.000; 29,7\n"
```
`Seps(';', ',', '.')`

Test case 2
```
            "A   ;    B;  C;          D;    E;    F;  G;      H; I ;K\n"
            "aaaa; 3.14; 22; 10,001; 29.7; 3.14; 24; 42,001.0; 29,703;a.z\n"
            "aaaa; 3.14; 22; 10,001; 29.7; 3.14; 24; 42,001.0; 29,703;"
            "a......z\n"
```
`Seps(';', '.', ',')`

Test case 3
```
            "A; B; C; D; E; F; G; H; I\n"
            "aaaa; 3.14; 22; 10,000,000; 29.7; 3.14; 24; 42,000; 29.7\n"
            "aaaa; 3.14; 22; 10,000,000; 29.7; 3.14; 24; 42,000; 29.7\n"
            "aaaa; 3.14; 22; 10,000,000; 29.7; 3.14; 24; 42,000; 29.7\n"
```
`Seps(';', '.', ',')`

```

Test case 4
```
"A| B| C| D| E| F| G| H| I\n"
            "aaaa| 3,14| 22| 10.000.000| 29,7| 3,14| 24| 42.000| 29,7\n"
            "aaaa| 3,14| 22| 10.000.000| 29,7| 3,14| 24| 42.000| 29,7\n"
            "aaaa| 3,14| 22| 10.000.000| 29,7| 3,14| 24| 42.000| 29,7\n"
```
`Seps('|', ',', '.')`

Test case 5
```
            "A, B, C, D, E, F, G, H, I\n"
            "aaaa, 3.14, 22, 10000000, 29.7, 3.14, 24, 42000, 29.7\n"
            "aaaa, 3.14, 22, 10000000, 29.7, 3.14, 24, 42000, 29.7\n"
            "aaaa, 3.14, 22, 10000000, 29.7, 3.14, 24, 42000, 29.7\n"
```
`Seps(',', '.', None)`
