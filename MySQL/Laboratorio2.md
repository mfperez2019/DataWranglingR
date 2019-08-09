Laboratorio2
================
Mafer Pérez
7 de agosto de 2019

    ## Loading required package: RMySQL

    ## Warning: package 'RMySQL' was built under R version 3.5.3

    ## Loading required package: DBI

    ##   id          name Gender Eye.color              Race Hair.color Height
    ## 1  0        A-Bomb   Male    yellow             Human    No Hair    203
    ## 2  1    Abe Sapien   Male      blue     Icthyo Sapien    No Hair    191
    ## 3  2      Abin Sur   Male      blue           Ungaran    No Hair    185
    ## 4  3   Abomination   Male     green Human / Radiation    No Hair    203
    ## 5  4       Abraxas   Male      blue     Cosmic Entity      Black    -99
    ## 6  5 Absorbing Man   Male      blue             Human    No Hair    193
    ##           Publisher Skin.color Alignment Weight
    ## 1     Marvel Comics       NULL      good    441
    ## 2 Dark Horse Comics       blue      good     65
    ## 3         DC Comics        red      good     90
    ## 4     Marvel Comics       NULL       bad    441
    ## 5     Marvel Comics       NULL       bad    -99
    ## 6     Marvel Comics       NULL       bad    122

``` r
#Obtener el nombre del superhéroe y casa publicadora de la tabla heroes_information
nombre <- dbGetQuery(mydb, "SELECT name, publisher FROM heroes_information;")
head(nombre)
```

    ##            name         publisher
    ## 1        A-Bomb     Marvel Comics
    ## 2    Abe Sapien Dark Horse Comics
    ## 3      Abin Sur         DC Comics
    ## 4   Abomination     Marvel Comics
    ## 5       Abraxas     Marvel Comics
    ## 6 Absorbing Man     Marvel Comics

    ##            publisher
    ## 1      Marvel Comics
    ## 2  Dark Horse Comics
    ## 3          DC Comics
    ## 4       NBC - Heroes
    ## 5          Wildstorm
    ## 6       Image Comics
    ## 7               <NA>
    ## 8        Icon Comics
    ## 9               SyFy
    ## 10     Hanna-Barbera
    ## 11      George Lucas
    ## 12      Team Epic TV
    ## 13        South Park
    ## 14     HarperCollins
    ## 15       ABC Studios
    ## 16 Universal Studios
    ## 17         Star Trek
    ## 18    IDW Publishing
    ## 19          Shueisha
    ## 20     Sony Pictures
    ## 21     J. K. Rowling
    ## 22       Titan Books
    ## 23         Rebellion
    ## 24         Microsoft
    ## 25  J. R. R. Tolkien

    ##   COUNT(DISTINCT publisher)
    ## 1                        24

    ##   id        name Gender Eye color              Race Hair color Height
    ## 1  0      A-Bomb   Male    yellow             Human    No Hair    203
    ## 2  3 Abomination   Male     green Human / Radiation    No Hair    203
    ## 3 17       Alien   Male      NULL   Xenomorph XX121    No Hair    244
    ## 4 19       Amazo   Male       red           Android       NULL    257
    ## 5 29     Ant-Man   Male      blue             Human      Blond    211
    ## 6 33  Anti-Venom   Male      blue          Symbiote      Blond    229
    ##           Publisher Skin color Alignment Weight
    ## 1     Marvel Comics       NULL      good    441
    ## 2     Marvel Comics       NULL       bad    441
    ## 3 Dark Horse Comics      black       bad    169
    ## 4         DC Comics       NULL       bad    173
    ## 5     Marvel Comics       NULL      good    122
    ## 6     Marvel Comics       NULL      NULL    358

    ##   id              name Gender Eye color  Race Hair color Height
    ## 1  0            A-Bomb   Male    yellow Human    No Hair    203
    ## 2  5     Absorbing Man   Male      blue Human    No Hair    193
    ## 3  7      Adam Strange   Male      blue Human      Blond    185
    ## 4  9         Agent Bob   Male     brown Human      Brown    178
    ## 5 14       Alex Mercer   Male      NULL Human       NULL    -99
    ## 6 16 Alfred Pennyworth   Male      blue Human      Black    178
    ##       Publisher Skin color Alignment Weight
    ## 1 Marvel Comics       NULL      good    441
    ## 2 Marvel Comics       NULL       bad    122
    ## 3     DC Comics       NULL      good     88
    ## 4 Marvel Comics       NULL      good     81
    ## 5     Wildstorm       NULL       bad    -99
    ## 6     DC Comics       NULL      good     72

    ##     id          name Gender Eye color  Race Hair color Height
    ## 1    0        A-Bomb   Male    yellow Human    No Hair    203
    ## 2   29       Ant-Man   Male      blue Human      Blond    211
    ## 3   59          Bane   Male      NULL Human       NULL    203
    ## 4  119      Bloodaxe Female      blue Human      Brown    218
    ## 5  221   Doctor Doom   Male     brown Human      Brown    201
    ## 6  373    Juggernaut   Male      blue Human        Red    287
    ## 7  391       Kingpin   Male      blue Human    No Hair    201
    ## 8  412        Lizard   Male       red Human    No Hair    203
    ## 9  476 Mr Incredible   Male      blue Human      Blond    201
    ## 10 557           Rey Female     hazel Human      Brown    297
    ## 11 583      Scorpion   Male     brown Human      Brown    211
    ## 12 591      She-Hulk Female     green Human      Green    201
    ##            Publisher Skin color Alignment Weight
    ## 1      Marvel Comics       NULL      good    441
    ## 2      Marvel Comics       NULL      good    122
    ## 3          DC Comics       NULL       bad    180
    ## 4      Marvel Comics       NULL       bad    495
    ## 5      Marvel Comics       NULL       bad    187
    ## 6      Marvel Comics       NULL   neutral    855
    ## 7      Marvel Comics       NULL       bad    203
    ## 8      Marvel Comics       NULL       bad    230
    ## 9  Dark Horse Comics       NULL      good    158
    ## 10      George Lucas       NULL      good    -99
    ## 11     Marvel Comics       NULL       bad    310
    ## 12     Marvel Comics       NULL      good    315

    ##   count(name)
    ## 1          98

    ##   COUNT(`eye color`)
    ## 1                271

    ##                 name weight
    ## 1      Absorbing Man    122
    ## 2         Agent Zero    104
    ## 3         Air-Walker    108
    ## 4              Alien    169
    ## 5              Amazo    173
    ## 6               Ammo    101
    ## 7            Ant-Man    122
    ## 8         Apocalypse    135
    ## 9            Aqualad    106
    ## 10           Aquaman    146
    ## 11             Atlas    101
    ## 12             Atlas    126
    ## 13              Bane    180
    ## 14        Battlestar    133
    ## 15             Beast    181
    ## 16         Big Barda    135
    ## 17            Bishop    124
    ## 18           Bizarro    155
    ## 19        Black Adam    113
    ## 20          Blackout    104
    ## 21           Box III    110
    ## 22          Brainiac    135
    ## 23             Cable    158
    ## 24   Captain America    108
    ## 25   Captain Britain    116
    ## 26  Captain Mar-vell    108
    ## 27    Captain Marvel    101
    ## 28     Citizen Steel    170
    ## 29    Crimson Dynamo    104
    ## 30            Cyborg    173
    ## 31       Darth Vader    135
    ## 32          Deathlok    178
    ## 33       Deathstroke    101
    ## 34        Doc Samson    171
    ## 35       Doctor Doom    187
    ## 36    Doctor Doom II    132
    ## 37    Doctor Octopus    110
    ## 38      Doppelganger    104
    ## 39          Evilhawk    106
    ## 40            Falcon    108
    ## 41            Frenzy    104
    ## 42            Frigga    167
    ## 43   Granny Goodness    115
    ## 44           Hawkeye    104
    ## 45           Hellboy    158
    ## 46          Hercules    146
    ## 47         Hydro-Man    119
    ## 48          Iron Man    191
    ## 49            Jigsaw    113
    ## 50              Kang    104
    ## 51 Kraven the Hunter    106
    ## 52         Luke Cage    191
    ## 53 Martian Manhunter    135
    ## 54          Maverick    110
    ## 55          Mephisto    140
    ## 56             Mimic    101
    ## 57   Mister Sinister    128
    ## 58       Moon Knight    101
    ## 59     Mr Incredible    158
    ## 60             Namor    125
    ## 61          Namorita    101
    ## 62         Omega Red    191
    ## 63        Paul Blart    117
    ## 64     Razor-Fist II    117
    ## 65         Red Skull    108
    ## 66       Red Tornado    146
    ## 67          Robin II    101
    ## 68             Ronin    104
    ## 69        Sabretooth    171
    ## 70 Scarlet Spider II    113
    ## 71       Shadow King    149
    ## 72         She-Thing    153
    ## 73               Sif    191
    ## 74     Silver Surfer    101
    ## 75             Skaar    180
    ## 76       Space Ghost    113
    ## 77             Steel    131
    ## 78          Superman    101
    ## 79            T-1000    146
    ## 80             T-800    176
    ## 81             T-850    198
    ## 82               T-X    149
    ## 83      The Comedian    101
    ## 84         Thor Girl    143
    ## 85       Thunderbird    101
    ## 86           Thundra    158
    ## 87             Toxin    117
    ## 88         Ultragirl    105
    ## 89             Venom    117
    ## 90            Vision    135
    ## 91         Vision II    135
    ## 92            Walrus    162
    ## 93           Warlock    108
    ## 94           Warpath    158
    ## 95    Winter Soldier    117
    ## 96         Wolverine    135
    ## 97        Wonder Man    171
    ## 98    Wyatt Wingfoot    117

    ##                  name weight height
    ## 1               MODOK    338    366
    ## 2           Wolfsbane    473    366
    ## 3           Onslaught    405    305
    ## 4           Sasquatch    900    305
    ## 5          Juggernaut    855    287
    ## 6      Solomon Grundy    437    279
    ## 7            Darkseid    817    267
    ## 8            Doomsday    412    244
    ## 9                Hulk    630    244
    ## 10        Killer Croc    356    244
    ## 11            Kilowog    324    234
    ## 12         Anti-Venom    358    229
    ## 13               Lobo    288    229
    ## 14          Venom III    334    229
    ## 15           Colossus    225    226
    ## 16           Bloodaxe    495    218
    ## 17               Hela    225    213
    ## 18          Man-Thing    225    213
    ## 19           Predator    234    213
    ## 20           Red Hulk    630    213
    ## 21           Scorpion    310    211
    ## 22              Spawn    405    211
    ## 23               Odin    293    206
    ## 24             Ultron    331    206
    ## 25             A-Bomb    441    203
    ## 26        Abomination    441    203
    ## 27             Lizard    230    203
    ## 28      Beta Ray Bill    216    201
    ## 29            Kingpin    203    201
    ## 30           She-Hulk    315    201
    ## 31             Thanos    443    201
    ## 32          Gladiator    268    198
    ## 33      Gorilla Grodd    270    198
    ## 34       Living Brain    360    198
    ## 35               Thor    288    198
    ## 36      Thunderstrike    288    198
    ## 37         Molten Man    248    196
    ## 38              Rhino    320    196
    ## 39 Drax the Destroyer    306    193
    ## 40            Etrigan    203    193
    ## 41               Loki    236    193
    ## 42           Valkyrie    214    191
    ## 43          Destroyer    383    188
    ## 44               Ares    270    185
    ## 45            Sandman    203    185
    ## 46        Tiger Shark    203    185
    ## 47           Hyperion    207    183
    ## 48        Machine Man    383    183
    ## 49              Thing    225    183
    ## 50               Blob    230    178

    ##                          name               race
    ## 1                      A-Bomb              Human
    ## 2                  Abe Sapien      Icthyo Sapien
    ## 3                    Abin Sur            Ungaran
    ## 4                 Abomination  Human / Radiation
    ## 5                     Abraxas      Cosmic Entity
    ## 6               Absorbing Man              Human
    ## 7                 Adam Monroe               NULL
    ## 8                Adam Strange              Human
    ## 9                    Agent 13               NULL
    ## 10                  Agent Bob              Human
    ## 11                 Agent Zero               NULL
    ## 12                 Air-Walker               NULL
    ## 13                       Ajax             Cyborg
    ## 14                 Alan Scott               NULL
    ## 15                Alex Mercer              Human
    ## 16               Alex Woolsly               NULL
    ## 17          Alfred Pennyworth              Human
    ## 18                      Alien    Xenomorph XX121
    ## 19           Allan Quatermain               NULL
    ## 20                      Amazo            Android
    ## 21                       Ammo              Human
    ## 22             Ando Masahashi               NULL
    ## 23                      Angel               NULL
    ## 24                      Angel            Vampire
    ## 25                 Angel Dust             Mutant
    ## 26            Angel Salvadore               NULL
    ## 27                     Angela               NULL
    ## 28                 Animal Man              Human
    ## 29                  Annihilus               NULL
    ## 30                    Ant-Man              Human
    ## 31                 Ant-Man II              Human
    ## 32               Anti-Monitor      God / Eternal
    ## 33                 Anti-Spawn               NULL
    ## 34                 Anti-Venom           Symbiote
    ## 35                 Apocalypse             Mutant
    ## 36                   Aquababy               NULL
    ## 37                    Aqualad          Atlantean
    ## 38                    Aquaman          Atlantean
    ## 39                    Arachne              Human
    ## 40                  Archangel             Mutant
    ## 41                   Arclight               NULL
    ## 42                     Ardina              Alien
    ## 43                       Ares               NULL
    ## 44                      Ariel               NULL
    ## 45                      Armor               NULL
    ## 46                    Arsenal              Human
    ## 47                  Astro Boy               NULL
    ## 48                      Atlas      God / Eternal
    ## 49                      Atlas             Mutant
    ## 50                       Atom               NULL
    ## 51                       Atom               NULL
    ## 52                  Atom Girl               NULL
    ## 53                    Atom II              Human
    ## 54                   Atom III               NULL
    ## 55                    Atom IV               NULL
    ## 56                     Aurora             Mutant
    ## 57                     Azazel           Neyaphem
    ## 58                     Azrael              Human
    ## 59                      Aztar               NULL
    ## 60                       Bane              Human
    ## 61                    Banshee              Human
    ## 62                     Bantam               NULL
    ## 63                    Batgirl              Human
    ## 64                    Batgirl               NULL
    ## 65                Batgirl III               NULL
    ## 66                 Batgirl IV              Human
    ## 67                  Batgirl V               NULL
    ## 68                 Batgirl VI               NULL
    ## 69                     Batman              Human
    ## 70                     Batman              Human
    ## 71                  Batman II              Human
    ## 72                 Battlestar               NULL
    ## 73                 Batwoman V              Human
    ## 74                       Beak               NULL
    ## 75                      Beast             Mutant
    ## 76                  Beast Boy              Human
    ## 77                     Beetle               NULL
    ## 78                     Ben 10               NULL
    ## 79              Beta Ray Bill               NULL
    ## 80                   Beyonder      God / Eternal
    ## 81                  Big Barda            New God
    ## 82                  Big Daddy               NULL
    ## 83                    Big Man               NULL
    ## 84                Bill Harken              Alpha
    ## 85              Billy Kincaid               NULL
    ## 86                     Binary               NULL
    ## 87               Bionic Woman             Cyborg
    ## 88                 Bird-Brain               NULL
    ## 89                   Bird-Man              Human
    ## 90                Bird-Man II              Human
    ## 91                    Birdman      God / Eternal
    ## 92                     Bishop             Mutant
    ## 93                    Bizarro            Bizarro
    ## 94               Black Abbott               NULL
    ## 95                 Black Adam               NULL
    ## 96                 Black Bolt            Inhuman
    ## 97               Black Canary              Human
    ## 98               Black Canary          Metahuman
    ## 99                  Black Cat              Human
    ## 100               Black Flash      God / Eternal
    ## 101             Black Goliath               NULL
    ## 102          Black Knight III              Human
    ## 103           Black Lightning               NULL
    ## 104               Black Mamba               NULL
    ## 105               Black Manta              Human
    ## 106             Black Panther              Human
    ## 107               Black Widow              Human
    ## 108            Black Widow II               NULL
    ## 109                  Blackout              Demon
    ## 110                 Blackwing               NULL
    ## 111                 Blackwulf              Alien
    ## 112                     Blade            Vampire
    ## 113               Blaquesmith               NULL
    ## 114                    Bling!               NULL
    ## 115                     Blink             Mutant
    ## 116                  Blizzard               NULL
    ## 117                  Blizzard               NULL
    ## 118               Blizzard II               NULL
    ## 119                      Blob               NULL
    ## 120                  Bloodaxe              Human
    ## 121                 Bloodhawk             Mutant
    ## 122               Bloodwraith               NULL
    ## 123               Blue Beetle               NULL
    ## 124               Blue Beetle               NULL
    ## 125            Blue Beetle II               NULL
    ## 126           Blue Beetle III              Human
    ## 127                 Boba Fett      Human / Clone
    ## 128                      Bolt               NULL
    ## 129                Bomb Queen               NULL
    ## 130                 Boom-Boom             Mutant
    ## 131                    Boomer               NULL
    ## 132              Booster Gold              Human
    ## 133                       Box               NULL
    ## 134                   Box III               NULL
    ## 135                    Box IV               NULL
    ## 136                  Brainiac            Android
    ## 137                Brainiac 5               NULL
    ## 138            Brother Voodoo              Human
    ## 139                Brundlefly             Mutant
    ## 140                     Buffy              Human
    ## 141                  Bullseye              Human
    ## 142                 Bumblebee              Human
    ## 143                 Bumbleboy               NULL
    ## 144                   Bushido              Human
    ## 145                     Cable             Mutant
    ## 146                  Callisto               NULL
    ## 147             Cameron Hicks              Alpha
    ## 148                Cannonball               NULL
    ## 149           Captain America              Human
    ## 150              Captain Atom  Human / Radiation
    ## 151           Captain Britain              Human
    ## 152              Captain Cold              Human
    ## 153              Captain Epic               NULL
    ## 154         Captain Hindsight              Human
    ## 155          Captain Mar-vell               NULL
    ## 156            Captain Marvel              Human
    ## 157            Captain Marvel         Human-Kree
    ## 158         Captain Marvel II              Human
    ## 159          Captain Midnight              Human
    ## 160            Captain Planet      God / Eternal
    ## 161          Captain Universe      God / Eternal
    ## 162                   Carnage           Symbiote
    ## 163                       Cat               NULL
    ## 164                    Cat II               NULL
    ## 165                  Catwoman              Human
    ## 166             Cecilia Reyes               NULL
    ## 167                   Century              Alien
    ## 168                   Cerebra             Mutant
    ## 169                   Chamber             Mutant
    ## 170                 Chameleon               NULL
    ## 171                Changeling               NULL
    ## 172                   Cheetah              Human
    ## 173                Cheetah II              Human
    ## 174               Cheetah III              Human
    ## 175                   Chromos               NULL
    ## 176              Chuck Norris               NULL
    ## 177             Citizen Steel              Human
    ## 178             Claire Bennet               NULL
    ## 179                      Clea               NULL
    ## 180                     Cloak               NULL
    ## 181                Clock King              Human
    ## 182                Cogliostro               NULL
    ## 183              Colin Wagner               NULL
    ## 184              Colossal Boy               NULL
    ## 185                  Colossus             Mutant
    ## 186                   Copycat             Mutant
    ## 187                   Corsair               NULL
    ## 188               Cottonmouth              Human
    ## 189          Crimson Crusader               NULL
    ## 190            Crimson Dynamo               NULL
    ## 191                   Crystal            Inhuman
    ## 192                     Curse               NULL
    ## 193                    Cy-Gor               NULL
    ## 194                    Cyborg             Cyborg
    ## 195           Cyborg Superman             Cyborg
    ## 196                   Cyclops             Mutant
    ## 197                    Cypher               NULL
    ## 198                    Dagger               NULL
    ## 199              Danny Cooper               NULL
    ## 200             Daphne Powell               NULL
    ## 201                 Daredevil              Human
    ## 202                  Darkhawk              Human
    ## 203                   Darkman               NULL
    ## 204                  Darkseid            New God
    ## 205                  Darkside               NULL
    ## 206                  Darkstar             Mutant
    ## 207                Darth Maul Dathomirian Zabrak
    ## 208               Darth Vader             Cyborg
    ## 209                      Dash              Human
    ## 210                      Data            Android
    ## 211                   Dazzler             Mutant
    ## 212                   Deadman              Human
    ## 213                  Deadpool             Mutant
    ## 214                  Deadshot              Human
    ## 215                  Deathlok             Cyborg
    ## 216               Deathstroke              Human
    ## 217                Demogoblin              Demon
    ## 218                 Destroyer               NULL
    ## 219               Diamondback              Human
    ## 220                DL Hawkins               NULL
    ## 221                Doc Samson  Human / Radiation
    ## 222               Doctor Doom              Human
    ## 223            Doctor Doom II               NULL
    ## 224               Doctor Fate              Human
    ## 225            Doctor Octopus              Human
    ## 226            Doctor Strange              Human
    ## 227                    Domino              Human
    ## 228                 Donatello             Mutant
    ## 229                Donna Troy             Amazon
    ## 230                  Doomsday              Alien
    ## 231              Doppelganger               NULL
    ## 232                  Dormammu               NULL
    ## 233              Dr Manhattan     Human / Cosmic
    ## 234        Drax the Destroyer    Human / Altered
    ## 235                       Ego               NULL
    ## 236                Elastigirl              Human
    ## 237                   Electro              Human
    ## 238                   Elektra              Human
    ## 239               Elle Bishop               NULL
    ## 240             Elongated Man               NULL
    ## 241                Emma Frost               NULL
    ## 242               Enchantress              Human
    ## 243                    Energy               NULL
    ## 244                     ERG-1               NULL
    ## 245                Ethan Hunt              Human
    ## 246                   Etrigan              Demon
    ## 247             Evil Deadpool             Mutant
    ## 248                  Evilhawk              Alien
    ## 249                    Exodus             Mutant
    ## 250             Fabian Cortez               NULL
    ## 251                    Falcon              Human
    ## 252             Fallen One II               NULL
    ## 253                     Faora         Kryptonian
    ## 254                     Feral               NULL
    ## 255           Fighting Spirit               NULL
    ## 256             Fin Fang Foom    Kakarantharaian
    ## 257                  Firebird               NULL
    ## 258                  Firelord               NULL
    ## 259                  Firestar             Mutant
    ## 260                 Firestorm              Human
    ## 261                 Firestorm               NULL
    ## 262                     Fixer               NULL
    ## 263                     Flash              Human
    ## 264              Flash Gordon               NULL
    ## 265                  Flash II              Human
    ## 266                 Flash III              Human
    ## 267                  Flash IV              Human
    ## 268                     Forge               NULL
    ## 269         Franklin Richards             Mutant
    ## 270            Franklin Storm               NULL
    ## 271                    Frenzy               NULL
    ## 272                    Frigga               NULL
    ## 273                  Galactus      Cosmic Entity
    ## 274                    Gambit             Mutant
    ## 275                    Gamora      Zen-Whoberian
    ## 276               Garbage Man             Mutant
    ## 277                 Gary Bell              Alpha
    ## 278               General Zod         Kryptonian
    ## 279                   Genesis               NULL
    ## 280               Ghost Rider              Demon
    ## 281            Ghost Rider II               NULL
    ## 282                 Giant-Man              Human
    ## 283              Giant-Man II               NULL
    ## 284                   Giganta               NULL
    ## 285                 Gladiator          Strontian
    ## 286              Goblin Queen               NULL
    ## 287                  Godzilla              Kaiju
    ## 288                       Gog               NULL
    ## 289                      Goku             Saiyan
    ## 290                   Goliath              Human
    ## 291                   Goliath              Human
    ## 292                   Goliath               NULL
    ## 293                Goliath IV               NULL
    ## 294             Gorilla Grodd            Gorilla
    ## 295           Granny Goodness               NULL
    ## 296                   Gravity              Human
    ## 297                    Greedo             Rodian
    ## 298               Green Arrow              Human
    ## 299              Green Goblin              Human
    ## 300           Green Goblin II               NULL
    ## 301          Green Goblin III               NULL
    ## 302           Green Goblin IV               NULL
    ## 303                     Groot     Flora Colossus
    ## 304                  Guardian              Human
    ## 305               Guy Gardner    Human-Vuldarian
    ## 306                Hal Jordan              Human
    ## 307                  Han Solo              Human
    ## 308                   Hancock              Human
    ## 309              Harley Quinn              Human
    ## 310              Harry Potter              Human
    ## 311                     Havok             Mutant
    ## 312                      Hawk               NULL
    ## 313                   Hawkeye              Human
    ## 314                Hawkeye II              Human
    ## 315                  Hawkgirl               NULL
    ## 316                   Hawkman               NULL
    ## 317                 Hawkwoman               NULL
    ## 318              Hawkwoman II               NULL
    ## 319             Hawkwoman III               NULL
    ## 320                 Heat Wave              Human
    ## 321                      Hela          Asgardian
    ## 322                   Hellboy              Demon
    ## 323                   Hellcat              Human
    ## 324                 Hellstorm               NULL
    ## 325                  Hercules           Demi-God
    ## 326             Hiro Nakamura               NULL
    ## 327                  Hit-Girl              Human
    ## 328                 Hobgoblin               NULL
    ## 329                    Hollow               NULL
    ## 330              Hope Summers               NULL
    ## 331           Howard the Duck               NULL
    ## 332                      Hulk  Human / Radiation
    ## 333               Human Torch  Human / Radiation
    ## 334                  Huntress               NULL
    ## 335                      Husk             Mutant
    ## 336                    Hybrid           Symbiote
    ## 337                 Hydro-Man               NULL
    ## 338                  Hyperion            Eternal
    ## 339                    Iceman             Mutant
    ## 340                   Impulse              Human
    ## 341             Indiana Jones              Human
    ## 342                    Indigo              Alien
    ## 343                       Ink             Mutant
    ## 344           Invisible Woman  Human / Radiation
    ## 345                 Iron Fist              Human
    ## 346                  Iron Man              Human
    ## 347               Iron Monger               NULL
    ## 348                      Isis               NULL
    ## 349                Jack Bauer               NULL
    ## 350            Jack of Hearts              Human
    ## 351                 Jack-Jack              Human
    ## 352                James Bond              Human
    ## 353             James T. Kirk              Human
    ## 354             Jar Jar Binks             Gungan
    ## 355              Jason Bourne              Human
    ## 356                 Jean Grey             Mutant
    ## 357           Jean-Luc Picard              Human
    ## 358             Jennifer Kale               NULL
    ## 359               Jesse Quick              Human
    ## 360              Jessica Cruz              Human
    ## 361             Jessica Jones              Human
    ## 362           Jessica Sanders               NULL
    ## 363                    Jigsaw               NULL
    ## 364                Jim Powell               NULL
    ## 365                 JJ Powell               NULL
    ## 366             Johann Krauss               NULL
    ## 367          John Constantine              Human
    ## 368              John Stewart              Human
    ## 369               John Wraith               NULL
    ## 370                     Joker              Human
    ## 371                      Jolt               NULL
    ## 372                   Jubilee             Mutant
    ## 373               Judge Dredd              Human
    ## 374                Juggernaut              Human
    ## 375                  Junkpile             Mutant
    ## 376                   Justice              Human
    ## 377                  Jyn Erso              Human
    ## 378                     K-2SO            Android
    ## 379                      Kang               NULL
    ## 380                Karate Kid              Human
    ## 381           Kathryn Janeway              Human
    ## 382          Katniss Everdeen              Human
    ## 383                  Kevin 11              Human
    ## 384                  Kick-Ass              Human
    ## 385                 Kid Flash              Human
    ## 386              Kid Flash II               NULL
    ## 387               Killer Croc          Metahuman
    ## 388              Killer Frost              Human
    ## 389                   Kilowog         Bolovaxian
    ## 390                 King Kong             Animal
    ## 391                King Shark             Animal
    ## 392                   Kingpin              Human
    ## 393                      Klaw              Human
    ## 394              Kool-Aid Man               NULL
    ## 395                 Kraven II              Human
    ## 396         Kraven the Hunter              Human
    ## 397                    Krypto         Kryptonian
    ## 398               Kyle Rayner              Human
    ## 399                  Kylo Ren              Human
    ## 400             Lady Bullseye               NULL
    ## 401          Lady Deathstrike             Cyborg
    ## 402                    Leader               NULL
    ## 403                     Leech               NULL
    ## 404                    Legion             Mutant
    ## 405                  Leonardo             Mutant
    ## 406                Lex Luthor              Human
    ## 407                Light Lass               NULL
    ## 408             Lightning Lad               NULL
    ## 409            Lightning Lord               NULL
    ## 410              Living Brain               NULL
    ## 411           Living Tribunal      Cosmic Entity
    ## 412               Liz Sherman               NULL
    ## 413                    Lizard              Human
    ## 414                      Lobo           Czarnian
    ## 415                      Loki          Asgardian
    ## 416                  Longshot              Human
    ## 417                 Luke Cage              Human
    ## 418             Luke Campbell               NULL
    ## 419            Luke Skywalker              Human
    ## 420                      Luna              Human
    ## 421                      Lyja               NULL
    ## 422                   Mach-IV               NULL
    ## 423               Machine Man               NULL
    ## 424                   Magneto             Mutant
    ## 425                     Magog               NULL
    ## 426                     Magus               NULL
    ## 427           Man of Miracles      God / Eternal
    ## 428                   Man-Bat              Human
    ## 429                 Man-Thing               NULL
    ## 430                  Man-Wolf               NULL
    ## 431                  Mandarin              Human
    ## 432                    Mantis         Human-Kree
    ## 433         Martian Manhunter            Martian
    ## 434               Marvel Girl               NULL
    ## 435              Master Brood               NULL
    ## 436              Master Chief    Human / Altered
    ## 437                     Match               NULL
    ## 438              Matt Parkman               NULL
    ## 439                  Maverick               NULL
    ## 440                    Maxima               NULL
    ## 441              Maya Herrera               NULL
    ## 442                    Medusa            Inhuman
    ## 443                  Meltdown               NULL
    ## 444                  Mephisto               NULL
    ## 445                      Mera          Atlantean
    ## 446                   Metallo            Android
    ## 447                Metamorpho               NULL
    ## 448                 Meteorite               NULL
    ## 449                    Metron               NULL
    ## 450             Micah Sanders               NULL
    ## 451              Michelangelo             Mutant
    ## 452                 Micro Lad               NULL
    ## 453                     Mimic               NULL
    ## 454              Minna Murray               NULL
    ## 455                    Misfit               NULL
    ## 456              Miss Martian               NULL
    ## 457          Mister Fantastic  Human / Radiation
    ## 458             Mister Freeze              Human
    ## 459              Mister Knife            Spartoi
    ## 460           Mister Mxyzptlk      God / Eternal
    ## 461           Mister Sinister    Human / Altered
    ## 462              Mister Zsasz              Human
    ## 463               Mockingbird              Human
    ## 464                     MODOK             Cyborg
    ## 465                      Mogo             Planet
    ## 466           Mohinder Suresh               NULL
    ## 467                    Moloch               NULL
    ## 468                Molten Man               NULL
    ## 469                   Monarch               NULL
    ## 470             Monica Dawson               NULL
    ## 471               Moon Knight              Human
    ## 472                 Moonstone               NULL
    ## 473                    Morlun               NULL
    ## 474                     Morph               NULL
    ## 475              Moses Magnum               NULL
    ## 476               Mr Immortal             Mutant
    ## 477             Mr Incredible              Human
    ## 478              Ms Marvel II               NULL
    ## 479              Multiple Man               NULL
    ## 480                  Mysterio              Human
    ## 481                  Mystique             Mutant
    ## 482                     Namor          Atlantean
    ## 483                     Namor               NULL
    ## 484                    Namora               NULL
    ## 485                  Namorita               NULL
    ## 486            Naruto Uzumaki              Human
    ## 487           Nathan Petrelli               NULL
    ## 488                    Nebula          Luphomoid
    ## 489 Negasonic Teenage Warhead             Mutant
    ## 490                 Nick Fury              Human
    ## 491              Nightcrawler               NULL
    ## 492                 Nightwing              Human
    ## 493              Niki Sanders               NULL
    ## 494              Nina Theroux              Alpha
    ## 495               Nite Owl II               NULL
    ## 496                 Northstar               NULL
    ## 497                      Nova              Human
    ## 498                      Nova     Human / Cosmic
    ## 499                      Odin      God / Eternal
    ## 500                 Offspring               NULL
    ## 501                 Omega Red               NULL
    ## 502                Omniscient               NULL
    ## 503             One Punch Man              Human
    ## 504             One-Above-All      Cosmic Entity
    ## 505                 Onslaught             Mutant
    ## 506                    Oracle              Human
    ## 507                    Osiris               NULL
    ## 508                 Overtkill               NULL
    ## 509                Ozymandias              Human
    ## 510                 Parademon          Parademon
    ## 511                Paul Blart              Human
    ## 512                   Penance               NULL
    ## 513                 Penance I               NULL
    ## 514                Penance II               NULL
    ## 515                   Penguin              Human
    ## 516            Peter Petrelli               NULL
    ## 517                   Phantom               NULL
    ## 518              Phantom Girl               NULL
    ## 519                   Phoenix             Mutant
    ## 520                  Plantman             Mutant
    ## 521               Plastic Lad               NULL
    ## 522               Plastic Man              Human
    ## 523                 Plastique               NULL
    ## 524                Poison Ivy              Human
    ## 525                   Polaris             Mutant
    ## 526                Power Girl         Kryptonian
    ## 527                 Power Man             Mutant
    ## 528                  Predator             Yautja
    ## 529               Professor X             Mutant
    ## 530            Professor Zoom              Human
    ## 531              Proto-Goblin               NULL
    ## 532                  Psylocke             Mutant
    ## 533                  Punisher              Human
    ## 534                Purple Man              Human
    ## 535                      Pyro               NULL
    ## 536                         Q      God / Eternal
    ## 537                   Quantum               NULL
    ## 538                  Question              Human
    ## 539               Quicksilver             Mutant
    ## 540                     Quill               NULL
    ## 541              Ra's Al Ghul              Human
    ## 542             Rachel Pirzad              Alpha
    ## 543                     Rambo              Human
    ## 544                   Raphael             Mutant
    ## 545                     Raven              Human
    ## 546                       Ray              Human
    ## 547             Razor-Fist II               NULL
    ## 548                 Red Arrow              Human
    ## 549                  Red Hood              Human
    ## 550                  Red Hulk  Human / Radiation
    ## 551                  Red Mist               NULL
    ## 552                 Red Robin              Human
    ## 553                 Red Skull               NULL
    ## 554               Red Tornado            Android
    ## 555               Redeemer II               NULL
    ## 556              Redeemer III               NULL
    ## 557              Renata Soliz               NULL
    ## 558                       Rey              Human
    ## 559                     Rhino  Human / Radiation
    ## 560                 Rick Flag               NULL
    ## 561                   Riddler               NULL
    ## 562                Rip Hunter              Human
    ## 563                   Ripcord               NULL
    ## 564                     Robin              Human
    ## 565                  Robin II              Human
    ## 566                 Robin III              Human
    ## 567                   Robin V              Human
    ## 568                  Robin VI              Human
    ## 569            Rocket Raccoon             Animal
    ## 570                     Rogue               NULL
    ## 571                     Ronin              Human
    ## 572                 Rorschach              Human
    ## 573                Sabretooth             Mutant
    ## 574                      Sage               NULL
    ## 575                   Sandman              Human
    ## 576                 Sasquatch               NULL
    ## 577                    Sauron              Maiar
    ## 578             Savage Dragon               NULL
    ## 579                 Scarecrow              Human
    ## 580            Scarlet Spider              Human
    ## 581         Scarlet Spider II              Clone
    ## 582             Scarlet Witch             Mutant
    ## 583                   Scorpia               NULL
    ## 584                  Scorpion              Human
    ## 585            Sebastian Shaw             Mutant
    ## 586                    Sentry             Mutant
    ## 587               Shadow King               NULL
    ## 588               Shadow Lass           Talokite
    ## 589                 Shadowcat             Mutant
    ## 590                 Shang-Chi              Human
    ## 591               Shatterstar               NULL
    ## 592                  She-Hulk              Human
    ## 593                 She-Thing  Human / Radiation
    ## 594                   Shocker              Human
    ## 595                    Shriek               NULL
    ## 596          Shrinking Violet               NULL
    ## 597                       Sif          Asgardian
    ## 598                      Silk              Human
    ## 599              Silk Spectre               NULL
    ## 600           Silk Spectre II               NULL
    ## 601             Silver Surfer              Alien
    ## 602                Silverclaw               NULL
    ## 603                 Simon Baz              Human
    ## 604                  Sinestro          Korugaran
    ## 605                     Siren          Atlantean
    ## 606                  Siren II               NULL
    ## 607                     Siryn               NULL
    ## 608                     Skaar               NULL
    ## 609                Snake-Eyes             Animal
    ## 610                  Snowbird               NULL
    ## 611                     Sobek               NULL
    ## 612            Solomon Grundy             Zombie
    ## 613                  Songbird               NULL
    ## 614               Space Ghost              Human
    ## 615                     Spawn              Demon
    ## 616                   Spectre      God / Eternal
    ## 617                 Speedball               NULL
    ## 618                    Speedy              Human
    ## 619                    Speedy              Human
    ## 620            Spider-Carnage           Symbiote
    ## 621               Spider-Girl              Human
    ## 622               Spider-Gwen              Human
    ## 623                Spider-Man              Human
    ## 624                Spider-Man              Human
    ## 625                Spider-Man              Human
    ## 626              Spider-Woman              Human
    ## 627           Spider-Woman II               NULL
    ## 628          Spider-Woman III               NULL
    ## 629           Spider-Woman IV               NULL
    ## 630                     Spock       Human-Vulcan
    ## 631                     Spyke             Mutant
    ## 632                   Stacy X               NULL
    ## 633                 Star-Lord      Human-Spartoi
    ## 634                  Stardust               NULL
    ## 635                  Starfire         Tamaranean
    ## 636                  Stargirl              Human
    ## 637                    Static             Mutant
    ## 638                     Steel               NULL
    ## 639          Stephanie Powell               NULL
    ## 640               Steppenwolf            New God
    ## 641                     Storm             Mutant
    ## 642              Stormtrooper              Human
    ## 643                   Sunspot             Mutant
    ## 644                  Superboy               NULL
    ## 645            Superboy-Prime         Kryptonian
    ## 646                 Supergirl         Kryptonian
    ## 647                  Superman         Kryptonian
    ## 648               Swamp Thing      God / Eternal
    ## 649                     Swarm             Mutant
    ## 650                     Sylar               NULL
    ## 651                     Synch               NULL
    ## 652                    T-1000            Android
    ## 653                     T-800             Cyborg
    ## 654                     T-850             Cyborg
    ## 655                       T-X             Cyborg
    ## 656                Taskmaster              Human
    ## 657                   Tempest               NULL
    ## 658                    Thanos            Eternal
    ## 659                  The Cape               NULL
    ## 660              The Comedian              Human
    ## 661                     Thing  Human / Radiation
    ## 662                      Thor          Asgardian
    ## 663                 Thor Girl          Asgardian
    ## 664               Thunderbird               NULL
    ## 665            Thunderbird II               NULL
    ## 666           Thunderbird III               NULL
    ## 667             Thunderstrike               NULL
    ## 668                   Thundra               NULL
    ## 669               Tiger Shark              Human
    ## 670                     Tigra               NULL
    ## 671                  Tinkerer               NULL
    ## 672                     Titan               NULL
    ## 673                      Toad             Mutant
    ## 674                     Toxin           Symbiote
    ## 675                     Toxin           Symbiote
    ## 676             Tracy Strauss               NULL
    ## 677                 Trickster              Human
    ## 678                    Trigon      God / Eternal
    ## 679           Triplicate Girl               NULL
    ## 680                    Triton            Inhuman
    ## 681                  Two-Face               NULL
    ## 682                 Ultragirl               NULL
    ## 683                    Ultron            Android
    ## 684               Utgard-Loki        Frost Giant
    ## 685                  Vagabond               NULL
    ## 686              Valerie Hart               NULL
    ## 687                  Valkyrie               NULL
    ## 688                  Vanisher               NULL
    ## 689                    Vegeta             Saiyan
    ## 690                     Venom           Symbiote
    ## 691                  Venom II               NULL
    ## 692                 Venom III           Symbiote
    ## 693                 Venompool           Symbiote
    ## 694                Vertigo II               NULL
    ## 695                      Vibe              Human
    ## 696                Vindicator              Human
    ## 697                Vindicator               NULL
    ## 698                  Violator               NULL
    ## 699               Violet Parr              Human
    ## 700                    Vision            Android
    ## 701                 Vision II               NULL
    ## 702                     Vixen              Human
    ## 703                    Vulcan               NULL
    ## 704                   Vulture              Human
    ## 705                    Walrus              Human
    ## 706               War Machine              Human
    ## 707                   Warbird               NULL
    ## 708                   Warlock               NULL
    ## 709                      Warp               NULL
    ## 710                   Warpath             Mutant
    ## 711                      Wasp              Human
    ## 712                   Watcher               NULL
    ## 713                 Weapon XI               NULL
    ## 714              White Canary              Human
    ## 715               White Queen               NULL
    ## 716                  Wildfire               NULL
    ## 717            Winter Soldier              Human
    ## 718                   Wiz Kid               NULL
    ## 719                 Wolfsbane               NULL
    ## 720                 Wolverine             Mutant
    ## 721               Wonder Girl           Demi-God
    ## 722                Wonder Man               NULL
    ## 723              Wonder Woman             Amazon
    ## 724                    Wondra               NULL
    ## 725            Wyatt Wingfoot               NULL
    ## 726                      X-23     Mutant / Clone
    ## 727                     X-Man               NULL
    ## 728               Yellow Claw               NULL
    ## 729              Yellowjacket              Human
    ## 730           Yellowjacket II              Human
    ## 731                      Ymir        Frost Giant
    ## 732                      Yoda     Yoda's species
    ## 733                   Zatanna              Human
    ## 734                      Zoom               NULL

    ##            publisher gender count(gender)
    ## 1      Marvel Comics Female           111
    ## 2          DC Comics Female            61
    ## 3       NBC - Heroes Female             7
    ## 4  Dark Horse Comics Female             5
    ## 5       Image Comics Female             2
    ## 6               <NA> Female             2
    ## 7               SyFy Female             2
    ## 8      HarperCollins Female             2
    ## 9       George Lucas Female             2
    ## 10       ABC Studios Female             2
    ## 11       Icon Comics Female             1
    ## 12         Star Trek Female             1
    ## 13         Wildstorm Female             1
    ## 14      Team Epic TV Female             1

    ##       publisher alignment    race count(name)
    ## 1     DC Comics      good Ungaran         142
    ## 2 Marvel Comics      good   Human         259
