# Doc ARM

## Conditions arithmétiques

|code(binaire)|code(Hexa)|mnémonique|signification|condition testée|
|:---:|:---:|:---:|:---:|:---:|
|0000|0|EQ| égal|Z|
|0001|1|NE| non égal|!Z|
|0010|2|CS/HS| ≥ dans N|C|
|0011|3|CC/LO| < dans N|!C|
|0100|4|MI| moins N||
|0101|5|PL| plus N||
|0110|6|VS| débordement|V|
|0111|7|VC| pas de débordement|!V|
|1000|8|HI| > dans N|C ∧ !Z|
|1001|9|LS| ≤ dans N|!C ∨ Z|
|1010|A|GE| ≥ dans Z|(N ∧ V ) ∨ (!N ∧ !V )|
|1011|B|LT| < dans Z|(N ∧ !V ) ∨ (!N ∧ V )|
|1100|C|GT| > dans Z|!Z ∧ ((N ∧ V ) ∨ (!N ∧ !V ))|
|1101|D|LE| ≤ dans Z|Z ∨ (N ∧ !V ) ∨ (!N ∧ V )|
|1110|E|AL| toujours||

## Instructions arithmétique ou logiques

### Liste des instructions arithmétique ou logiques


|code-op(Binaire)|code-op(Hexa)| Nom| Explication du nom| Opération |remarque|
|:---:|:---:|:---:|:---:|:---:|:---:|
|0000|0| AND |AND| et bit à bit||
|0001|1| EOR |Exclusive OR| ou exclusif bit à bit||
|0010|2| SUB |SUBstract| soustraction||
|0011|3| RSB |Reverse SuBstract| soustraction inversée||
|0100|4| ADD |ADDition| addition||
|0101|5| ADC |ADdition with Carry| addition avec retenue||
|0110|6| SBC |SuBstract with Carry| soustraction avec emprunt||
|0111|7| RSC |Reverse Substract with Carry| soustraction inversée avec emprunt||
|1000|8| TST |TeST| et bit à bit |pas rd|
|1001|9| TEQ |Test EQuivalence| ou exclusif bit à bit| pas rd|
|1010|A| CMP |CoMPare |soustraction |pas rd|
|1011|B| CMN |CoMpare Not| addition |pas rd|
|1100|C| ORR |OR| ou bit à bit||
|1101|D| MOV |MOVe| copie |pas rn|
|1110|E| BIC |BIt Clear| et not bit à bit||
|1111|F| MVN |MoVe Not| not (complément à 1) |pas rn|

### Encodage des instructions arithmétique ou logiques

| Position | Longueur | Nom       | Explication du nom                                           |
| -------- | :------: | --------- | ------------------------------------------------------------ |
| 31 - 28  |    4     | condition | code de la condition (voir [Conditions arithmétiques](#Conditions arithmétiques)) |
| 27 - 26  |    2     |           |                                                              |
| 25       |    1     | I         | ce bit indique si on utilise une valeur immédiate            |
| 24 - 21  |    4     | code-op   | le code de l'opération donné dans le tableau [Instructions arithmétique ou logiques](#Instructions arithmétique ou logiques) |
| 20       |    1     | S         | ce bit indique si on veut que les codes de condition arithmétique soient mis à jour |
| 19 - 16  |    4     | rn        | première opérande                                            |
| 15 - 12  |    4     | rd        | registre de destination                                      |
| 11 - 0   |    12    | opérande  | deuxième opérande                                            |

### Move

#### Opérandes

| Position | Longueur | Nom                | Explication du nom |
| -------- | :------: | ------------------ | ------------------ |
| 11 - 8   |    4     | valeur de rotation |                    |
| 7 - 0    |    8     | immediate          | valeur en binaire  |

| Position | Longueur | Nom                | Explication du nom |
| -------- | :------: | ------------------ | ------------------ |
| 11 - 8   |    4     | valeur de rotation |                    |
| 7 - 0    |    8     | immediate          | valeur en binaire  |

#### Types de shift

| code | Nom  | Explication du nom |  Opération   | remarque |
| :--: | :--: | :----------------: | :----------: | :------: |
| 0000 | LSR  |        AND         | et bit à bit |          |



