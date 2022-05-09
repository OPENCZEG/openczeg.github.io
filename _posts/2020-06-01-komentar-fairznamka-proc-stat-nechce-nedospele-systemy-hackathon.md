---
title: "Komentář: Proč stát nechce nedospělé systémy z hackathonů?"
subtitle: <ul><li>Hackathon na dálniční známky byl skvělý pokus o agylní vývoj, ale nepovedlo se to.<li>Proč říkám takovým projektům nedospělé a co dělat jinak?<li>Nebojte se vývoje pro veřejnou správu, ale potřebujete hodně znalostí.</ul>
author: Michal Rada
category: [clanky]
tags: [Vývoj, Autorské články, Komentáře, ISVS]
---

Aby bylo hned od začátku jasno. Nemám nic proti nadšeneckým aktivitám open-source komunity. Myslím, že je to oproti postupům tradičních dodavatelských firem hodně osvěžující přístup, jak pro veřejnou správu něco dělat. Ale přeci jen jsou dosavadní výsledky velice nedospělé. A protože jsem byl požádán, abych jeden takový zhodnotil (a v hodnocení nedopadl moc dobře), je myslím férové, abych nabídl svůj pohled na věc, a hlavně pár rad budoucím snahám. Ano, bavím se o výsledku e-shopu na dálniční známky, ale to byla jen první kapka v moři. Spíše než kritiku si takovéto projekty zaslouží radu a pomoc, jak se stát dospělejšími.

Poté co Státní fond dopravní infrastruktury (SFDI) - tedy ne Ministerstvo dopravy, jak se často mylně uvádí - málem utratil půl miliardy za systém na elektronické dálniční známky, chopila se tohoto fantu open-source komunita a během pár dnů nabídla státu e-shop pro dálniční známky. A co na to stát? Nepřekvapivě tento systém nechce. Mohlo by se zdát, že důvody pro odmítnutí řešení vzniklého z hackathonu jsou ryze byznysové a že zatím stojí potenciální dodavatelé systému pro SFDI. Tuhle část posuzovat nechci a ani mi to nepřísluší. Nicméně byl jsem požádán, abych zhodnotil dodané dílo z pohledu souladu s architektonickými principy Národní architektury ČR a s požadavky na informační systémy veřejné správy. A v tomto hodnocení bohužel jinak fandovsky skvěle zvládnutý systém pohořel. To je na jednu stranu škoda. A protože nerad jen kritizuji bez návrhu na zlepšení, berte mé následující řádky jako doporučení pro budoucí obdobné snahy.

**Na špatné zadání musí přijít špatná odpověď**

Všechno začíná od začátku. A na počátku bylo slovo. A to slovo bylo "zadání". Každý projekt musí mít správně definované zadání. K tomu nestačí prosté dvě věty: "Chceme e-shop na dálniční známky podle zákona. Nechceme za to utratit 500 milionů." Ta druhá se nepovedla od samotného počátku, ale ta první je taky špatně. Stát v podobě SFDI šel od počátku velice podivnou cestou, kdy se pokusil schovat nedokonalé zadání a nepromyšlené řešení pod roušku utajovaných neveřejných informací. Jistě, kdyby šlo o e-shop na zbraně a jaderný odpad, dalo by se to pochopit. U systému na elektronické dálniční známky to ale pochopitelné a omluvitelné není. Samozřejmě, že v takovém systému i z pohledu zákona jsou neveřejné informace, například informace o vozidlech zpravodajských služeb. Ale kvůli tomu utajit celé ICT řešení je naprostý nesmysl. To jsem mimochodem říkal nejen já od začátku.

Prvotní myšlenka je tedy zcela špatná. Bohužel cokoliv se na ni nabalilo, bylo stejně špatné. Od samotné premisy zadání, že se jedná o "e-shop" (přičemž systém pro elektronický nákup přes internet byl jen jednou z částí systému), až po nedostatky v rozmyšlení toho, jak má být takový systém zadán. Architektura samotného řešení byla zpracována dobře. O tom svědčí i bezproblémové stanovisko Odboru hlavního architekta MV k žádosti o souhlas s realizací projektu. Architektonicky dobrý koncept narážel ale už i v této fázi na nesrovnalosti. OHA vůbec nehodnotil fakt, že SFDI celý systém zabalilo pod nesmyslné utajení, navíc bez detailního rozboru důvodů. Dále nikdo nehodnotil způsob poptávky a zadání, jež nepočítalo s otevřenou soutěží. 

Chyběly podrobnosti na straně zadávacích podmínek, a především technických a byznys požadavků v zadávací dokumentaci. Zadání se dost odlišovalo od architektonického záměru a popisu řešení, a právě díky tomu se tam podařilo schovat několik poměrně hluboko zakopaných psů. 

**Není to e-shop, nebude to e-shop a nikdy to neměl být e-shop**

Obchod pro majitele vozidel, kde si mohou elektronicky koupit dálniční známku, je sice pro občana to nejvíc viditelné, ale v komplexnosti informačního systému, jak jej definuje zákon, se jedná o naprosto zanedbatelnou věc. Ano, kdyby se jednalo jen o e-shop, tak se to dá postavit za den, zadarmo a naprosto bez problémů.

Problém je ale v tom, že to e-shop není. Jedná se o poměrně komplexní ICT řešení pro celou agendu dálničních známek. Není to sice systém pro šmírování řidičů, jak se snaží bulvarizovat neodborný a místy až dementní [článek na Seznamu](https://www.seznamzpravy.cz/clanek/e-shop-na-dalnicni-znamky-byl-zasterkou-pro-tajny-sledovaci-system-87866), ale jedná se opravdu o komplexní řešení. A zase se v bulváru vypichuje jen jeden aspekt. Sledování pohybu vozidla podle jeho SPZ. Všichni jsou najednou hrozně vyděšeni z toho, že systém měl z kamer sledovat, kdo projíždí kontrolním bodem a podle SPZ vyhodnocovat, kdo známku má a kdo ne. Odhlédněme teď od toho, že zaznamenávání SPZek a porovnávání s databází známek je jedinou cestou, jak splnění povinnosti kontrolovat i od toho, že podobný mechanismus mají de facto všechny státy, kde e-známky fungují a kde se nepoužívají nálepky na sklo.

Systém je zjevně složitější než jen nějaký obyčejný e-shop či vyhledávač SPZ vozidel a porovnávání s databází, kdo si v e-shopu pro danou SPZ koupil a kdo ne. A v tom je právě ten problém. Agenda dálničních známek, jak ji definuje [zákon o pozemních komunikacích ve znění od 1. ledna 2021](https://www.zakonyprolidi.cz/cs/1997-13/zneni-20210101), je opravdu docela složitá. Cílem tohoto komentáře není dělat rozbor celé agendy, na to jsou jistě povolanější, a hlavně se to mělo stát už dávno.

**Nadáváme na nedospělá řešení**

Nejsem sám, kdo v takových hurá akcích, jako byl tento hackathon upozorňuje na to, že takto narychlo "nakóděné" pseudosystémy jsou nedospělé a nepoužitelné a v důsledku to agilnímu vývoji v české veřejné správě dělá víc škody než užitku. Výsledek můžete vidět třeba na [fairznamka.cz](https://www.zakonyprolidi.cz/cs/1997-13/zneni-20210101), což je oficiální web projektu, nebo v příslušných repozitářích.

Jsou to skvělé akce, které ukazují, že na každý systém nepotřebujete tisícovky programátorů a obchoďáků a stamiliony hodin. Jenže, výsledek je jaksi... naprosto naprd. Výsledkem je aplikace, která řeší ani ne pětinu zadání ze zákona, a navíc neodpovídá základním požadavkům na ISVS, dokonce se o tom v dokumentaci de facto ani nedočtete.

**Co dělat jinak?**

Přeci jen "nadšení nestačí", a aby z hackathonu nevypadl další "hnus fialovej", je třeba to vzít opravdu vážně.

Jedna věc je nadšení a chuť ukázat tradičním velkotovárnám na dodávky ISVS, jak se to má dělat v jedenadvacátém století. To je skvělé a maximálně tomu fandím. Ale to taky nestačí.

Existuje správná cesta? Ano. Kromě nadšenců do programování a "čtečů" zadání (mimochodem dosti nekompletního), to chce také architekty, kteří rozumí požadavkům a EG, analytiky, kteří ví, jak fungují systémy ve veřejné správě a další odborníky. Jen kodéři to nezachrání.

1. Vždy se musíte dívat pod kameny: To, co se o systému požadovaném veřejnou správou dočtete v internetových médiích nestačí. Vždy počítejte s tím, že to zkrátka "bude o dost složitější", než to na první pohled vypadá.
2. Musíte rozumět agendě: Pokud chcete budovat informační systém pro veřejnou správu, musíte podrobně rozumět tomu, k čemu má takový systém opravdu sloužit. To chce si nejen přečíst zákony (ne jeden zákon), ale udělat si v hlavě i jejich dekompozici.
3. Musíte rozumět ISVS: Další věcí, které musíte dobře rozumět, je mechanismus ISVS (informačního systému veřejné správy) a povinnostem, které se týkají jeho vývoje, rozvoje, správy, provozu atd. Samozřejmě maximum povinností má "správce", ale i dodavatel leccos musí umět a vědět, jinak pohoří.
4. Neignorujte povinnosti: Jasně, zákon o ISVS je jedna věc, ale jde to dál. Od září 2019 existuje [závazná národní architektura](https://archi.gov.cz), u které to, co děláte, musí být v souladu, ale také vám dává hodně obecných návodů, jak a co dělat. Bez této znalosti se do vývoje snad ani raději nepouštějte.
5. Uvědomte si, co děláte: Nebudujete systém pro firmu vyrábějící obaly na brambůrky. Informační systémy ve veřejné správě jsou prostě svázány řadou i dost otravných (na vývoj) pravidel. A ta se musejí dodržovat. Dodávat do veřejné správy vyžaduje ohromné množství architektonických a byznysových a procesních znalostí. Bez nich to vždycky dopadne špatně.
                                                                                                                                                               
----------

Jako odborník na architekturu jsem byl po dokončení projektu požádán, abych celou věc zhodnotil z hlediska architektury a souladu s EG principy. Proto si dovolím být tak kritický. Nechci ale ukazovat prstem, jen chci na tomhle příkladě ukázat, jak se to má dělat. Nechci účastníky hackathonu na férové známky nikterak urážet a snižovat obrovské množství kvalitní programátorské víkendové dřiny. Bohužel ale přišla vniveč, a to by se stávat nemělo. I agilní hackathony musí dospět, aby je někdo bral vážně.