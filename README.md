# fcmeans
Implementation of Fuzzy-C-means clustering algorithm for JavaScript/TypeScript - *STILL IN DEVELOPMENT*
## motivation
Why using C-means clustering algorithms in JavaScript/TypeScript? Yes, JavaScript is not a typical language for data science methods but JavaScript is still the language for browsers. So if you want to create an application for web and want to calculate the clusters on clientside, you need an implementation for JavaScript. The k-means algorithm exists widely in JavaScript-space but unfortunately not the (n-dimensional, ![latex render n>3](https://latex.codecogs.com/gif.latex?n=\in\mathbb{N}%20\land%20n%3E3 "n\in\mathbb{N} \land n>3")) C-means algorithm which would always - instead of k-means - lead to same results. I don't want to create the perfect module for this but I want to set it public in hope to approximate it with the OpenSource community. So feel free to participate.

## Get started
### Installing
You can add this module to your project by this github repository while it's not published on npm.
```
npm install https://github.com/durek1337/cmeans
```
or
```
yarn add https://github.com/durek1337/cmeans
```

### Importing
Simply import the module to use it.

ES6
```javascript
import fcmeans from 'fcmeans'
```

CommonJS
```javascript
const fcmeans = require('fcmeans')
```

### Example
```javascript
import fcmeans, {calculateFuzzifier} from 'fcmeans'
var amount = 50
var dimensions = 3
var max = 10
var min = 1
var data_vectors = (new Array(amount)).fill(0).map((e,i) => (new Array(dimensions)).fill(0).map((e) => Math.round((max-min)*Math.random())+min))
var clusters = Math.floor(Math.sqrt(amount))
var fuzzifier = calculateFuzzifier(dimensions,amount)
var result = fcmeans({k : clusters, vectors : data_vectors, epsilon : 0.0001, fuzziness : fuzzifier})
console.log("fuzzifier",fuzzifier,"result",JSON.stringify(result))
```


<details>
<summary>Results for one execution</summary>
fuzzifier 6.964152032076
result
<code>{"centroids":[[6.32818075403257,4.645920074604211,6.104947524131507],[4.4165881209614355,5.750511348130167,4.971218575506165],[3.716478703947623,5.768237395462908,3.6774287921482816],[5.911578846963853,6.524336740532647,6.5796632970456885],[5.88850532588595,6.062890654099869,5.385919464774966],[7.660864679991841,8.3838885365249,7.84442448271217],[6.314048466841104,4.40610461995109,6.1568155759328596]],"membershipMatrix":{"rows":50,"cols":7,"mtx":[[0.14101754863046384,0.13254955690293205,0.12094363838588558,0.16218906783865972,0.1411503374711683,0.16256312932041894,0.1395867214504716],[0.14219970919606614,0.1513714154040498,0.16142248215517424,0.13622622230125675,0.1426326829799189,0.12357548853254588,0.14257199943098833],[0.1353810947026932,0.13038409472196238,0.12412486741706753,0.1466060272330747,0.13869952677244995,0.1906203165292354,0.13418407262351684],[0.14007960207059666,0.1488418878529835,0.14312007349672595,0.14822209141440781,0.142729956806541,0.1373326276892769,0.13967376066946818],[0.15089068244926107,0.1276830440855284,0.11511254116132892,0.16476788093512082,0.14306556344441757,0.1497674811469817,0.14871280677736146],[0.14514314472656636,0.16130530089813724,0.15114721127148237,0.13854315718869956,0.14224427923106023,0.11575813719345791,0.14585876949059629],[0.15351348151558109,0.13412695740647979,0.12718402513272822,0.14467785521517412,0.14186150721181012,0.1441312545178399,0.15450491900038676],[0.16419126224651395,0.1332911504142122,0.12337400547584614,0.14264583748369333,0.1400248430223517,0.1282635479763638,0.1682093533810189],[0.1395250953901285,0.1517269113748468,0.1607292442947358,0.13667206532570705,0.15154186190915794,0.1216349564736846,0.13816986523173924],[0.16057721498483493,0.13304928720404186,0.12536192117808356,0.14203623600502321,0.14254607107889425,0.13388363414892807,0.16254563540019415],[0.135895484965127,0.15701319584658216,0.17505097825164254,0.13524618444629993,0.1409253771397269,0.12021172944766048,0.13565704990296099],[0.13415724522774203,0.13896952848698302,0.13155359309343637,0.15402632928820859,0.1431302494673293,0.1655269099526127,0.13263614448368802],[0.14037859991902446,0.15511941580764158,0.14445382895091197,0.13839193048914533,0.171397489462739,0.113015474859835,0.1372432605107027],[0.133332378411552,0.15472311231040906,0.16136972520349188,0.14270971621519574,0.14487861658073092,0.13080975763497354,0.13217669364364687],[0.1260622082426908,0.12086801625678051,0.11346895139508101,0.1419085807732672,0.13125836199826085,0.2419664751637602,0.12446740617015944],[0.15249366490686206,0.14325392095459955,0.13376491532933843,0.14540285210831722,0.14130600513291683,0.12952003131534642,0.1542586102526195],[0.13622612759459232,0.13005320915671004,0.12273771070213045,0.14836937598827896,0.1378702463192367,0.18959532520132238,0.13514800503772914],[0.13494856070581285,0.15369448325268678,0.1725206144629411,0.13667538100507767,0.14326496545074338,0.12465219413213445,0.13424380099060382],[0.13477747957755096,0.13279821035124478,0.12205591668376385,0.16351561251835278,0.15362777837884495,0.16147411249388177,0.13175088999636086],[0.1298855749908411,0.1701131437019896,0.16848258474927666,0.14043144296982876,0.14469160944025347,0.11793147234736226,0.12846417180044814],[0.1405898061058232,0.12859549996752534,0.11811219294276479,0.1576170986611352,0.13931762760449165,0.1766147090371766,0.13915306568108324],[0.13451830787307925,0.12829250398577124,0.12148314266758112,0.14700105772778094,0.14031579465416238,0.1955799084838096,0.13280928460781544],[0.13203304067404292,0.15625799275231317,0.1901368164636317,0.13205937459921363,0.14135563524891603,0.1168834710347602,0.1312736692271224],[0.13333446528895265,0.12644366135578686,0.11950491912786741,0.14543368971605106,0.1371027665979166,0.20631491345782935,0.13186558445559607],[0.14841548947478667,0.1498493238770946,0.13897498001688627,0.1456632420232866,0.14224596435105014,0.12552551652287527,0.1493254837340204],[0.14514314472656636,0.16130530089813724,0.15114721127148237,0.13854315718869956,0.14224427923106023,0.11575813719345791,0.14585876949059629],[0.1335939279883504,0.1298838079259363,0.12320010272413459,0.14724714418835427,0.13786737658774473,0.1959045484460027,0.13230309213947705],[0.13913338385850857,0.14672689441402273,0.15127020471089536,0.14126030913825394,0.14988508928136224,0.1339156938052588,0.1378084247916983],[0.15614717604089245,0.13620372841613815,0.1307502924401399,0.14109036023846908,0.1435908247053882,0.13462757266918376,0.15759004548978842],[0.15361293044491697,0.14220749526826457,0.1405614235890519,0.13749661885439185,0.14568742362962928,0.12568002769298842,0.154754080520757],[0.1356093187757044,0.1252888040205525,0.11753676984139853,0.14673555215785822,0.13746625709558574,0.20329272388293285,0.13407057422596777],[0.1436013221235592,0.15198421040876298,0.16120228016459817,0.13525494662133797,0.1426669439530464,0.12107546798162054,0.14421482874707472],[0.1335939279883504,0.1298838079259363,0.12320010272413459,0.14724714418835427,0.13786737658774473,0.1959045484460027,0.13230309213947705],[0.19107872218351163,0.12258801847975057,0.10894620995383743,0.13946190071127015,0.14758889647023565,0.11064348080408609,0.17969277139730844],[0.1493166356956151,0.1464905514430538,0.148895991441338,0.13657347183777982,0.1442872626515104,0.12404031858759114,0.15039576834311175],[0.1494275791975214,0.14958229286863103,0.15249338092466758,0.13474029543837568,0.1439589937312348,0.11907368932169274,0.1507237685178768],[0.14931691480547524,0.13906498415537655,0.1324628590935595,0.14390407528446192,0.158345187964712,0.13012749999523165,0.14677847870118313],[0.1329586211396854,0.15085731132621188,0.15011630267431542,0.14737177342215602,0.1519658196628791,0.13573156537620767,0.13099860639854452],[0.15089068244926107,0.1276830440855284,0.11511254116132892,0.16476788093512082,0.14306556344441757,0.1497674811469817,0.14871280677736146],[0.1367773388114423,0.14131626045211337,0.1329198818702521,0.15482752447806175,0.14287643733220573,0.15571498210302678,0.13556757495289795],[0.1351999414762904,0.1805511217698245,0.1415361238879008,0.14782894519436582,0.14975930096123705,0.11186720862409638,0.13325735808628514],[0.1347341723409316,0.1394288565353767,0.1346597792818697,0.1503722696399123,0.1486439457423991,0.15938084178094614,0.1327801346785645],[0.16414534902707714,0.13714447858825352,0.12972352565251344,0.13694344915119788,0.14146182117674425,0.12163585193828777,0.16894552446592606],[0.1498780245713282,0.1514850663915002,0.1431095117593948,0.14091081784906556,0.14176358882056583,0.12133639120624531,0.15151659940190007],[0.15776297492650576,0.13805883151238293,0.13113920321128036,0.14110927808812462,0.1411223427577865,0.130003100699182,0.16080426880473786],[0.13563175868905175,0.15261802313606232,0.1662281572173008,0.13872433743084875,0.14352518480819784,0.12833708156295232,0.13493545715558616],[0.1400521280384631,0.1395889346632645,0.1345799610734666,0.14818630556038734,0.1548952731683631,0.14496446200669091,0.13773293548936447],[0.15897898081286577,0.1445718189163398,0.1370799375056675,0.1366568661830124,0.14137201018260775,0.1182656293900611,0.16307475700944568],[0.13898852914497115,0.15555253500964683,0.15161207464966409,0.14452648823607486,0.1427046641418887,0.12797448583293392,0.1386412229848205],[0.14461959876875924,0.1443369114248193,0.14491872602240838,0.14041681322694954,0.15205655398507598,0.1303259420278532,0.14332545454413442]]}}</code>
</details>
The assignments in `result.membershipMatrix.mtx` has a length of 7 (which is also stored in `result.membershipMatrix.cols`). This amount was calculated and stored in variable `clusters`. The values of `result.membershipMatrix.mtx` are between 0 and 1 but the values scatter around ![latex render 1 devided by clusters](https://latex.codecogs.com/gif.latex?\frac{1}{clusters} "1 devided by clusters"). The sum of all elements of one membership array is 1 (negleted computation errors which could lead to a little bit lower value).


## Sources
* Algorithm implementation by https://github.com/nantunes/figue
* Fuzzier-Finder: A simple and fast method to determine the parameters for fuzzy c–means cluster analysis doi:10.1093/bioinformatics/btq534
