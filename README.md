# Tax evasion study in a society realized as a dilutedIsing model with competing interactions (article from J. Giraldo-Barreto et J. Restrepo)

## Résumé

Dans cet article, les auteurs s'intéressent au problème économique et
social qu'est l'évasion fiscale, qui consiste, pour un agent, à réduire
le montant de ses impôts en transférant ses actifs dans un pays où la
fiscalité est plus avantageuse.

Afin d'approcher ce phénomène, ils reprennent dans leur recherche le
modèle d'Ising, décrivant une société constituée de $N$ agents (spins
d'Ising) qui font le choix de payer ou non leurs taxes (2 valeurs de
spin : $\sigma = +1$ ou $-1$) et entre lesquels s'échangent des
informations. Ces interactions d'échange (liaisons paramagnétiques,
ferromagnétiques ou pendantes) créent une forme de frustration similaire
à la frustration magnétique chez l'agent qui doit prendre une décision
tout en prenant compte des informations contradictoires communiquées par
ses plus proches voisins. De plus, tous les individus sont soumis aux
politiques gouvernementales (champ magnétique externe $H$) et peuvent
être audités avec une certaine probabilité $\alpha$.

D'autres paramètres exogènes sont étudiés. La température $T$ par
exemple, est ici perçue comme un paramètre global représentant le temps
qu'il faut pour qu'une politique soit réellement appliquée. L'évasion
fiscale devient importante lorsque cette température dépasse la
température transitoire $T_c$ (temps accordé pour payer une taxe).

Par ailleurs, les auteurs précisent que certains paramètres
psychologiques peuvent influer sur le taux d'évasion fiscale. Ils
montrent ainsi que la mise en place d'un système d'audit, même faible,
et de périodes de pénalité permet de réduire significativement le
pourcentage d'évasion fiscale, certains agents craignent plus que
d'autres la pénalité encourue. De plus, pour une probabilité d'audit
nulle, les interactions d'échange n'influent pas sur l'état stationnaire
d'évasion fiscale final. En revanche, pour une probabilité d'audit non
nulle, les informations qui proviennent des interactions d'échange
contribuent à maintenir les agents indécis sur une plus longue période
et conduisent à changer l'état stationnaire final de l'évasion.

Afin de déterminer les mesures qu'il faudrait mettre en place pour
réduire l'évasion fiscale, les chercheurs ont reproduit avec ce modèle
les résultats obtenus avec le cas de la Colombie, où l'évasion fiscale
et la corruption sont particulièrement présents. Les valeurs du champ
magnétique et de la probabilité d'audit ont été choisis en fonction des
politiques fiscales mises en place dans le pays au cours des dernières
années. Ils concluent que la combinaison d'une politique gouvernementale
souple et d'une probabilité d'audit non nulle est nécessaire pour
réduire efficacement l'évasion fiscale.

## Modélisation

::: center
Figure 1 : *graphique représentant le taux d'évasion fiscale en fonction
de la politique*

![image](figure.png)
:::

Nous avons modélisé le modèle d'Ising de l'article dans le cas où il n'y
a aucun contrôle fiscal, c'est-à-dire où l'on a $\alpha = 0$.
$$f.ev =  \frac{1}{N}\sum_{\sigma_i = -1} |\sigma_i|$$

Nous avons alors représenté le taux d'évasion fiscale (f. ev) en
fonction de la sévérité de la politique appliquée (H \[J\]).

On observe alors qu'en effet plus la politique est sévère plus la fraude
fiscale se fait rare, ce qui est en accord avec la réalité.

Contrairement à ce que présenter par l'article, nous avons observé que
la température n'a pas un grand impact sur le taux d'évasion fiscale
dans notre modèle. Cela peut s'expliquer par plusieurs raisons :

1.  L'article ne spécifiait pas les constantes utilisées ($k_B$, $J$,
    \...), nous avons pu par erreur utiliser des constantes non-adaptées
    faussant ainsi le résultat.

2.  L'expérience initiale effectue beaucoup d'opérations et prend une
    grille plus grande que la nôtre. Nous avons choisi de réduire ces
    dimensions car le temps de calcul devenait trop long et il était
    impossible de faire marcher le notebook correctement. Cette prise de
    liberté a pu être une source d'erreurs.

Lien GitHub :
<https://github.com/greygoose775/ProjPhysique/blob/main/PhysiqueSoc.ipynb>

## Lien avec le cours

Afin d'illustrer le phénomène d'évasion fiscale, les auteurs de cet
article utilisent un modèle de physique statistique similaire au
Random-Field Ising Model (RFIM), originellement introduit pour expliquer
les propriétés magnétiques de systèmes désordonnés qui présentent des
défauts ou des impuretés. En sciences sociales, ce modèle illustre un
choix binaire effectué par des agents : acheter ou vendre, porter le
masque ou non, payer les taxes ou non...

Les $N$ agents sont modélisés par des particules qui ne peuvent prendre
que 2 valeurs de spin : ceux qui payent leurs taxes prennent la valeur
$\sigma_i = +1$, ceux qui ne les payent pas prennent la valeur
$\sigma_i = -1$. Les agents interagissent entre eux et sont reliés par 3
types de liaisons différentes (paramagnétiques, ferromagnétiques ou
pendantes), décrivant l'influence sur un agent donné des choix effectués
par ses plus proches voisins. Dans le modèle de Giraldo-Barreto,
l'opérateur hamiltonien, analogue à l'énergie totale de l'alliage
constituant la société d'agents, est donnée par l'équation (1) :
$$\mathcal{H} = -\sum_{<i,j>} J_{ij}\sigma_i \sigma_j - \sum_i\sigma_i H + \sum_{i \in A | \sigma_i=-1}\sigma_i g_i(t-h)$$

Les valeurs propres de cet opérateur correspondent à l'énergie
$E(\sigma_i)$ de chaque site i, qui décrit l'incitation de l'agent i à
faire le choix $\sigma_i = 1$. L'expression (1) s'apparente à celle de
l'énergie d'un site obtenue pour le RFIM et vue en cours (à la
différence près que l'expression désigne l'énergie globale du système,
et non pas celle d'un site). On retrouve dans les deux cas l'effet de
pression sociale ou d'imitation, représenté par le terme incluant la
matrice de connectivité $J_{ij}$ : si $J_{ij} > 0$ (liaisons
ferromagnétiques), l'agent i aura tendance à imiter l'agent j ; si
$J_{ij} < 0$ (liaisons paramagnétiques), l'agent i aura tendance à faire
le choix contraire à celui de l'agent j ; et si $J_{ij} = 0$ (liaisons
pendantes), la décision de l'agent $j$ n'aura pas d'influence sur
l'agent i et vice-versa. Contrairement au modèle vu en cours où on
considérait les interactions entre tous les agents, le modèle étudié ici
ne considère que les interactions entre premiers voisins. Dans les deux
modèles, les agents sont soumis à un champ magnétique extérieur uniforme
modélisant un facteur exogène. Dans le modèle de Giraldo-Barreto, $H$
représente les politiques gouvernementales imposées aux agents. Dans le
modèle vu en cours, ce second terme représente l'information publique et
accessible par tous les agents. Le modèle RFIM inclue aussi un troisième
terme $f_i$ qui renvoie à l'inclination personnelle (expérience
personnelle ou éducation de l'agent). Ce terme n'apparaît pas dans (1)
mais est remplacé par un terme qui donne l'interaction entre les agents
qui ne souhaitent pas payer leurs taxes et un champ local $g_i$
correspondant à un audit de l'agent $i$ par l'Etat, caractérisé par une
probabilité $\alpha$ d'intervention.

De plus, les agents considérés souhaitent maximiser leur profit (théorie
du choix rationnel) mais tout en prenant compte des interactions
d'échange avec leurs plus proches voisins et du risque d'audit encouru.
La probabilité d'un agent i à prendre la valeur +1 ou -1 s'écrit :

$$\pi(\sigma_i) = \frac{1}{1 + e^{-\frac{E(-\sigma_i)-E(\sigma_i)}{k_B T}}}$$

avec $E(-\sigma_i) – E(\sigma_i)$ l'énergie associée à un changement de
valeur du spin au site i.

Cette règle de décision, qui présente des similarités avec la règle du
logit, prend donc aussi en compte les interactions d'échange entre les
agents et l'Etat. Dans le RFIM, l'inverse de la température $\beta$ qui
apparaît dans la règle du logit, caractérise le niveau de rationalité de
l'agent tandis que dans le modèle de Giraldo-Barreto, la température est
un paramètre global qui est à associer au temps requis pour qu'une
politique soit réellement mise en place.

Enfin, on constate d'autres similitudes entre les modèles. Par exemple,
la magnétisation globale définie par $m_k = \frac{1}{N}\sum_i \sigma_i$
est analogue à l'opinion moyenne définie dans le RFIM. Sur les
graphiques obtenus par les auteurs et sur celui obtenu à partir de
l'expression de l'aimantation $m$ en fonction du champ $h$ (équation de
Curie-Weiss), on peut discerner une phase paramagnétique et une phase
ferromagnétique. Dans les deux cas, la phase paramagnétique est
caractérisée par une valeur critique (une température de transition
$T_c$ ou une valeur moyenne d'interaction d'échange de transition
$J_c$).

## Critique du modèle

Dans cet article, Giraldo-Barreto et Restrepo souhaitent étudier les
comportements des fraudeurs fiscaux dans une société où l'État peut
intervenir et où les différents agents de cette société peuvent
s'influencer mutuellement. Un individu fraudeur (respectivement non
fraudeur) est caractérisé par un spin de valeur -1 (respectivement 1).
Les auteurs ont fait le choix de considérer dans leur modèle que tout ce
qui conduit un individu à prendre une valeur de spin ou une autre est
exogène. En effet, cette valeur évolue au cours du temps suite à des
interactions avec d'autres individus ou avec leur milieu. Néanmoins,
nous pouvons déjà remarquer que la décision de frauder d'un individu,
dans la vraie vie, ne provient pas que de ses influences extérieures
mais est aussi liée à sa classe sociale, à sa situation financière, à
son niveau d'éducation ou encore à son caractère tout simplement. Le
modèle ne prend pas en compte ce genre de possibilités car un individu
de ce type ne peut pas être rapproché d'un individu isolé : quelles que
soient les informations qu'il reçoit de ses voisins ou de ses relations
avec son milieu, il est un fraudeur de par sa nature et ses
caractéristiques personnelles. De ce fait, nous pourrions imaginer que
l'inclusion d'un facteur représentant les différences individuelles de
chaque agent améliorerait le modèle. Nous pourrions l'implémenter comme
une valeur comprise entre 0 et 1, une sorte de note, qui dicte, en
fonction des particularités individuelles, l'appétence pour la fraude
fiscale de chaque individu. De plus, les auteurs font l'hypothèse dans
leur modèle qu'il existe trois types d'interactions entre voisins :
ferromagnétique, paramagnétique et dilué. Par conséquent, les individus
encerlés de liaisons contradictoires paramagnétiques et ferromagnétiques
font face à des informations conflictuelles tandis que les individus
encerclés de liaisons diluées ont une forme de libre arbitre, car isolés
dans leur décision entre respecter la loi ou non. Ainsi, le manque de
prise en compte des prédispositions individuelles peut amener à une
situation où les individus ne savent pas quoi choisir entre frauder ou
non, ce qui ne nous permet pas d'étudier leurs comportements. Une autre
hypothèse des auteurs que nous jugeons critiquable est que, au contraire
d'autres études sur le sujet, ils utilisent la valeur de J, qui est
l'ampleur des interactions entre les individus, de façon globale et non
pas locale. Cela signifie qu'ils ne prennent pas non plus en compte les
différences de constitution des milieux de chaque individu et que tous
les échanges d'information et toutes les interactions entre les
individus ont la même valeur. De ce fait, tous les individus influencent
tous leurs voisins de la même façon, quelles que soient leurs
caractéristiques personnelles : un chef d'entreprise aura la même
influence sur ses pairs qu'un criminel multirécidiviste, ce qui paraît
absurde. Néanmoins, nous pouvons comprendre le choix des auteurs de
maintenir cette hypothèse pour des besoins de simplification du modèle.
Pour finir, les auteurs supposent l'équiprobabilité des interactions
ferromagnétiques, paramagnétiques et diluées, i.e. P(0) = P(-J) = P(J).
Ceci implique qu'être un individu isolé n'est pas une notion locale, car
chaque agent peut se retrouver dans la même disposition avec une même
probabilité, enlevant donc l'intérêt d'étudier les comportements des
fraudeurs fiscaux en fonction du comportement de leurs voisins. Nous
pensons qu'il est en effet plus que logique de supposer que les
individus isolés du point de vue de l'information sont entourés par le
même genre d'individus car sinon ses voisins auraient une influence,
quelle qu'elle soit. Nous comprenons encore une fois ce choix de la part
des auteurs qui préfèrent simplifier leur modèle, quitte à perdre en
précision.
