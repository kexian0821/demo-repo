Stat133\_lab04
================
Kexian Chen
2018/2/15

1.The character delimiter is comma and space
--------------------------------------------

2. There is a row for coloum names
----------------------------------

3.There are no missing values
-----------------------------

4.First column is character,2-7 are double, and the last one is integer.
------------------------------------------------------------------------

``` r
url <- "http://archive.ics.uci.edu/ml/machine-learning-databases/abalone/abalone.data"
abalone <- read.csv(url, sep = ",")

origin <- 'http://archive.ics.uci.edu/ml/machine-learning-databases/abalone/abalone.data'
destination <- 'abalone.data'
download.file(origin, destination)

str(abalone, vec.len = 1)
```

    ## 'data.frame':    4176 obs. of  9 variables:
    ##  $ M      : Factor w/ 3 levels "F","I","M": 3 1 ...
    ##  $ X0.455 : num  0.35 0.53 ...
    ##  $ X0.365 : num  0.265 0.42 ...
    ##  $ X0.095 : num  0.09 0.135 ...
    ##  $ X0.514 : num  0.226 ...
    ##  $ X0.2245: num  0.0995 ...
    ##  $ X0.101 : num  0.0485 ...
    ##  $ X0.15  : num  0.07 0.21 ...
    ##  $ X15    : int  7 9 ...

``` r
column_names <- c(
    'Sex',
    'Length',
    'Diameter',
    'Height',
    'Whole_weight',
    'Shucked_weight',
    'Viscera_weight',
    'Shell_weight',
    'Rings'
)

# vector of data types (for each column)
column_types <- c(
    'character',
    'real',
    'real',
    'real',
    'real',
    'real',
    'real',
    'real',
    'integer'   
)
abalone <- read.csv(
    'abalone.data',
    col.names = column_names,
    colClasses = column_types,
    sep = ","
)

# check its structure again
str(abalone, vec.len = 1)
```

    ## 'data.frame':    4176 obs. of  9 variables:
    ##  $ Sex           : chr  "M" ...
    ##  $ Length        : num  0.35 0.53 ...
    ##  $ Diameter      : num  0.265 0.42 ...
    ##  $ Height        : num  0.09 0.135 ...
    ##  $ Whole_weight  : num  0.226 ...
    ##  $ Shucked_weight: num  0.0995 ...
    ##  $ Viscera_weight: num  0.0485 ...
    ##  $ Shell_weight  : num  0.07 0.21 ...
    ##  $ Rings         : int  7 9 ...

Pittsburgh Bridges Data Set 1.There are 13 column names names 2.Field separator is blank spaces 3.There are missing values in the data set.

``` r
origin <-'http://archive.ics.uci.edu/ml/machine-learning-databases/bridges/bridges.data.version1'
destination <- 'bridges.data'
download.file(origin, destination)

col_names2 <- c(
  'Identifier',
  'RIVER',
  'LOCATION',
  'ERECTED',
  'PURPOSE',
  'LENGTH',
  'LANES',
  'CLEAR-G',
  'T-OR-D',
  'MATERIAL',
  'SPAN',
  'REL-L',
  'TYPE'
)

col_types2 <- c(
  'character',
  'character',
  'real',
  'real',
  'character',
  'character',
  'real',
  'character',
  'character',
  'character',
  'character',
  'character'
)

bridges1 <- read.table('bridges.data', col.names = col_names2, colClasses = col_types2,sep = ",", na.strings = "?")
bridges2 <- read.csv('bridges.data', col.names = col_names2,colClasses = col_types2, sep = ",", na.strings = "?")

str(bridges1, vec.len = 1)
```

    ## 'data.frame':    108 obs. of  13 variables:
    ##  $ Identifier: chr  "E1" ...
    ##  $ RIVER     : chr  "M" ...
    ##  $ LOCATION  : num  3 25 ...
    ##  $ ERECTED   : num  1818 ...
    ##  $ PURPOSE   : chr  "HIGHWAY" ...
    ##  $ LENGTH    : chr  NA ...
    ##  $ LANES     : num  2 2 ...
    ##  $ CLEAR.G   : chr  "N" ...
    ##  $ T.OR.D    : chr  "THROUGH" ...
    ##  $ MATERIAL  : chr  "WOOD" ...
    ##  $ SPAN      : chr  "SHORT" ...
    ##  $ REL.L     : chr  "S" ...
    ##  $ TYPE      : chr  "WOOD" ...

``` r
summary(bridges1)
```

    ##   Identifier           RIVER              LOCATION        ERECTED    
    ##  Length:108         Length:108         Min.   : 1.00   Min.   :1818  
    ##  Class :character   Class :character   1st Qu.:15.50   1st Qu.:1884  
    ##  Mode  :character   Mode  :character   Median :27.00   Median :1903  
    ##                                        Mean   :25.98   Mean   :1905  
    ##                                        3rd Qu.:37.50   3rd Qu.:1928  
    ##                                        Max.   :52.00   Max.   :1986  
    ##                                        NA's   :1                     
    ##    PURPOSE             LENGTH              LANES        CLEAR.G         
    ##  Length:108         Length:108         Min.   :1.00   Length:108        
    ##  Class :character   Class :character   1st Qu.:2.00   Class :character  
    ##  Mode  :character   Mode  :character   Median :2.00   Mode  :character  
    ##                                        Mean   :2.63                     
    ##                                        3rd Qu.:4.00                     
    ##                                        Max.   :6.00                     
    ##                                        NA's   :16                       
    ##     T.OR.D            MATERIAL             SPAN          
    ##  Length:108         Length:108         Length:108        
    ##  Class :character   Class :character   Class :character  
    ##  Mode  :character   Mode  :character   Mode  :character  
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##     REL.L               TYPE          
    ##  Length:108         Length:108        
    ##  Class :character   Class :character  
    ##  Mode  :character   Mode  :character  
    ##                                       
    ##                                       
    ##                                       
    ## 

``` r
head(bridges1)
```

    ##   Identifier RIVER LOCATION ERECTED  PURPOSE LENGTH LANES CLEAR.G  T.OR.D
    ## 1         E1     M        3    1818  HIGHWAY   <NA>     2       N THROUGH
    ## 2         E2     A       25    1819  HIGHWAY   1037     2       N THROUGH
    ## 3         E3     A       39    1829 AQUEDUCT   <NA>     1       N THROUGH
    ## 4         E5     A       29    1837  HIGHWAY   1000     2       N THROUGH
    ## 5         E6     M       23    1838  HIGHWAY   <NA>     2       N THROUGH
    ## 6         E7     A       27    1840  HIGHWAY    990     2       N THROUGH
    ##   MATERIAL   SPAN REL.L TYPE
    ## 1     WOOD  SHORT     S WOOD
    ## 2     WOOD  SHORT     S WOOD
    ## 3     WOOD   <NA>     S WOOD
    ## 4     WOOD  SHORT     S WOOD
    ## 5     WOOD   <NA>     S WOOD
    ## 6     WOOD MEDIUM     S WOOD

``` r
tail(bridges1)
```

    ##     Identifier RIVER LOCATION ERECTED PURPOSE LENGTH LANES CLEAR.G  T.OR.D
    ## 103        E85     M        9    1962 HIGHWAY   2213     4       G    DECK
    ## 104        E84     A       24    1969 HIGHWAY    870     6       G THROUGH
    ## 105        E91     O       44    1975 HIGHWAY   3756     6       G THROUGH
    ## 106        E90     M        7    1978 HIGHWAY    950     6       G THROUGH
    ## 107       E100     O       43    1982 HIGHWAY   <NA>    NA       G    <NA>
    ## 108       E109     A       28    1986 HIGHWAY   <NA>    NA       G    <NA>
    ##     MATERIAL   SPAN REL.L   TYPE
    ## 103    STEEL   LONG     F CONT-T
    ## 104    STEEL MEDIUM     F   ARCH
    ## 105    STEEL   LONG     F   ARCH
    ## 106    STEEL   LONG     F   ARCH
    ## 107     <NA>   <NA>     F   <NA>
    ## 108     <NA>   <NA>     F   <NA>

``` r
dim(bridges1)
```

    ## [1] 108  13

``` r
names(bridges1)
```

    ##  [1] "Identifier" "RIVER"      "LOCATION"   "ERECTED"    "PURPOSE"   
    ##  [6] "LENGTH"     "LANES"      "CLEAR.G"    "T.OR.D"     "MATERIAL"  
    ## [11] "SPAN"       "REL.L"      "TYPE"

``` r
colnames(bridges1)
```

    ##  [1] "Identifier" "RIVER"      "LOCATION"   "ERECTED"    "PURPOSE"   
    ##  [6] "LENGTH"     "LANES"      "CLEAR.G"    "T.OR.D"     "MATERIAL"  
    ## [11] "SPAN"       "REL.L"      "TYPE"

``` r
nrow(bridges1)
```

    ## [1] 108

``` r
ncol(bridges1)
```

    ## [1] 13

NBA Player Data
---------------

``` r
origin <-'https://github.com/ucb-stat133/stat133-fall-2017/raw/master/data/nba2017-players.csv'
destination <- 'nba2017-players.csv'
download.file(origin, destination)

dat<-read.csv('nba2017-players.csv', stringsAsFactors = FALSE)

tail(dat)
```

    ##              player team position height weight age experience
    ## 436 Leandro Barbosa  PHO       SG     75    194  34         13
    ## 437 Marquese Chriss  PHO       PF     82    233  19          0
    ## 438    Ronnie Price  PHO       PG     74    190  33         11
    ## 439     T.J. Warren  PHO       SF     80    230  23          2
    ## 440      Tyler Ulis  PHO       PG     70    150  21          0
    ## 441  Tyson Chandler  PHO        C     85    240  34         15
    ##                             college   salary games minutes points points3
    ## 436                                  4000000    67     963    419      35
    ## 437        University of Washington  2941440    82    1743    753      72
    ## 438       Utah Valley State College   282595    14     134     14       3
    ## 439 North Carolina State University  2128920    66    2048    951      26
    ## 440          University of Kentucky   918369    61    1123    444      21
    ## 441                                 12415000    47    1298    397       0
    ##     points2 points1
    ## 436     137      40
    ## 437     212     113
    ## 438       1       3
    ## 439     377     119
    ## 440     163      55
    ## 441     153      91

``` r
dat$player[dat$height<70]
```

    ## [1] "Isaiah Thomas" "Kay Felder"

``` r
Sal<- dat$position == 'C'

dat$player[Sal]
```

    ##  [1] "Al Horford"           "Kelly Olynyk"         "Tyler Zeller"        
    ##  [4] "Channing Frye"        "Edy Tavares"          "Tristan Thompson"    
    ##  [7] "Jakob Poeltl"         "Jonas Valanciunas"    "Lucas Nogueira"      
    ## [10] "Daniel Ochefu"        "Ian Mahinmi"          "Jason Smith"         
    ## [13] "Marcin Gortat"        "Dwight Howard"        "Mike Muscala"        
    ## [16] "Greg Monroe"          "John Henson"          "Thon Maker"          
    ## [19] "Al Jefferson"         "Myles Turner"         "Cristiano Felicio"   
    ## [22] "Joffrey Lauvergne"    "Robin Lopez"          "Hassan Whiteside"    
    ## [25] "Udonis Haslem"        "Willie Reed"          "Andre Drummond"      
    ## [28] "Aron Baynes"          "Boban Marjanovic"     "Frank Kaminsky"      
    ## [31] "Miles Plumlee"        "Joakim Noah"          "Kyle O'Quinn"        
    ## [34] "Marshall Plumlee"     "Willy Hernangomez"    "Bismack Biyombo"     
    ## [37] "Nikola Vucevic"       "Stephen Zimmerman"    "Jahlil Okafor"       
    ## [40] "Joel Embiid"          "Richaun Holmes"       "Shawn Long"          
    ## [43] "Tiago Splitter"       "Brook Lopez"          "Justin Hamilton"     
    ## [46] "Damian Jones"         "David West"           "JaVale McGee"        
    ## [49] "Kevon Looney"         "Zaza Pachulia"        "Dewayne Dedmon"      
    ## [52] "Joel Anthony"         "Pau Gasol"            "Chinanu Onuaku"      
    ## [55] "Clint Capela"         "Montrezl Harrell"     "DeAndre Jordan"      
    ## [58] "Diamond Stone"        "Marreese Speights"    "Jeff Withey"         
    ## [61] "Rudy Gobert"          "Enes Kanter"          "Steven Adams"        
    ## [64] "Deyonta Davis"        "Marc Gasol"           "Jusuf Nurkic"        
    ## [67] "Mason Plumlee"        "Nikola Jokic"         "Roy Hibbert"         
    ## [70] "Alexis Ajinca"        "Anthony Davis"        "DeMarcus Cousins"    
    ## [73] "Omer Asik"            "A.J. Hammons"         "Dwight Powell"       
    ## [76] "Nerlens Noel"         "Salah Mejri"          "Georgios Papagiannis"
    ## [79] "Kosta Koufos"         "Willie Cauley-Stein"  "Cole Aldrich"        
    ## [82] "Jordan Hill"          "Karl-Anthony Towns"   "Ivica Zubac"         
    ## [85] "Tarik Black"          "Timofey Mozgov"       "Alan Williams"       
    ## [88] "Alex Len"             "Tyson Chandler"

``` r
dat$salary[Sal]
```

    ##  [1] 26540100  3094014  8000000  7806971     5145 15330435  2703960
    ##  [8] 14382022  1921320   543471 15944154  5000000 12000000 23180275
    ## [15]  1015696 17100000 12517606  2568600 10230179  2463840   874636
    ## [22]  1709720 13219250 22116750  4000000  1015696 22116750  6500000
    ## [29]  7000000  2730000 12500000 17000000  3900000   543471  1375000
    ## [36] 17000000 11750000   950000  4788840  4826160  1025831    89513
    ## [43]  8550000 21165675  3000000  1171560  1551659  1403611  1182840
    ## [50]  2898000  2898000   165952 15500000   543471  1296240  1000000
    ## [57] 21165675   543471  1403611  1015696  2121288 17145838  3140517
    ## [64]  1369229 21165675  1921320  2328530  1358500  5000000  4600000
    ## [71] 22116750 16957900  9904494   650000  8375000  4384490   874636
    ## [78]  2202240  8046500  3551160  7643979  3911380  5960160  1034956
    ## [85]  6191000 16000000   874636  4823621 12415000

``` r
Durant<-data.frame(name = "Kevin Durant", team = "GSW",position = "SF",Height= 81,Weight= 240,Age= 28,Exp= 9,College= "University of Texas at Austin",Salary= 26540100,games=62,minutues=2070,points=1555,points3=117,points2=434,points1=336)
Durant
```

    ##           name team position Height Weight Age Exp
    ## 1 Kevin Durant  GSW       SF     81    240  28   9
    ##                         College   Salary games minutues points points3
    ## 1 University of Texas at Austin 26540100    62     2070   1555     117
    ##   points2 points1
    ## 1     434     336

``` r
UCLAC<-dat$college == 'University of California, Los Angeles'
UCLA<-data.frame(dat$player[UCLAC],dat$team[UCLAC],dat$position[UCLAC],dat$height[UCLAC],dat$weight[UCLAC],dat$age[UCLAC],dat$experience[UCLAC],dat$college[UCLAC],dat$salary[UCLAC],dat$games[UCLAC],dat$minutes[UCLAC],dat$points[UCLAC])
UCLA
```

    ##    dat.player.UCLAC. dat.team.UCLAC. dat.position.UCLAC. dat.height.UCLAC.
    ## 1         Kevin Love             CLE                  PF                82
    ## 2      Norman Powell             TOR                  SG                76
    ## 3       Kevon Looney             GSW                   C                81
    ## 4        Matt Barnes             GSW                  SF                79
    ## 5      Kyle Anderson             SAS                  SG                81
    ## 6       Trevor Ariza             HOU                  SF                80
    ## 7   Luc Mbah a Moute             LAC                  SF                80
    ## 8  Russell Westbrook             OKC                  PG                75
    ## 9       Jrue Holiday             NOP                  PG                76
    ## 10     Arron Afflalo             SAC                  SG                77
    ## 11   Darren Collison             SAC                  PG                72
    ## 12  Shabazz Muhammad             MIN                  SF                78
    ## 13       Zach LaVine             MIN                  SG                77
    ##    dat.weight.UCLAC. dat.age.UCLAC. dat.experience.UCLAC.
    ## 1                251             28                     8
    ## 2                215             23                     1
    ## 3                220             20                     1
    ## 4                226             36                    13
    ## 5                230             23                     2
    ## 6                215             31                    12
    ## 7                230             30                     8
    ## 8                200             28                     8
    ## 9                205             26                     7
    ## 10               210             31                     9
    ## 11               175             29                     7
    ## 12               223             24                     3
    ## 13               189             21                     2
    ##                       dat.college.UCLAC. dat.salary.UCLAC.
    ## 1  University of California, Los Angeles          21165675
    ## 2  University of California, Los Angeles            874636
    ## 3  University of California, Los Angeles           1182840
    ## 4  University of California, Los Angeles            383351
    ## 5  University of California, Los Angeles           1192080
    ## 6  University of California, Los Angeles           7806971
    ## 7  University of California, Los Angeles           2203000
    ## 8  University of California, Los Angeles          26540100
    ## 9  University of California, Los Angeles          11286518
    ## 10 University of California, Los Angeles          12500000
    ## 11 University of California, Los Angeles           5229454
    ## 12 University of California, Los Angeles           3046299
    ## 13 University of California, Los Angeles           2240880
    ##    dat.games.UCLAC. dat.minutes.UCLAC. dat.points.UCLAC.
    ## 1                60               1885              1142
    ## 2                76               1368               636
    ## 3                53                447               135
    ## 4                20                410               114
    ## 5                72               1020               246
    ## 6                80               2773               936
    ## 7                80               1787               484
    ## 8                81               2802              2558
    ## 9                67               2190              1029
    ## 10               61               1580               515
    ## 11               68               2063               900
    ## 12               78               1516               772
    ## 13               47               1749               889

``` r
rookiess<-dat$experience == '0'
rookies<-data.frame(dat$player[rookiess])
rookies
```

    ##       dat.player.rookiess.
    ## 1        Demetrius Jackson
    ## 2             Jaylen Brown
    ## 3               Kay Felder
    ## 4            Fred VanVleet
    ## 5             Jakob Poeltl
    ## 6            Pascal Siakam
    ## 7            Daniel Ochefu
    ## 8        Sheldon McClellan
    ## 9         Tomas Satoransky
    ## 10         DeAndre' Bembry
    ## 11         Malcolm Delaney
    ## 12         Malcolm Brogdon
    ## 13              Thon Maker
    ## 14           Georges Niang
    ## 15        Denzel Valentine
    ## 16             Paul Zipser
    ## 17             Okaro White
    ## 18         Rodney McGruder
    ## 19          Henry Ellenson
    ## 20         Michael Gbinije
    ## 21          Treveon Graham
    ## 22          Chasson Randle
    ## 23        Marshall Plumlee
    ## 24           Maurice Ndour
    ## 25    Mindaugas Kuzminskas
    ## 26               Ron Baker
    ## 27       Willy Hernangomez
    ## 28     Marcus Georges-Hunt
    ## 29         Patricio Garino
    ## 30       Stephen Zimmerman
    ## 31          Alex Poythress
    ## 32             Dario Saric
    ## 33             Joel Embiid
    ## 34              Shawn Long
    ## 35 Timothe Luwawu-Cabarrot
    ## 36            Caris LeVert
    ## 37        Isaiah Whitehead
    ## 38            Damian Jones
    ## 39           Patrick McCaw
    ## 40             Bryn Forbes
    ## 41           Davis Bertans
    ## 42         Dejounte Murray
    ## 43          Chinanu Onuaku
    ## 44           Isaiah Taylor
    ## 45            Kyle Wiltjer
    ## 46           Troy Williams
    ## 47           Brice Johnson
    ## 48           Diamond Stone
    ## 49           Joel Bolomboy
    ## 50            Alex Abrines
    ## 51        Domantas Sabonis
    ## 52          Semaj Christon
    ## 53         Andrew Harrison
    ## 54           Deyonta Davis
    ## 55            Wade Baldwin
    ## 56            Wayne Selden
    ## 57             Jake Layman
    ## 58          Tim Quarterman
    ## 59            Jamal Murray
    ## 60        Juan Hernangomez
    ## 61           Malik Beasley
    ## 62           Cheick Diallo
    ## 63              Quinn Cook
    ## 64            A.J. Hammons
    ## 65     Dorian Finney-Smith
    ## 66           Jarrod Uthoff
    ## 67        Nicolas Brussino
    ## 68            Yogi Ferrell
    ## 69             Buddy Hield
    ## 70    Georgios Papagiannis
    ## 71      Malachi Richardson
    ## 72         Skal Labissiere
    ## 73               Kris Dunn
    ## 74          Brandon Ingram
    ## 75             David Nwaba
    ## 76             Ivica Zubac
    ## 77           Derrick Jones
    ## 78           Dragan Bender
    ## 79         Marquese Chriss
    ## 80              Tyler Ulis

``` r
roo<-dat$experience =='0' & dat$position =='C'
rookie_center<-data.frame(dat$player[roo])
rookie_center
```

    ##         dat.player.roo.
    ## 1          Jakob Poeltl
    ## 2         Daniel Ochefu
    ## 3            Thon Maker
    ## 4      Marshall Plumlee
    ## 5     Willy Hernangomez
    ## 6     Stephen Zimmerman
    ## 7           Joel Embiid
    ## 8            Shawn Long
    ## 9          Damian Jones
    ## 10       Chinanu Onuaku
    ## 11        Diamond Stone
    ## 12        Deyonta Davis
    ## 13         A.J. Hammons
    ## 14 Georgios Papagiannis
    ## 15          Ivica Zubac

``` r
top_player<-data.frame(dat$player[dat$games>50 & dat$minutes>100])
top_player
```

    ##     dat.player.dat.games...50...dat.minutes...100.
    ## 1                                       Al Horford
    ## 2                                     Amir Johnson
    ## 3                                    Avery Bradley
    ## 4                                    Isaiah Thomas
    ## 5                                      Jae Crowder
    ## 6                                     Jaylen Brown
    ## 7                                    Jonas Jerebko
    ## 8                                     Kelly Olynyk
    ## 9                                     Marcus Smart
    ## 10                                    Terry Rozier
    ## 11                                    Tyler Zeller
    ## 12                                   Channing Frye
    ## 13                                   Iman Shumpert
    ## 14                                      Kevin Love
    ## 15                                    Kyrie Irving
    ## 16                                    LeBron James
    ## 17                               Richard Jefferson
    ## 18                                Tristan Thompson
    ## 19                                     Cory Joseph
    ## 20                                   DeMar DeRozan
    ## 21                                 DeMarre Carroll
    ## 22                                    Jakob Poeltl
    ## 23                               Jonas Valanciunas
    ## 24                                      Kyle Lowry
    ## 25                                  Lucas Nogueira
    ## 26                                   Norman Powell
    ## 27                                   Pascal Siakam
    ## 28                               Patrick Patterson
    ## 29                                    Bradley Beal
    ## 30                                     Jason Smith
    ## 31                                       John Wall
    ## 32                                   Marcin Gortat
    ## 33                                 Markieff Morris
    ## 34                                     Otto Porter
    ## 35                                Tomas Satoransky
    ## 36                                      Trey Burke
    ## 37                                 Dennis Schroder
    ## 38                                   Dwight Howard
    ## 39                                   Kent Bazemore
    ## 40                                  Kris Humphries
    ## 41                                 Malcolm Delaney
    ## 42                                    Mike Muscala
    ## 43                                    Paul Millsap
    ## 44                                 Thabo Sefolosha
    ## 45                                    Tim Hardaway
    ## 46                           Giannis Antetokounmpo
    ## 47                                     Greg Monroe
    ## 48                                   Jabari Parker
    ## 49                                     Jason Terry
    ## 50                                     John Henson
    ## 51                                 Malcolm Brogdon
    ## 52                             Matthew Dellavedova
    ## 53                                 Michael Beasley
    ## 54                                 Mirza Teletovic
    ## 55                                      Thon Maker
    ## 56                                      Tony Snell
    ## 57                                    Aaron Brooks
    ## 58                                    Al Jefferson
    ## 59                                      C.J. Miles
    ## 60                                     Jeff Teague
    ## 61                                     Lavoy Allen
    ## 62                                     Monta Ellis
    ## 63                                    Myles Turner
    ## 64                                     Paul George
    ## 65                                  Thaddeus Young
    ## 66                                    Bobby Portis
    ## 67                               Cristiano Felicio
    ## 68                                Denzel Valentine
    ## 69                                     Dwyane Wade
    ## 70                                    Jerian Grant
    ## 71                                    Jimmy Butler
    ## 72                                  Nikola Mirotic
    ## 73                                     Rajon Rondo
    ## 74                                     Robin Lopez
    ## 75                                    Goran Dragic
    ## 76                                Hassan Whiteside
    ## 77                                   James Johnson
    ## 78                                 Josh Richardson
    ## 79                                    Luke Babbitt
    ## 80                                 Rodney McGruder
    ## 81                                   Tyler Johnson
    ## 82                                 Wayne Ellington
    ## 83                                     Willie Reed
    ## 84                                  Andre Drummond
    ## 85                                     Aron Baynes
    ## 86                                       Ish Smith
    ## 87                                       Jon Leuer
    ## 88                        Kentavious Caldwell-Pope
    ## 89                                   Marcus Morris
    ## 90                                  Reggie Jackson
    ## 91                                 Stanley Johnson
    ## 92                                   Tobias Harris
    ## 93                                     Cody Zeller
    ## 94                                  Frank Kaminsky
    ## 95                                     Jeremy Lamb
    ## 96                                    Kemba Walker
    ## 97                                 Marco Belinelli
    ## 98                                 Marvin Williams
    ## 99                          Michael Kidd-Gilchrist
    ## 100                                  Nicolas Batum
    ## 101                                Carmelo Anthony
    ## 102                                   Courtney Lee
    ## 103                                   Derrick Rose
    ## 104                                 Justin Holiday
    ## 105                             Kristaps Porzingis
    ## 106                                   Kyle O'Quinn
    ## 107                           Mindaugas Kuzminskas
    ## 108                                      Ron Baker
    ## 109                              Willy Hernangomez
    ## 110                                   Aaron Gordon
    ## 111                                Bismack Biyombo
    ## 112                                    C.J. Watson
    ## 113                                  D.J. Augustin
    ## 114                                  Elfrid Payton
    ## 115                                  Evan Fournier
    ## 116                                     Jeff Green
    ## 117                                  Mario Hezonja
    ## 118                                 Nikola Vucevic
    ## 119                                    Dario Saric
    ## 120                               Gerald Henderson
    ## 121                                   Nik Stauskas
    ## 122                                 Richaun Holmes
    ## 123                               Robert Covington
    ## 124                               Sergio Rodriguez
    ## 125                                 T.J. McConnell
    ## 126                        Timothe Luwawu-Cabarrot
    ## 127                                    Brook Lopez
    ## 128                                   Caris LeVert
    ## 129                               Isaiah Whitehead
    ## 130                                     Joe Harris
    ## 131                                Justin Hamilton
    ## 132                                     Randy Foye
    ## 133                        Rondae Hollis-Jefferson
    ## 134                                Sean Kilpatrick
    ## 135                              Spencer Dinwiddie
    ## 136                                  Trevor Booker
    ## 137                                 Andre Iguodala
    ## 138                                     David West
    ## 139                                 Draymond Green
    ## 140                                      Ian Clark
    ## 141                           James Michael McAdoo
    ## 142                                   JaVale McGee
    ## 143                                   Kevin Durant
    ## 144                                   Kevon Looney
    ## 145                                  Klay Thompson
    ## 146                                  Patrick McCaw
    ## 147                               Shaun Livingston
    ## 148                                  Stephen Curry
    ## 149                                  Zaza Pachulia
    ## 150                                    Danny Green
    ## 151                                      David Lee
    ## 152                                  Davis Bertans
    ## 153                                 Dewayne Dedmon
    ## 154                               Jonathon Simmons
    ## 155                                  Kawhi Leonard
    ## 156                                  Kyle Anderson
    ## 157                              LaMarcus Aldridge
    ## 158                                  Manu Ginobili
    ## 159                                    Patty Mills
    ## 160                                      Pau Gasol
    ## 161                                    Tony Parker
    ## 162                                   Clint Capela
    ## 163                                    Eric Gordon
    ## 164                                   James Harden
    ## 165                               Montrezl Harrell
    ## 166                               Patrick Beverley
    ## 167                                  Ryan Anderson
    ## 168                                     Sam Dekker
    ## 169                                   Trevor Ariza
    ## 170                                  Austin Rivers
    ## 171                                  Blake Griffin
    ## 172                                   Brandon Bass
    ## 173                                     Chris Paul
    ## 174                                 DeAndre Jordan
    ## 175                                    J.J. Redick
    ## 176                                 Jamal Crawford
    ## 177                               Luc Mbah a Moute
    ## 178                              Marreese Speights
    ## 179                                 Raymond Felton
    ## 180                                 Wesley Johnson
    ## 181                                     Boris Diaw
    ## 182                                     Dante Exum
    ## 183                                 Gordon Hayward
    ## 184                                    Jeff Withey
    ## 185                                     Joe Ingles
    ## 186                                    Joe Johnson
    ## 187                                    Rodney Hood
    ## 188                                    Rudy Gobert
    ## 189                                   Shelvin Mack
    ## 190                                     Trey Lyles
    ## 191                                   Alex Abrines
    ## 192                                 Andre Roberson
    ## 193                               Domantas Sabonis
    ## 194                                    Enes Kanter
    ## 195                                   Jerami Grant
    ## 196                              Russell Westbrook
    ## 197                                 Semaj Christon
    ## 198                                   Steven Adams
    ## 199                                 Victor Oladipo
    ## 200                                Andrew Harrison
    ## 201                                    James Ennis
    ## 202                                 JaMychal Green
    ## 203                                     Marc Gasol
    ## 204                                    Mike Conley
    ## 205                                     Tony Allen
    ## 206                                   Troy Daniels
    ## 207                                   Vince Carter
    ## 208                                  Zach Randolph
    ## 209                                Al-Farouq Aminu
    ## 210                                   Allen Crabbe
    ## 211                                  C.J. McCollum
    ## 212                                 Damian Lillard
    ## 213                                    Evan Turner
    ## 214                               Maurice Harkless
    ## 215                                 Meyers Leonard
    ## 216                                    Noah Vonleh
    ## 217                                 Shabazz Napier
    ## 218                               Danilo Gallinari
    ## 219                                Emmanuel Mudiay
    ## 220                                    Gary Harris
    ## 221                                   Jamal Murray
    ## 222                                  Jameer Nelson
    ## 223                               Juan Hernangomez
    ## 224                                 Kenneth Faried
    ## 225                                   Nikola Jokic
    ## 226                                    Will Barton
    ## 227                                Wilson Chandler
    ## 228                                  Anthony Davis
    ## 229                               Dante Cunningham
    ## 230                                  E'Twaun Moore
    ## 231                                   Jrue Holiday
    ## 232                                   Solomon Hill
    ## 233                                    Tim Frazier
    ## 234                                   Devin Harris
    ## 235                                  Dirk Nowitzki
    ## 236                            Dorian Finney-Smith
    ## 237                                  Dwight Powell
    ## 238                                Harrison Barnes
    ## 239                               Nicolas Brussino
    ## 240                                    Salah Mejri
    ## 241                                     Seth Curry
    ## 242                                Wesley Matthews
    ## 243                               Anthony Tolliver
    ## 244                                  Arron Afflalo
    ## 245                                   Ben McLemore
    ## 246                                Darren Collison
    ## 247                                 Garrett Temple
    ## 248                                   Kosta Koufos
    ## 249                                      Ty Lawson
    ## 250                            Willie Cauley-Stein
    ## 251                                 Andrew Wiggins
    ## 252                                   Cole Aldrich
    ## 253                                   Gorgui Dieng
    ## 254                             Karl-Anthony Towns
    ## 255                                      Kris Dunn
    ## 256                                Nemanja Bjelica
    ## 257                                    Ricky Rubio
    ## 258                               Shabazz Muhammad
    ## 259                                     Tyus Jones
    ## 260                                 Brandon Ingram
    ## 261                               D'Angelo Russell
    ## 262                                Jordan Clarkson
    ## 263                                  Julius Randle
    ## 264                                Larry Nance Jr.
    ## 265                                      Luol Deng
    ## 266                                     Nick Young
    ## 267                                    Tarik Black
    ## 268                                 Timofey Mozgov
    ## 269                                       Alex Len
    ## 270                                 Brandon Knight
    ## 271                                   Devin Booker
    ## 272                                   Eric Bledsoe
    ## 273                                   Jared Dudley
    ## 274                                Leandro Barbosa
    ## 275                                Marquese Chriss
    ## 276                                    T.J. Warren
    ## 277                                     Tyler Ulis

``` r
##Max and Min of all players
max(dat$height,na.rm = TRUE)
```

    ## [1] 87

``` r
dat$player[which.max(dat$height)]
```

    ## [1] "Edy Tavares"

``` r
min(dat$height,na.rm= TRUE)
```

    ## [1] 69

``` r
dat$player[which.min(dat$height)]
```

    ## [1] "Isaiah Thomas"

``` r
mean(dat$height)##Average of height
```

    ## [1] 79.1542

``` r
table(dat$team) ##how many differnt teams
```

    ## 
    ## ATL BOS BRK CHI CHO CLE DAL DEN DET GSW HOU IND LAC LAL MEM MIA MIL MIN 
    ##  14  15  15  15  15  15  15  15  15  15  14  14  15  15  15  14  14  14 
    ## NOP NYK OKC ORL PHI PHO POR SAC SAS TOR UTA WAS 
    ##  14  15  15  15  15  15  14  15  15  15  15  14

``` r
dat$player[which.max(dat$age)] ##oldest player
```

    ## [1] "Vince Carter"

``` r
median(dat$salary)##meadian salary
```

    ## [1] 3500000

``` r
Exp9<-dat$experience>9
median(dat$salary[Exp9]) ##median salary with 10 or more yrs experience
```

    ## [1] 5644034

``` r
SGPG<- dat$position =='SG' | dat$position=='PG'
median(dat$salary[SGPG]) ##meadian salary of position SG and PG
```

    ## [1] 3230690

``` r
PGS<- dat$position =='PG' & dat$age >28 & dat$height<75
median(dat$salary[PGS]) ##median salary of Power Forwards (PF), 29 years or older, and 74 inches tall or less
```

    ## [1] 4770263

``` r
Or4less<- dat$points<5
table(Or4less) ##How many players scored 4 points or less? 7
```

    ## Or4less
    ## FALSE  TRUE 
    ##   434     7

``` r
dat$player[Or4less] ##Who are they
```

    ## [1] "Chris McCullough" "Michael Gbinije"  "Patricio Garino" 
    ## [4] "Isaiah Taylor"    "Brice Johnson"    "Roy Hibbert"     
    ## [7] "Elijah Millsap"

``` r
dat$player[dat$points==0] ##Who is the player with 0 points
```

    ## [1] "Patricio Garino"

``` r
table(dat$college=="University of California, Berkeley") ##No players are from "University of California, Berkeley"
```

    ## 
    ## FALSE 
    ##   441

``` r
table(dat$college=="University of Notre Dame")
```

    ## 
    ## FALSE  TRUE 
    ##   438     3

``` r
dat$player[dat$college=="University of Notre Dame"]##Are there any players from "University of Notre Dame"? If so how many and who are they?
```

    ## [1] "Demetrius Jackson" "Jerian Grant"      "Pat Connaughton"

``` r
table(dat$weight>260)
```

    ## 
    ## FALSE  TRUE 
    ##   420    21

``` r
dat$player[dat$weight>260] ##Are there any players with weight greater than 260 pounds? If so how many and who are they?
```

    ##  [1] "Jonas Valanciunas" "Dwight Howard"     "Greg Monroe"      
    ##  [4] "Al Jefferson"      "Kevin Seraphin"    "Cristiano Felicio"
    ##  [7] "Hassan Whiteside"  "Andre Drummond"    "Boban Marjanovic" 
    ## [10] "Jahlil Okafor"     "Brook Lopez"       "JaVale McGee"     
    ## [13] "Zaza Pachulia"     "DeAndre Jordan"    "Derrick Favors"   
    ## [16] "Jusuf Nurkic"      "Roy Hibbert"       "DeMarcus Cousins" 
    ## [19] "Kosta Koufos"      "Ivica Zubac"       "Timofey Mozgov"

``` r
table(dat$college=="") ##How many players did not attend a college in the US?
```

    ## 
    ## FALSE  TRUE 
    ##   356    85

``` r
PPM = dat$points / dat$minutes
max(PPM) ##Who is the player with the maximum rate of points per minute?
```

    ## [1] 0.9129193

``` r
PPM3 = dat$points3/dat$minutes
dat$player[which.max(PPM3)] ##Who is the player with the maximum rate of three-points per minute?
```

    ## [1] "Stephen Curry"

``` r
PPM2 = dat$points2/dat$minutes
dat$player[which.max(PPM2)] ##Who is the player with the maximum rate of two-points per minute?
```

    ## [1] "JaVale McGee"

``` r
PPM1 = dat$points1/dat$minutes
dat$player[which.max(PPM1)] ##Who is the player with the maximum rate of two-points per minute?
```

    ## [1] "Russell Westbrook"

``` r
gsw1 = dat$team == 'GSW'
##Create a data frame gsw with the name, height, weight of Golden State Warriors (GSW)
gsw<- data.frame(dat$player[gsw1],dat$height[gsw1],dat$weight[gsw1])

##Display the data in gsw sorted by height in increasing order
gsw<- c(dat$player[gsw1],dat$height[gsw1],dat$weight[gsw1])
data.frame(gsw[order(dat$height[gsw1])],sort(dat$height[gsw1]))
```

    ##    gsw.order.dat.height.gsw1... sort.dat.height.gsw1..
    ## 1                     Ian Clark                     75
    ## 2                 Stephen Curry                     75
    ## 3                Andre Iguodala                     78
    ## 4                Draymond Green                     79
    ## 5                 Klay Thompson                     79
    ## 6                   Matt Barnes                     79
    ## 7                 Patrick McCaw                     79
    ## 8              Shaun Livingston                     79
    ## 9                    David West                     81
    ## 10         James Michael McAdoo                     81
    ## 11                 Kevin Durant                     81
    ## 12                 Kevon Looney                     81
    ## 13                Zaza Pachulia                     83
    ## 14                 Damian Jones                     84
    ## 15                 JaVale McGee                     84

``` r
##Display the data in gsw by weight in decreasing order
data.frame(gsw[order(dat$weight[gsw1],decreasing = TRUE)],sort(dat$weight[gsw1],decreasing = TRUE))
```

    ##    gsw.order.dat.weight.gsw1...decreasing...TRUE..
    ## 1                                     JaVale McGee
    ## 2                                    Zaza Pachulia
    ## 3                                       David West
    ## 4                                     Damian Jones
    ## 5                                     Kevin Durant
    ## 6                                   Draymond Green
    ## 7                             James Michael McAdoo
    ## 8                                      Matt Barnes
    ## 9                                     Kevon Looney
    ## 10                                  Andre Iguodala
    ## 11                                   Klay Thompson
    ## 12                                Shaun Livingston
    ## 13                                   Stephen Curry
    ## 14                                   Patrick McCaw
    ## 15                                       Ian Clark
    ##    sort.dat.weight.gsw1...decreasing...TRUE.
    ## 1                                        270
    ## 2                                        270
    ## 3                                        250
    ## 4                                        245
    ## 5                                        240
    ## 6                                        230
    ## 7                                        230
    ## 8                                        226
    ## 9                                        220
    ## 10                                       215
    ## 11                                       215
    ## 12                                       192
    ## 13                                       190
    ## 14                                       185
    ## 15                                       175

``` r
##Display the player name, team, and salary, of the top 5 highest-paid players
data.frame(head(dat$player[order(dat$salary,decreasing = TRUE)]),head(dat$salary[order(dat$salary,decreasing = TRUE)]),head(dat$team[order(dat$salary,decreasing = TRUE)]))
```

    ##   head.dat.player.order.dat.salary..decreasing...TRUE...
    ## 1                                           LeBron James
    ## 2                                             Al Horford
    ## 3                                          DeMar DeRozan
    ## 4                                           Kevin Durant
    ## 5                                           James Harden
    ## 6                                      Russell Westbrook
    ##   head.dat.salary.order.dat.salary..decreasing...TRUE...
    ## 1                                               30963450
    ## 2                                               26540100
    ## 3                                               26540100
    ## 4                                               26540100
    ## 5                                               26540100
    ## 6                                               26540100
    ##   head.dat.team.order.dat.salary..decreasing...TRUE...
    ## 1                                                  CLE
    ## 2                                                  BOS
    ## 3                                                  TOR
    ## 4                                                  GSW
    ## 5                                                  HOU
    ## 6                                                  OKC

``` r
##Display the player name, team, and points3, of the top 10 three-point players
data.frame(head(dat$player[order(dat$points3,decreasing = TRUE)],n=10),head(dat$points3[order(dat$points3,decreasing = TRUE)],n=10),head(dat$team[order(dat$points3,decreasing = TRUE)],n=10))
```

    ##    head.dat.player.order.dat.points3..decreasing...TRUE....n...10.
    ## 1                                                    Stephen Curry
    ## 2                                                    Klay Thompson
    ## 3                                                     James Harden
    ## 4                                                      Eric Gordon
    ## 5                                                    Isaiah Thomas
    ## 6                                                     Kemba Walker
    ## 7                                                     Bradley Beal
    ## 8                                                   Damian Lillard
    ## 9                                                    Ryan Anderson
    ## 10                                                     J.J. Redick
    ##    head.dat.points3.order.dat.points3..decreasing...TRUE....n...10.
    ## 1                                                               324
    ## 2                                                               268
    ## 3                                                               262
    ## 4                                                               246
    ## 5                                                               245
    ## 6                                                               240
    ## 7                                                               223
    ## 8                                                               214
    ## 9                                                               204
    ## 10                                                              201
    ##    head.dat.team.order.dat.points3..decreasing...TRUE....n...10.
    ## 1                                                            GSW
    ## 2                                                            GSW
    ## 3                                                            HOU
    ## 4                                                            HOU
    ## 5                                                            BOS
    ## 6                                                            CHO
    ## 7                                                            WAS
    ## 8                                                            POR
    ## 9                                                            HOU
    ## 10                                                           LAC

Group By
--------

``` r
##Create a data frame with the average height, average weight, and average age, grouped by position
POIH <- aggregate(dat$height,by=list(dat$position),FUN= mean)
POIW <- aggregate(dat$weight,by=list(dat$position),FUN= mean)
POIA <- aggregate(dat$age,by=list(dat$position),FUN= mean)
data.frame(Height=POIH, Weight=POIW,Age=POIA)
```

    ##   Height.Group.1 Height.x Weight.Group.1 Weight.x Age.Group.1    Age.x
    ## 1              C 83.25843              C 250.7978           C 25.93258
    ## 2             PF 81.50562             PF 235.8539          PF 25.93258
    ## 3             PG 74.30588             PG 188.5765          PG 26.38824
    ## 4             SF 79.63855             SF 220.4699          SF 27.07229
    ## 5             SG 77.02105             SG 204.7684          SG 26.20000

``` r
##Create a data frame with the average height, average weight, and average age, grouped by team
TEAH <- aggregate(dat$height,by=list(dat$team),FUN= mean)
TEAW <- aggregate(dat$weight,by=list(dat$team),FUN= mean)
TEAA <- aggregate(dat$age,by=list(dat$team),FUN= mean)
data.frame(Height=TEAH, Weight=TEAW,Age=TEAA)
```

    ##    Height.Group.1 Height.x Weight.Group.1 Weight.x Age.Group.1    Age.x
    ## 1             ATL 79.14286            ATL 219.9286         ATL 28.42857
    ## 2             BOS 78.20000            BOS 219.8667         BOS 25.26667
    ## 3             BRK 78.66667            BRK 222.4000         BRK 25.46667
    ## 4             CHI 78.53333            CHI 215.6000         CHI 25.80000
    ## 5             CHO 78.80000            CHO 212.8000         CHO 25.86667
    ## 6             CLE 78.86667            CLE 226.4000         CLE 29.60000
    ## 7             DAL 79.13333            DAL 215.6667         DAL 26.93333
    ## 8             DEN 79.40000            DEN 220.2667         DEN 25.80000
    ## 9             DET 79.53333            DET 228.0000         DET 25.46667
    ## 10            GSW 79.86667            GSW 223.5333         GSW 27.73333
    ## 11            HOU 78.28571            HOU 214.8571         HOU 25.64286
    ## 12            IND 78.50000            IND 226.0714         IND 27.00000
    ## 13            LAC 78.80000            LAC 225.0667         LAC 29.53333
    ## 14            LAL 80.00000            LAL 224.3333         LAL 25.53333
    ## 15            MEM 79.26667            MEM 221.7333         MEM 27.40000
    ## 16            MIA 79.00000            MIA 219.2857         MIA 26.71429
    ## 17            MIL 80.35714            MIL 224.1429         MIL 25.71429
    ## 18            MIN 79.71429            MIN 221.5714         MIN 25.07143
    ## 19            NOP 79.50000            NOP 218.9286         NOP 25.78571
    ## 20            NYK 80.00000            NYK 218.3333         NYK 26.60000
    ## 21            OKC 79.26667            OKC 219.2000         OKC 25.73333
    ## 22            ORL 78.93333            ORL 216.2000         ORL 25.20000
    ## 23            PHI 79.33333            PHI 225.0000         PHI 24.73333
    ## 24            PHO 78.53333            PHO 213.8000         PHO 25.40000
    ## 25            POR 79.42857            POR 217.9286         POR 24.21429
    ## 26            SAC 78.46667            SAC 216.6000         SAC 25.86667
    ## 27            SAS 79.13333            SAS 217.3333         SAS 28.86667
    ## 28            TOR 79.06667            TOR 222.6000         TOR 25.20000
    ## 29            UTA 79.46667            UTA 222.1333         UTA 26.20000
    ## 30            WAS 79.50000            WAS 215.1429         WAS 25.85714

``` r
##Create a data frame with the average height, average weight, and average age, grouped by team and position.
data.frame(aggregate(dat[ ,c('age','weight','height')],by=list(dat$team,dat$position),FUN=mean))
```

    ##     Group.1 Group.2      age   weight   height
    ## 1       ATL       C 28.00000 252.5000 83.00000
    ## 2       BOS       C 27.33333 245.3333 83.33333
    ## 3       BRK       C 27.00000 267.5000 84.00000
    ## 4       CHI       C 25.66667 250.0000 83.00000
    ## 5       CHO       C 25.50000 245.5000 83.50000
    ## 6       CLE       C 27.33333 251.0000 83.66667
    ## 7       DAL       C 25.25000 243.2500 83.75000
    ## 8       DEN       C 25.66667 255.0000 83.66667
    ## 9       DET       C 27.00000 276.3333 84.00000
    ## 10      GSW       C 27.60000 251.0000 82.60000
    ## 11      HOU       C 21.66667 241.6667 81.33333
    ## 12      IND       C 26.00000 266.0000 82.50000
    ## 13      LAC       C 25.33333 258.3333 82.66667
    ## 14      LAL       C 24.66667 263.3333 83.66667
    ## 15      MEM       C 26.00000 246.0000 84.00000
    ## 16      MIA       C 29.66667 240.0000 82.00000
    ## 17      MIL       C 23.66667 236.6667 83.66667
    ## 18      MIN       C 26.00000 243.0000 83.00000
    ## 19      NOP       C 26.75000 256.5000 83.75000
    ## 20      NYK       C 25.75000 242.5000 83.00000
    ## 21      OKC       C 23.50000 250.0000 83.50000
    ## 22      ORL       C 23.33333 251.6667 83.00000
    ## 23      PHI       C 24.40000 254.0000 82.60000
    ## 24      PHO       C 27.00000 253.3333 83.33333
    ## 25      POR       C 22.00000 280.0000 84.00000
    ## 26      SAC       C 23.00000 248.3333 84.33333
    ## 27      SAS       C 32.33333 246.6667 83.00000
    ## 28      TOR       C 23.00000 251.3333 84.00000
    ## 29      UTA       C 25.00000 238.0000 84.50000
    ## 30      WAS       C 28.75000 245.0000 83.25000
    ## 31      ATL      PF 29.00000 236.5000 81.50000
    ## 32      BOS      PF 26.66667 235.3333 81.00000
    ## 33      BRK      PF 27.33333 239.3333 80.00000
    ## 34      CHI      PF 23.00000 225.0000 82.50000
    ## 35      CHO      PF 24.50000 238.5000 82.25000
    ## 36      CLE      PF 26.50000 245.5000 81.00000
    ## 37      DAL      PF 27.00000 224.0000 81.25000
    ## 38      DEN      PF 25.33333 231.0000 80.66667
    ## 39      DET      PF 23.66667 236.0000 82.00000
    ## 40      GSW      PF 25.00000 230.0000 80.00000
    ## 41      HOU      PF 26.00000 240.0000 82.00000
    ## 42      IND      PF 26.00000 249.2000 80.60000
    ## 43      LAC      PF 26.66667 243.6667 81.33333
    ## 44      LAL      PF 23.66667 239.0000 81.33333
    ## 45      MEM      PF 28.00000 234.0000 81.50000
    ## 46      MIA      PF 27.33333 231.3333 81.00000
    ## 47      MIL      PF 27.00000 243.0000 81.75000
    ## 48      MIN      PF 26.66667 239.3333 82.33333
    ## 49      NOP      PF 23.00000 221.0000 82.50000
    ## 50      NYK      PF 24.33333 225.0000 82.66667
    ## 51      OKC      PF 28.00000 237.5000 81.25000
    ## 52      ORL      PF 30.00000 235.0000 81.00000
    ## 53      PHI      PF 22.50000 230.5000 80.50000
    ## 54      PHO      PF 23.00000 227.6667 82.00000
    ## 55      POR      PF 24.00000 241.6667 83.00000
    ## 56      SAC      PF 25.50000 232.5000 81.50000
    ## 57      SAS      PF 29.33333 238.3333 82.00000
    ## 58      TOR      PF 25.33333 231.6667 81.33333
    ## 59      UTA      PF 25.75000 246.0000 81.25000
    ## 60      WAS      PF 24.00000 222.5000 82.50000
    ## 61      ATL      PG 28.33333 187.3333 74.33333
    ## 62      BOS      PG 23.66667 192.0000 72.00000
    ## 63      BRK      PG 24.00000 204.3333 76.33333
    ## 64      CHI      PG 25.25000 189.0000 75.50000
    ## 65      CHO      PG 27.75000 175.0000 73.75000
    ## 66      CLE      PG 25.66667 189.6667 73.00000
    ## 67      DAL      PG 28.50000 185.5000 73.25000
    ## 68      DEN      PG 27.00000 195.0000 74.50000
    ## 69      DET      PG 29.33333 196.0000 74.00000
    ## 70      GSW      PG 29.50000 191.0000 77.00000
    ## 71      HOU      PG 27.00000 188.3333 75.33333
    ## 72      IND      PG 28.00000 175.6667 73.33333
    ## 73      LAC      PG 31.50000 190.0000 72.50000
    ## 74      LAL      PG 21.00000 194.5000 76.00000
    ## 75      MEM      PG 23.66667 196.6667 75.66667
    ## 76      MIA      PG 27.00000 188.0000 75.50000
    ## 77      MIL      PG 26.00000 198.0000 76.00000
    ## 78      MIN      PG 22.66667 199.6667 75.33333
    ## 79      NOP      PG 25.00000 186.3333 74.33333
    ## 80      NYK      PG 25.50000 187.5000 74.50000
    ## 81      OKC      PG 26.66667 188.3333 74.66667
    ## 82      ORL      PG 27.66667 181.0000 74.00000
    ## 83      PHI      PG 27.33333 192.0000 74.66667
    ## 84      PHO      PG 27.00000 176.6667 72.33333
    ## 85      POR      PG 25.50000 185.0000 74.00000
    ## 86      SAC      PG 27.66667 190.0000 72.33333
    ## 87      SAS      PG 27.33333 180.0000 74.33333
    ## 88      TOR      PG 25.33333 194.3333 73.66667
    ## 89      UTA      PG 25.25000 190.0000 75.25000
    ## 90      WAS      PG 25.66667 185.3333 74.00000
    ## 91      ATL      SF 29.25000 215.2500 78.75000
    ## 92      BOS      SF 25.66667 221.6667 78.66667
    ## 93      BRK      SF 22.33333 209.3333 78.66667
    ## 94      CHI      SF 24.50000 217.5000 79.50000
    ## 95      CHO      SF 23.00000 232.0000 79.00000
    ## 96      CLE      SF 35.00000 231.5000 79.25000
    ## 97      DAL      SF 23.00000 195.0000 79.00000
    ## 98      DEN      SF 31.00000 222.6667 80.66667
    ## 99      DET      SF 24.00000 228.3333 79.66667
    ## 100     GSW      SF 32.33333 227.0000 79.33333
    ## 101     HOU      SF 25.00000 221.0000 80.00000
    ## 102     IND      SF 27.50000 222.5000 79.50000
    ## 103     LAC      SF 33.00000 225.0000 79.00000
    ## 104     LAL      SF 29.25000 214.0000 80.25000
    ## 105     MEM      SF 31.33333 220.0000 79.66667
    ## 106     MIA      SF 23.50000 225.0000 80.00000
    ## 107     MIL      SF 23.50000 228.0000 81.50000
    ## 108     MIN      SF 24.33333 215.6667 79.66667
    ## 109     NOP      SF 26.00000 217.3333 79.33333
    ## 110     NYK      SF 29.50000 227.5000 80.50000
    ## 111     OKC      SF 25.00000 218.2500 79.75000
    ## 112     ORL      SF 24.25000 217.2500 80.50000
    ## 113     PHI      SF 23.33333 216.0000 79.00000
    ## 114     PHO      SF 21.00000 210.0000 79.50000
    ## 115     POR      SF 24.75000 216.2500 80.50000
    ## 116     SAC      SF 28.50000 225.0000 79.00000
    ## 117     SAS      SF 25.00000 230.0000 79.00000
    ## 118     TOR      SF 27.33333 226.0000 79.66667
    ## 119     UTA      SF 30.00000 230.6667 79.66667
    ## 120     WAS      SF 25.00000 207.0000 80.00000
    ## 121     ATL      SG 24.00000 205.0000 78.00000
    ## 122     BOS      SG 23.00000 205.0000 76.00000
    ## 123     BRK      SG 26.75000 210.5000 76.75000
    ## 124     CHI      SG 28.50000 210.7500 75.75000
    ## 125     CHO      SG 26.25000 203.7500 78.00000
    ## 126     CLE      SG 30.66667 219.0000 78.00000
    ## 127     DAL      SG 29.00000 214.5000 77.50000
    ## 128     DEN      SG 21.75000 197.0000 76.75000
    ## 129     DET      SG 23.33333 203.3333 78.00000
    ## 130     GSW      SG 24.00000 191.6667 77.66667
    ## 131     HOU      SG 28.66667 191.6667 74.00000
    ## 132     IND      SG 28.50000 207.5000 76.00000
    ## 133     LAC      SG 30.66667 196.6667 76.33333
    ## 134     LAL      SG 26.33333 204.3333 77.33333
    ## 135     MEM      SG 27.33333 216.0000 76.33333
    ## 136     MIA      SG 25.50000 207.5000 76.50000
    ## 137     MIL      SG 27.00000 200.5000 77.00000
    ## 138     MIN      SG 26.00000 204.5000 77.50000
    ## 139     NOP      SG 27.50000 193.0000 76.00000
    ## 140     NYK      SG 28.25000 200.0000 77.50000
    ## 141     OKC      SG 23.50000 200.0000 77.00000
    ## 142     ORL      SG 24.50000 210.2500 77.50000
    ## 143     PHI      SG 26.00000 210.0000 77.50000
    ## 144     PHO      SG 27.00000 203.5000 76.50000
    ## 145     POR      SG 23.75000 202.7500 77.25000
    ## 146     SAC      SG 25.60000 203.8000 77.20000
    ## 147     SAS      SG 28.20000 207.0000 78.00000
    ## 148     TOR      SG 25.00000 209.6667 76.66667
    ## 149     UTA      SG 24.50000 210.0000 79.00000
    ## 150     WAS      SG 24.00000 205.6667 77.66667
