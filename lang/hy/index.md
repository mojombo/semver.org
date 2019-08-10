---
title: Սեմանտիկ Տարբերակում 2.0.0
language: hy
---

Սեմանտիկ Տարբերակում 2.0.0
==============================

Համառոտ
------

Այս ֆորմատով ներկայացված տարբերակի համարի (version number) դեպքում՝
ՄԱԺՈՐ․ՄԻՆՈՐ․ՓԱԹՉ (MAJOR.MINOR.PATCH), պետք է մեծացնել՝

1. ՄԱԺՈՐ տարբերակի համարը, երբ տեղի են ունեցել API֊ի այնպիսի փոփոխություններ,
   որոնց արդյունքում խախտվել է հետ համատեղելիությունը։
2. ՄԻՆՈՐ տարբերակի համարը, երբ ավելացվել է նոր ֆունկցիոնալ՝ հետ
   համատեղելիությունը չխախտելով (backwards-compatible)։
3. ՓԱԹՉ տարբերակի համարը, երբ տեղի են ունեցել հետ համատեղելի փոփոխություններ։

Կարելի է անել նաև հավելյալ նշանակումներ՝ որպես հավելում ՄԱԺՈՐ․ՄԻՆՈՐ․ՓԱԹՉ
ֆորմատին․ մինչթողարկումային (pre-release) պիտակ (label) և բիլդ-մետատվյալ
(build metadata)։

Ներածություն
----------

Ծրագրային ապահովման մենեջմենթի աշխարհում գոյություն ունի «կախվածությունների
դժոխք» (dependency hell) հասկացություն։ Ձեր համակարգի մեծացման և դրան ինտեգրված
փեքիջների քանակի ավելացման հետ մեծանում է հավանականությունը, որ դուք վաղ թե ուշ  
կկանգնեք այս խնդրի առաջ։

Այն համակարգերում, որոնք ունեն շատ կախվածություններ, նոր տարբերակի թողարկումը
կարող է արագ վերածվել մղձավանջի։ Եթե կախվածությունների սպեցիֆիկացիան շատ խիստ է,
դուք կարող եք կանգնել նոր տարբերակի թողարկման արգելքի (version lock) առաջ
(անհնար է դառնում թարմացնել ծրագիրը՝ առանց թարմացնելու կախման մեջ գտնվող բոլոր
փեքիջները)։ Մյուս կողմից էլ, եթե կախվածությունների սպեցիֆիկացիան շատ ազատ է,
դուք անխուսափելիորեն կբախվեք տարբերակի անհամապատասխանության (version
promiscuity) խնդրին․ անհիմն է ենթադրությունը, որ ձեր ծրագիրը կմնա համատեղելի
ապագա տարբերակների հետ։ «Կախվածությունների դժոխքը» մի իրավիճակ է, երբ տարբերակի
թողարկման և/կամ տարբերակի անհապատասխանության արգելքը թույլ չի տալիս ձեզ հեշտ և
անվտանգ զարգացնել ձեր նախագիծը։

Որպես այս խնդրի լուծում՝ ես առաջարկում եմ պարզ կանոններ և պահանջներ, որոնք
սահմանում են, թե ինչպես են սահմանվում և մեծացվում տարբերակների համարները։ Այս
կանոնները հիմնված են (բայց ոչ անպայման սահմանափակված) բաց (open source) և փակ
(closed source) ծրագրային ապահովման գոյություն ունեցող և լայն տարածում գտած
պրակտիկաների վրա։ Նախևառաջ, որպեսզի այս կանոններն աշխատեն, դուք պետք է սահմանեք
փաբլիք API: Այն կարող է նկարագրված լինել ինչպես դոկումենտացիայի, այնպես էլ կոդի
մեջ։ Կարևոր է, որ API֊ը լինի ճիշտ և հասկանալի։ Ձեր API֊ը հայտարարելուց հետո դուք
փոփոխությունների մասին կտեղեկացնեք տարբերակի համարը մեծացնելու միջոցով։
Դիտարկենք այս ֆորմատով ներկայացված տարբերակ՝ X.Y.Z (ՄԱԺՈՐ․ՄԻՆՈՐ․ՓԱԹՉ)։ Սխալների
ուղղումները (bug fix), որոենք չեն ազդել API-ի վրա, մեծացնում են ՓԱԹՉ֊ը։ Հետ
համատեղելի հավելումները և փոփոխությունները մեծացնում են ՄԻՆՈՐ֊ը, հետ
համատեղելիությունը խախտող փոփոխությունները մեծացնում են ՄԱԺՈՐ֊ը։

Ես անվանել եմ այս համակարգը «Սեմանտիկ տարբերակում» (Semantic Versioning): Այս
սխեմայի միջոցով տարբերակի համարը և դրա փոխվելը իմաստավորում են կոդի
պարունակությունը և նրանում եղած փոփոխությունները տարբերակից տարբերակ։

Սեմանտիկ տարբերակման սպեցիֆիկացիա (SemVer)
------------------------------------------

Նշված բառերը՝ «ՊԵՏՔ Է» (MUST, SHALL), «ՉՊԵՏՔ Է» (MUST NOT, SHALL NOT),
«ՊԱՐՏԱԴԻՐ Է» (REQUIRED), «ԱՆՀՐԱԺԵՇՏ Է» (SHOULD), «ԱՆՀՐԱԺԵՇՏ ՉԷ» (SHOULD NOT),
«ԽՈՐՀՈՒՐԴ Է ՏՐՎՈՒՄ» (RECOMMENDED), «ԿԱՐՈՂ Է» (MAY) և «ՊԱՐՏԱԴԻՐ ՉԷ» (OPTIONAL)
պետք է ինտերպրիտացվեն [RFC 2119](http://tools.ietf.org/html/rfc2119) ստանդարտին
համապատասխան։

1. Ծրագրային ապահովումը, որն օգտագործվում է Սեմանտիկ տարբերակում, ՊԵՏՔ Է (MUST)
   հայտարարի հասանելի փաբլիք API: Այդ API֊ը կարող է հայտարարվել ինչպես կոդի մեջ,
   այնպես էլ՝ առանձին դոկումենտացիայում։ Երկու դեպքում էլ այն պետք է լինի ճշգրիտ
   (precise) և սպառիչ (comprehensive)։

1. Տարբերակի ՆՈՐՄԱԼ համարը (normal version) ՊԵՏՔ Է (MUST) ունենա այս ֆորմատը՝
   X.Y.Z, որտեղ X, Y և Z թվերը ոչ բացասական ամբողջ թվեր են և ՉՊԵՏՔ է (MUST NOT)
   սկսվեն զրոյով։ X֊ը տարբերակի ՄԱԺՈՐ համարն է, Y֊ը՝ ՄԻՆՈՐ և Z֊ը՝ ՓԱԹՉ։ Բոլոր
   բաղադիրչները պետք է մեծացվեն թվայնորեն․ օրինակ՝ 1.9.0 -> 1.10.0 -> 1.11.0։

1. Փեքիջի թողարկումից հետո այդ տարբերակի պարունակությունը ՉՊԵՏՔ է (MUST NOT)
   փոփոխության ենթարկվի։ Ցանկացած փոփոխություն ՊԵՏՔ Է (MUST) թողարկվի որպես նոր
   տարբերակ։

1. Զրոյական ՄԱԺՈՐ տարբերակը (0.y.z) նախատեսված է ծրագրային ապահովման
   ստեղծման/մշակման նախնական փուլի (initial development) համար։ Ամեն ինչ կարող է
   փոխվել՝ կամայական պահի։ Փաբլիք API֊ը չպետք է դիտարկվի որպես ստաբիլ։

1. 1.0.0 տարբերակի թողարկումից հետո API-ը համարվում է ստաբիլ, և տարբերակի համարը
   փոխվում է կախված նրանից, թե ինչպես է փոխվում փաբլիք API֊ը։

1. Տարբերակի ՓԱԹՉ համարը՝ Z (x.y.Z | x > 0), ՊԵՏՔ Է (MUST) մեծացվի, եթե տեղի են
   ունեցել միայն հետ համատեղելի սխալների ուղղումներ (bug fix)։ Սխալի ուղղում՝
   նշանակում է ներքին փոփոխություն, որը ուղղում է սխալ պահվածքը։

1. Տարբերակի ՄԻՆՈՐ համարը՝ Y (x.Y.z | x > 0), ՊԵՏՔ Է (MUST) մեծացվի, եթե փաբլիք
   API֊ում ավելացել է նոր հետ համատեղելի ֆունկցիոնալ։ Տարբերակի համարը ՊԵՏՔ Է
   (MUST) մեծացվի, եթե հասանելի փաբլիք API֊ի որևէ ֆունկցիոնալ պիտակավորվել է
   որպես հնացած (deprecated)։ Տարբերակի համարը ԿԱՐՈՂ Է (MAY) մեծացվել, եթե տեղի
   է ունեցել նոր ֆունկցիոնալի ինտեգրացիա, կամ զգալի բարելավումներ են տեղի
   ունեցել փրայվիթ կոդում։ Այն ԿԱՐՈՂ Է (MAY) նաև պարունակել ՓԱԹՉ մակարդակի
   փոփոխություններ։ Տարբերակի ՓԱԹՉ համարը ՊԵՏՔ Է (MUST) զրոյացվի, երբ մեծացվում
   է ՄԻՆՈՐ համարը։

1. Տարբերակի ՄԱԺՈՐ համարը՝ X (X.y.z | X > 0), ՊԵՏՔ Է (MUST) մեծացվի, եթե փաբլիք
   API֊ում ներկայացվել են հետ համատեղելիությունը խախտող կամայական
   փոփոխություններ։ Այն ԿԱՐՈՂ Է (MAY) պարունակել նաև ՓԱԹՉ և ՄԻՆՈՐ մակարդակի
   փոփոխություններ։ Տարբերակի ՓԱԹՉ և ՄԻՆՈՐ համարները ՊԵՏՔ Է (MUST) զրոյացվեն,
   երբ մեծացվում է ՄԱԺՈՐ համարը։

1. Մինչթողարկումային (pre-release) տարբերակը ԿԱՐՈՂ Է (MAY) պիտակավորվել
   տարբերակի ՓԱԹՉ համարից անմիջապես հետո գծիկ և դրան հետևող կետիկով առանձնացված
   տարբեր իդենտիֆիկատորներ ավելացնելու միջոցով։ Իդենտիֆիկատորները ՊԵՏՔ Է (MUST)
   պարունակեն միայն ASCII տառա֊թվային սիմվոլներ և գծիկ՝ [0-9A-Za-z-]։
   Իդենտիֆիկատորները ՉՊԵՏՔ Է (MUST NOT) լինեն դատարկ։ Թվային իդենտիֆիկատորները
   ՉՊԵՏՔ Է (MUST NOT) սկսվեն զրոյով։ Մինչթողարկումային տարբերակները ունեն ավելի
   ցածր ԿԱՐԳԱՎԻՃԱԿ, քան համապատասխան ՆՈՐՄԱԼ֊ները։ Մինչթողարկումային տարբերակը
   ցույց է տալիս, որ այդ տարբերակը ստաբիլ չէ և կարող է չբավարարել
   համատեղելիության պահանջները, որոնք նշված են համապատասխան ՆՈՐՄԱԼ տարբերակում․
   օրինակ՝ 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92։

1. Բիլդ֊մետատվյալները (build-metadata) ԿԱՐՈՂ ԵՆ (MAY) պիտակավորվել տարբերակի
   ՓԱԹՉ համարից կամ մինչթողարկումային տարբերակի իդենտիֆիկատորից անմիջապես հետո
   գումարման նշան և դրան հետևող կետիկով առանձնացված տարբեր իդենտիֆիկատորներ
   ավելացնելու միջոցով։ Իդենտիֆիկատորները ՊԵՏՔ Է (MUST) պարունակեն միայն ASCII
   տառա֊թվային սիմվոլներ և գծիկ՝ [0-9A-Za-z-]։ Իդենտիֆիկատորները ՉՊԵՏՔ Է (MUST
   NOT) լինեն դատարկ։ Բիլդ֊մետատվյալները ՊԵՏՔ Է (MUST) անտեսել տարբերակի
   ԿԱՐԳԱՎԻՃԱԿԸ որոշելիս այսինքն, եթե նույն ծրագրի երկու տարբերակները տարբերվում
   են միայն բիլդ֊մետատվյալներով, ուրեմն դրանք ունեն նույն ԿԱՐԳԱՎԻՃԱԿԸ․ օրինակ՝
   1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85։

1. ԿԱՐԳԱՎԻՃԱԿԸ (precedence) որոշում է, թե ինչպես է պետք համեմատել տարբերակները
   միմյանց հետ, երբ դրանք դասավորված են։ ԿԱՐԳԱՎԻՃԱԿԸ ՊԵՏՔ Է (MUST) հաշվել
   տարբերակի համարը՝ ՄԱԺՈՐ, ՄԻՆՈՐ, ՓԱԹՉ, և մինչթողարկումային իդենտիֆիկատորները
   բաժանելու միջոցով։ ԿԱՐԳԱՎԻՃԱԿԸ որոշելիս բիլդ֊մետատվյալները հաշվի չեն առնվում։
   ԿԱՐԳԱՎԻՃԱԿԸ որոշվում է ՄԱԺՈՐ, ՄԻՆՈՐ, ՓԱԹՉ տարբերակի համարները ձախից աջ
   թվայնորեն համեմատելու միջոցով․ օրինակ՝ 1.0.0 < 2.0.0 < 2.1.0 < 2.1.1։ Երբ
   ՄԱԺՈՐ, ՄԻՆՈՐ և ՓԱԹՉ տարբերակի համարները հավասար են, մինչթողարկումային
   տարբերակը ունենում է ավելի փոքր ԿԱՐԳԱՎԻՃԱԿ, քան ՆՈՐՄԱԼ տարբերակը․ օրինակ՝
   1.0.0-alpha < 1.0.0։ Երբ տարբերակների ՄԱԺՈՐ, ՄԻՆՈՐ և ՓԱԹՉ համարները հավասար
   են, ԿԱՐԳԱՎԻՃԱԿԸ ՊԵՏՔ Է (MUST) որոշել մինչթողարկումային տարբերակի միջոցով՝
   ձախից աջ կետով առանձնացված իդենտիֆիկատորները համեմատելով մինչև առաջին
   տարբերող իդենտիֆիկատոր գտնելը։ Մինչթողարկումային տարբերակները համեմատվում են
   տվյալ եղանակով՝ իդենտիֆիկատորները, որոնք կազմված են միայն թվերից, համեմատվում
   են թվայնորեն։ Տառեր և գծիկ պարունակող իդենտիֆիկատորները համեմատվում են
   տառացի՝ ASCII աղյուսակի հերթականությամբ։ Թվային իդենտիֆիկատորները միշտ
   ունենում են ավելի ցածր կարգավիճակ, քան ոչ թվայինները։ Մինչթողարկումային
   սիմվոլների մեծ քանակ ունեցող տարբերակը ունենում է ավելի բարձր կարգավիճակ, երբ
   համեմատվող իդենտիֆիկատորները նույնն են․ օրինակ՝ 1.0.0-alpha < 1.0.0-alpha.1 <
   1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 <
   1.0.0։

Բակուս֊Նոյերի սխեման SemVer֊ով ներկայացված տարբերակի համարների համար
--------------------------------------------------------------------

    <valid semver> ::= <version core>
                     | <version core> "-" <pre-release>
                     | <version core> "+" <build>
                     | <version core> "-" <pre-release> "+" <build>

    <version core> ::= <major> "." <minor> "." <patch>

    <major> ::= <numeric identifier>

    <minor> ::= <numeric identifier>

    <patch> ::= <numeric identifier>

    <pre-release> ::= <dot-separated pre-release identifiers>

    <dot-separated pre-release identifiers> ::= <pre-release identifier>
                                              | <pre-release identifier> "." <dot-separated pre-release identifiers>

    <build> ::= <dot-separated build identifiers>

    <dot-separated build identifiers> ::= <build identifier>
                                        | <build identifier> "." <dot-separated build identifiers>

    <pre-release identifier> ::= <alphanumeric identifier>
                               | <numeric identifier>

    <build identifier> ::= <alphanumeric identifier>
                         | <digits>

    <alphanumeric identifier> ::= <non-digit>
                                | <non-digit> <identifier characters>
                                | <identifier characters> <non-digit>
                                | <identifier characters> <non-digit> <identifier characters>

    <numeric identifier> ::= "0"
                           | <positive digit>
                           | <positive digit> <digits>

    <identifier characters> ::= <identifier character>
                              | <identifier character> <identifier characters>

    <identifier character> ::= <digit>
                             | <non-digit>

    <non-digit> ::= <letter>
                  | "-"

    <digits> ::= <digit>
               | <digit> <digits>

    <digit> ::= "0"
              | <positive digit>

    <positive digit> ::= "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

    <letter> ::= "A" | "B" | "C" | "D" | "E" | "F" | "G" | "H" | "I" | "J"
               | "K" | "L" | "M" | "N" | "O" | "P" | "Q" | "R" | "S" | "T"
               | "U" | "V" | "W" | "X" | "Y" | "Z" | "a" | "b" | "c" | "d"
               | "e" | "f" | "g" | "h" | "i" | "j" | "k" | "l" | "m" | "n"
               | "o" | "p" | "q" | "r" | "s" | "t" | "u" | "v" | "w" | "x"
               | "y" | "z"