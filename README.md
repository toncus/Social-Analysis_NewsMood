3 Trends to take notice of
CBS tweet were the most positive of all news organizations, yet they came in at an unimpressive mean score of 0.3355.
The only other news organization that had a mean positive score was BBC with 0.0679.
CNN, Fox News and NYTimes had mean score that all seemed to cross slightly into negative territory.
Dependencies

1
# Dependencies
2
import tweepy
3
import json
4
import pandas as pd
5
import matplotlib.pyplot as plt
6
from datetime import datetime
7
from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer
8
analyzer = SentimentIntensityAnalyzer()
9
import datetime as dt 
10
import matplotlib.patches as mpatches
11
import os
12
import numpy as np
Twitter API Keys

# Twitter API Keys
1
# Twitter API Keys
2
consumer_key = "QiXSjj5Jdr3rgST8mRefRaVU0"
3
consumer_secret = "2G1vw2GqzGg1iN0zKoR4EXzwRgnrSMRUfZviOdwlghOcJwikVo"
4
access_token = "936508446-Y4rpk0TmJsgH1s35Ot2qdJy2yidK9zNGjPvBxa6v"
5
access_token_secret = "ZhosHPGiHkY1h7vDgr14nk4cmPfJyDEqNO6nAUVmyKNg0"
Setup Tweepy API

1
# Setup Tweepy API
2
auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
3
auth.set_access_token(access_token, access_token_secret)
4
api = tweepy.API(auth, parser=tweepy.parsers.JSONParser())
News Organizations List

tweeting_newsorg
1
#BBC, CBS, CNN, Fox, and New York times.
2
newsorg_list = ['BBC','CBS','CNN','FoxNews','NYTimes']
3
tweets = []
4
tweeting_newsorg = []
5
tweet_time = []
Looping through tweets

1
#Looping through last 100 tweets for each news organization
2
for each in newsorg_list:
3
    all_tweeting = api.user_timeline(screen_name = each, count = 100)
4
    for tweet in all_tweeting:
5
        print(each + ": " + tweet['text'])
6
        tweets.append(tweet['text'])
7
        tweet_time.append(tweet["created_at"])        
8
?
9
        tweeting_newsorg.append(each)  
BBC: Could this be an answer to global water shortages? ???? This machine creates water out of thin air. 

https://t.co/caz4nXMJg5
BBC: Tonight, @regyates meets people whose lives have been devastated by the Grenfell fire. 

Reggie Yates: Searching fo… https://t.co/HPgtcZuHte
BBC: Tonight, @mcgregor_ewan and @McgColin celebrate the centenary of the Royal Air Force. 

RAF at 100 with Ewan and Co… https://t.co/nF2iwBP51b
BBC: The first ever statue of David Bowie has been unveiled in the town where he debuted Ziggy Stardust. ??… https://t.co/lFgROYVkv1
BBC: When you're enjoying being single and people just can't deal with it. ???? @kathbum #LiveAtTheApollo 

https://t.co/byHMHWyhPq
BBC: ?????????? Welcome to Tangier Island, the tiny US island where people speak with a British accent.… https://t.co/1RoM285gRJ
BBC: ?? We could listen to him speak all day. 

?? Sir David Attenborough's voice was just as iconic in the 60s as it is t… https://t.co/zYi3oK5C13
BBC: Predictions suggest a build-up of about 80,000 tonnes of plastic in the Pacific Ocean is growing rapidly. ??????… https://t.co/uKD9BQWmUi
BBC: ????? @prattprattpratt stars as a happy-go-lucky hero who joins forces with an unlikely group of aliens. 

Guardians… https://t.co/B9W7kRZ1Qz
BBC: Weighing just 100g, a newborn panda is one 900th the size of its mum! ???? #DavidAttenboroughsNaturalCuriosities https://t.co/nKLQh03DJs
BBC: ??Meet SoFi - the soft robot fish developed by MIT to swim among real fish in coral reefs and around the ocean to he… https://t.co/HDa7q7WsHf
BBC: Ever wondered what made you feel moody? It might be your gut.

?? https://t.co/l8oMv5gPN2 https://t.co/vq2yhtBOAn
BBC: RT @BBCScotland: Up your brunch game with perfect poached eggs.

via @bbcthesocial https://t.co/1imXNeOZ9d
BBC: RT @bbcweather: #Winter may not be done with us yet, as colder continental air fights back against milder maritime air across the UK this w…
BBC: RT @BBCSport: A simply astonishing confession from Australia captain Steve Smith and batsman Cameron Bancroft ?? https://t.co/YaE7fBZamq
BBC: A woman who drinks 30 cans a day says her addiction to energy drinks is worse than gambling.… https://t.co/d11ATW0F0f
BBC: You learn something new every day. Here's how to poo a baby jaguar. ????#BigCatsAboutTheHouse https://t.co/Eg5rF1414b
BBC: When the clocks have gone forward but there's no way you're getting out of bed yet. ??????#DaylightSavings https://t.co/cHBPV3ITsQ
BBC: "I still see people screaming for help."

This Sunday at 9pm on @BBCTwo, @REGYATES meets the people whose lives wer… https://t.co/RS16yXF17H
BBC: The story of the last decade of Picasso's life, through the words of family and friends. ??

Picasso's Last Stand |… https://t.co/RyiuI8KgSk
BBC: "Beauty is your inside, it's your personality and what shines from beneath." 

25-year-old rapper Paigey Cakey had… https://t.co/CVGr69Y0oO
BBC: Cambridge have won the men's and women's Boat Races. https://t.co/COTzXYuo4N ?? ?? #BoatRace2018 https://t.co/6SQjF1ToSt
BBC: ???? @RomeshRanga is NOT a fan of Gogglebox. #LiveAtTheApollo
https://t.co/FHm9g6Emss
BBC: When proposals go wrong... ???? #Doodlebugs 
https://t.co/8Yi6giWO3S
BBC: Writer Sara Maitland has lived alone in rural Scotland for 20 years. 

Here are seven valuable life lessons we can… https://t.co/2eAqUlnwuA
BBC: ??How an Instagram video lost me my dream job in fashion: https://t.co/72yWgHdc1k https://t.co/fl3DxMcIL5
BBC: ?? @clarebalding is live from the River Thames as @UniofOxford and @Cambridge_Uni  meet for one of the most iconic e… https://t.co/Ls9rtIYov4
BBC: RT @bbcthree: The barber helping men with dementia relive their younger lives. https://t.co/p8axQVK836
BBC: Which animals are likely to become extinct in your lifetime? ????
https://t.co/9KwlmcNrWV
BBC: Don't miss the highlights from the Gymnastics World Cup! ???????????

World Cup Gymnastics | @BBCOne | 2:05pm |… https://t.co/7mpufyeEMo
BBC: How much do you know about horses? Take this quiz to see if you are an equestrian expert…??

https://t.co/ChGCB9Xi1W https://t.co/P9UgJ99nsx
BBC: Meet Hester, the 10-year-old visually impaired skier who's hoping for Paralympic gold one day. ???https://t.co/6aiUaTc3yS
BBC: "The enthusiastic viewer should feel he is almost the man on the spot!" 

In 1949, the BBC announced it would telev… https://t.co/WEoPpkrW1V
BBC: RT @BBCNewsNI: Prince Harry and Meghan Markle are visiting Northern Ireland https://t.co/ODxLd1LIr8 https://t.co/s0zPTXj3Tk
BBC: RT @bbcf1: Lewis Hamilton took the first pole of the season in spectacular style ??

https://t.co/a7YDOx0FlQ
BBC: RT @sportrelief: A humongous THANK YOU to everyone who has taken part, fund-raised &amp; watched over the past weeks &amp; tonight. The #SportRelie…
BBC: RT @sportrelief: The nation has joined together for this year's #SportRelief pulling out all the stops to make their steps count. Well done…
BBC: ??A Cultural history of the avocado: https://t.co/jo1UyWlVw7 https://t.co/7VF6pBpG57
BBC: Meet Alexandre, one of the only male performers of ‘baladi’ – also known as belly dancing – in the Middle East. ??

 https://t.co/K12N1Y6PU7
BBC: RT @BBCOne: .@GaryLineker, @OreOduba, @ThisisDavina &amp; more kick off the biggest ever night of #SportRelief now on @bbcone. @sportrelief 
Fo…
BBC: From @taylorswift13 to @Beyonce: these are the secretive musicians who avoid interviews. ???? https://t.co/nqOmaVMzoo https://t.co/sbDga7L5cp
BBC: Tonight, @GaryLineker, @ThisisDavina and @OreOduba kick off the biggest ever night of @sportrelief! ????????… https://t.co/tgbpC76heP
BBC: Your week, as told by @louistheroux. ????
https://t.co/Ae6bDBpIBW
BBC: RT @BBCWales: A #DanceForParkinsons session with @ndcwales for @GetCreativeUK in #Cardiff this week 

Find out what’s happening on the fina…
BBC: Meet Australian maths teacher Eddie Woo, who has won fans worldwide with his high-energy lessons, posted on YouTube… https://t.co/vTfNDZzA3b
BBC: RT @BBCOne: No @andy_murray, this is not a dream. @GeriHalliwell really IS in your bedroom making you sing Spice Girls songs ??

@sportrelie…
BBC: These beautiful photographs reveal how refugees in Tyneside have turned to the healing powers of gardening. ????… https://t.co/2gq0t9FnIR
BBC: How would you react if you woke up and found Michael McIntyre and Peppa Pig in your bedroom? 

Poor @AndyMurray…

S… https://t.co/7ZP0hUYeKr
BBC: Spring is here! ?????? Make the most of seasonal ingredients with these delicious soup recipes. https://t.co/fXp7eJXoJc https://t.co/hA1b2bdSrd
BBC: Want to get creative this weekend? Here's how to make a hooky rug. 
#MakeCraftBritain 
https://t.co/uqibyP09s7
BBC: RT @BBCSport: He was one of English football's first black players and the British Army's first ever black officer to command white troops.…
BBC: RT @BBCRadio2: ?? “I thought the script was really frightening and original.” Martin Freeman chats to @achrisevans about his creepy new film…
BBC: RT @BBCTwo: Our entire weekend plans. ???? #BigCatsAboutTheHouse https://t.co/vl0zUcCdmI
BBC: RT @sportrelief: It looks like #TeamGryffindor are storming ahead in the #HogwartsLeague in the #SportRelief app. 

#TeamHufflepuff, #TeamS…
BBC: ????Some blueberry muffins sold by cafes and supermarkets contain more than the recommended daily intake of sugar fo… https://t.co/9bh6K8aMH2
BBC: Friday night is CELEBRITY FIGHT NIGHT! ????

Who'll be victorious? Tune in to #SportRelief to find out!

https://t.co/9ZhgNGmxOD
BBC: Scrolling through headlines, the world can feel like a pretty dark place. So here are nine reasons to be happy. ?? ??… https://t.co/KrNoB0qaqC
BBC: Would you want secret helpers like these to help you out in nerve-wracking situations? #TheSecretHelpers 
https://t.co/ua2X4vxKR3
BBC: Meet the first polar bear cub to be born in the UK in 25 years. ??
https://t.co/njq1r6eONE
BBC: RT @BBCOne: All hail queen Kat! ???? 

#EastEnders @BBCEastenders https://t.co/PLmAc53L6t
BBC: Istanbul's Blue Mosque looks spectacular. @wmarybeard looks at the art, meaning and significance of calligraphy the… https://t.co/Mv3voUkcvc
BBC: ?? The artist reimagining Islamic calligraphy for the 21st Century: https://t.co/wgbVwZLDEa #Civilisations https://t.co/nxW6Sokjdn
BBC: In 1918, the very first signs of the Spanish Flu pandemic were kept under wraps. So how did the deadly illness get… https://t.co/zuZryXLihL
BBC: Go behind-the-scenes at @TheBigCatSanct where expert Giles Clark is hand-rearing a jaguar cub. ??… https://t.co/0hDQP6X1wA
BBC: Tai chi has been recommended to help people with the chronic pain condition fibromyalgia. 

https://t.co/uYDlKfWbt7 https://t.co/Y7P9ceP82j
BBC: The cost of living alone, rather than living as a couple, is more than £1000 a year. ????

This is the price of being… https://t.co/udzI9xGci6
BBC: .@ManUtd have applied to have a professional women's team. ?? https://t.co/rxzdRsDhUd https://t.co/meO65NRCtm
BBC: Worried about your impact on the planet? ????

This is how to make your next holiday more eco-friendly. ????

??… https://t.co/wCmDZJledV
BBC: Think twice before you throw your kitchen waste in the bin! Here's how to grow plants from kitchen scraps. ??????

??… https://t.co/MMgrC8yseG
BBC: RT @mixital: ???New #DoctorWho writing challenge!???
Write a story featuring Rory Williams! Share it with us here: https://t.co/zW42ZnvJnc

#…
BBC: Could you name the disaster that killed the most people in the last 100 years?

Contagion! The BBC Four Pandemic |… https://t.co/10zHfD8PHT
BBC: ??Some musicians love doing them, others don’t.

Seven secretive musicians who like to avoid interviews:… https://t.co/7Rm55Ddynj
BBC: RT @BBCEarth: Today is #WorldWaterDay. This teen has an ingenious way to test the safety of water around the world 
@BBC_Future https://t.c…
BBC: Has @chrishughes_22 read any of his own book? ????

Here's what he confessed when he took on @BBCR1's fake lie detect… https://t.co/tVaKesbKQ1
BBC: Secret Universe: The Hidden Life of the Cell is on @BBCFOUR tonight at 8pm. ?? https://t.co/PVf4thZOb3
BBC: A battle is raging in your body right now. This is how the TRIM 21 protein defends your cells from viruses. https://t.co/XUAPbRS4j5
BBC: ????Footloose, Fleetwood Mac's Rumours and Le Freak are among the classic records about to enter the US National Reco… https://t.co/gDLNOmNLhY
BBC: Meet the five artists who have been shortlisted for the £30,000 Hepworth sculpture award. https://t.co/1UGe2zQlDT https://t.co/MwWxUZWAhs
BBC: RT @bbcwritersroom: Check out an interview with the #writer of #TheAssassinationofGianniVersace @tomrobsmith on our blog
https://t.co/m5rty…
BBC: RT @bbcthree: 'I was the only female in a violent all-male gang' https://t.co/NjF720J71M https://t.co/k7T0PqyuiG
BBC: ??Can social media stop you getting a job? https://t.co/M9uTa8vMHA https://t.co/LwXJCGgW0b
BBC: RT @bbcpress: 50 classic cookery shows served up on @BBCiPlayer this Easter: https://t.co/RbyjFq6Dsj https://t.co/Hvt1m1dhpU
BBC: Come on, who doesn't say "xylophone" on a daily basis? ????@daraobriain #LiveAtTheApollo

https://t.co/5k1yKuwpzA
BBC: Tantrums are inevitable... ????This is how you raise a baby jaguar. #BigCatsAboutTheHouse

https://t.co/4mBf6xmvOr
BBC: RT @BBCSport: John Bishop’s on a one man mission to World Cup victory for @SportRelief!

Keep an eye out here for Geoff Hurst's 'dab' ??????…
BBC: "I felt vulnerable but now I feel empowered.”

25-year-old rapper Paigey Cakey had a hair transplant after her hair… https://t.co/fGoueTbzyQ
BBC: Watch as @ZoeTheBall attempts to cycle over 300 miles, to raise awareness about mental health and raise money for… https://t.co/qGcCT8wLSt
BBC: Who were my parents - and why was I left on a hillside to die? 

After a life full of questions, Anthea finally has… https://t.co/5fEma0vgfw
BBC: ????You really can't go wrong with a recipe from Mary Berry. 

????? Here are some of @BBCFood's favourites. ??… https://t.co/svyK73KV0o
BBC: Is it too late to save the oceans from plastic? ??

Go behind the scenes of the documentary Sir David Attenborough c… https://t.co/SjXbB6OZAN
BBC: RT @bbcmusic: Anne-Marie, Kylie Minogue, Ladysmith Black Mambazo and more have been added to the lineup for The Queen's Birthday Party conc…
BBC: Fictional locations such as Narnia, Gotham City and Neverland have mysteriously appeared on road signs in Oxfordshi… https://t.co/3NzQqfNNux
BBC: ?? Did you know that @DBtodomundo was asked to leave his school choir? 

?? Here are 11 things we learned from the Ta… https://t.co/tusEZQgIbG
BBC: What did students think when the BBC transported them to places they never thought possible? #ForReal… https://t.co/KFgZaE3PXi
BBC: Almost 1,000 sausage dogs have taken part in a dachshund dash! ???????

https://t.co/SMYaziJUrq
BBC: Ruben is a star of @cbbc's #TheDumpingGround and has Down's Syndrome.

Growing up with a disability could have been… https://t.co/lNo1Pa2wTu
BBC: The annual Marmalade Festival held at the weekend is one of the UK's many festivals dedicated solely to a particula… https://t.co/I75Ufx17Gq
BBC: Spring has officially sprung! ??????????

https://t.co/fAZSeVV8Oo
BBC: "I've just had a haircut so I now look ninety-nine-and-a-half!" ???????

A 100-year-old called Sadie has shared the s… https://t.co/X9QbWw0Ey0
BBC: RT @BBC_Teach: On #WorldPoetryDay let us know which your class’ favourite poem and/or poet?

Is it one of these? ???? https://t.co/qtn7IPXDFH…
CBS: Don’t miss a minute of the action. Stream the Elite Eight® games LIVE today starting at 2PM ET with a FREE trial of… https://t.co/8NwU8HdiHR
CBS: RT @MomCBS: That's a wrap on the #Mom panel at #PaleyFest! Thanks for following along! https://t.co/we4JgqPt6P
CBS: RT @MomCBS: A fan just commented that #Mom helped bring him out of a deep depression. ?????? #PaleyFest
CBS: RT @MomCBS: "Go out for it anyway. If you're good for the role, you're good for the role." @theJaimePressly's advice for aspiring actors wi…
CBS: RT @MomCBS: Mom Co-Creator @GemmaRBaker just pointed out her own #Mom in the audience at #PaleyFest! ??
CBS: RT @MomCBS: "I'm not someone in recovery who goes to AA, but I have taken so much away from it...to take one day at a time." - @theJaimePre…
CBS: RT @MomCBS: "You get to appreciate working with such talented people." - @AnnaKFaris #Mom #PaleyFest
CBS: RT @MomCBS: “I love this job. I love working with these women. I love working in front of the live audience… It’s alive and it’s fun.” - @A…
CBS: Get on your feet for @Jason_Aldean, @ThomasRhett, @ChrisStapleton, @KeithUrban, and @ChrisYoungMusic, the five nomi… https://t.co/oT5ogjdj4x
CBS: Get ready for some sweet games! Stream #5 Clemson vs #1 Kansas LIVE at 7PM ET and #11 Syracuse vs #2 Duke LIVE at 9… https://t.co/4WstgrKNnW
CBS: RT @SEALTeamCBS: In honor of #NationalPuppyDay... ?? #SEALTeam https://t.co/4mIZPpiRlU
CBS: RT @HawaiiFive0CBS: Nothing like a man and his dog! ???? Happy #NationalPuppyDay to Eddie, the best pup on the Five-0 Task Force! #H50 https:…
CBS: Game on! 16 teams left and the race to the finish continues tonight. Stream #11 Loyola-Chicago vs #7 Nevada LIVE at… https://t.co/W374rmzzoC
CBS: Save the date! These are season finales you do NOT want to miss. RT if you're excited! https://t.co/UUQoWsPPSh https://t.co/cDl4WmxMtU
CBS: Congratulations to all of the @CBSDaytime nominees for the #DaytimeEmmys! See the full list of #DaytimeEmmy nominee… https://t.co/ivJVJWvfsf
CBS: Female Vocalist Of The Year nominee @MarenMorris will show her fans how it’s done when she takes the stage to showc… https://t.co/PITjmAoFT8
CBS: The legendary @Reba returns to host the 53rd #ACMawards and she’s proving just how comfortable she is behind the mi… https://t.co/XPXcSPRXqC
CBS: RT @nancyodell: Told my daughter I'd be presenting at @ACMawards again this year. (Woot woot!We both luv country music!)She took this pic o…
CBS: RT @ladyantebellum: Ecstatic to announce we'll be performing at the #ACMawards in Las Vegas again this year! https://t.co/Qfhs94j6FR
CBS: Country superstars @kennychesney, @ladyantebellum, @blakeshelton, and @KeithUrban have just been added to the stell… https://t.co/bJ4If7MacP
CBS: RT @YandR_CBS: Forever evolving, Forever inspiring, Forever Young and Restless. ?? Get ready to celebrate 45 years of #YR starting in just…
CBS: New start times in East/Central Time Zones: #60Minutes 7:37ET/6:37CT #Instinct series premiere 8:37ET/7:37CT… https://t.co/xT3YKqmu2M
CBS: Spend your Sunday streaming Second Round games LIVE with a FREE trial of CBS All Access! https://t.co/3P85rXLy4b https://t.co/zbWfirD9Ju
CBS: RT @instinctcbs: TONIGHT, Dr. Dylan Reinhart rewrites the book on abnormal behavior. Don't miss the premiere of #Instinct at 8/7c! https://…
CBS: If any duo knows how to rock the stage, it's @FLAGALine. The Vocal Duo Of The Year nominee will perform live at the… https://t.co/FknabB8NQp
CBS: How is your bracket looking after last night? Stream Second Round games LIVE today with a FREE trial of CBS All Acc… https://t.co/25JlIpgwog
CBS: Where better to spend #StPatricksDay than the place everybody knows your name? It’s just your luck that every singl… https://t.co/Fom5wmdENL
CBS: Stars @JakeMcDorman and Nik Dodani will join the cast in the upcoming revival of Murphy Brown coming to CBS.… https://t.co/JCAx29lo0i
CBS: RT @thegoodfight: Go behind the scenes with costume designer @DanLawsonStyle in "Behind The Style," a new weekly video series all about the…
CBS: The games have just begun! Continue to stream First Round games LIVE today with a FREE trial of CBS All Access:… https://t.co/YTGsJ48zYP
CBS: RT @TheTalkCBS: You asked, we answered! The fun never ends when the ladies #KeepTalking and answer your fan questions ?????? https://t.co/ie1…
CBS: RT @instinctcbs: Dr. Dylan Reinhart is lured back into the field from his life of quiet academia when a certain serial killer makes things…
CBS: Stream First Round games LIVE today starting at 12PM ET with a FREE trial of CBS All Access! https://t.co/3P85rXLy4b https://t.co/vZow3YD8cb
CBS: RT @CBSSports: It's the most wonderful time of the year. #MarchMadness https://t.co/e4c9qohqSR
CBS: Give these ladies some love! @Lauren_Alaina, @DBradbery, @carlypearce, and @RaeLynn are nominated for New Female Vo… https://t.co/IVhwURfJ3S
CBS: RT @ManWithAPlan: Hungry for more #ManWithAPlan bloopers and behind-the-scenes videos featuring cast like @matt_leblanc, @thelizasnyder, @k…
CBS: Music stars @MileyCyrus, @edsheeran, @ladygaga, and more will honor the legendary @eltonofficial and his hit songs… https://t.co/UzxARCCLnI
CBS: RT @thegoodfight: The verdict is in. The new season of #TheGoodFight is ??????! Stream it now on CBS All Access: https://t.co/FkYSNSXlRb https…
CBS: RT @MadamSecretary: In less than an hour, #MadamSecretary's Keith Carradine will be taking over the @MadamSecretary Twitter page! Tweet alo…
CBS: RT @DierksBentley: Take and post a photo of the woman in your life who inspires you daily! Use the hashtag #WomanAmenACM in your post for a…
CBS: RT @MomCBS: If you missed guest star @KChenoweth in the latest episode of #Mom, not to worry! Watch now: https://t.co/RlvXoGOZ0l https://t.…
CBS: Give a round of applause to @KelseaBallerini, @MirandaLambert, @Reba, @MarenMorris, and @CarrieUnderwood, the five… https://t.co/Ncp1BTXx6N
CBS: RT @thegoodfight: Smart, sexy, and sophisticated. See what's coming this season on #TheGoodFight. https://t.co/CuKhx2G50P https://t.co/ygTI…
CBS: RT @BlueBloods_CBS: Even stand-up guys fall down sometimes. #BlueBloods is new tonight at 10/9c! https://t.co/UOlDm22wWW
CBS: Today and every day we celebrate the women in our lives who empower and inspire us. Share a story about an influent… https://t.co/9rVtqrElvT
CBS: Take and post a photo of the woman in your life who inspires you daily! Use the hashtag #WomanAmenACM in your post… https://t.co/7ShhvE48zy
CBS: RT @thegoodfight: Meticulously constructed. Soapy &amp; sexy. Intoxicating, savage television. ?? Here's what critics are saying about #TheGoodF…
CBS: This just in! @Jason_Aldean, @mirandalambert, @LukeBryanOnline, and many more are set to perform at the 53rd Academ… https://t.co/mfxw2VxzU4
CBS: Meet the ensemble of talented actors slated to join $1, a new mystery series coming to CBS All Access:… https://t.co/QoyYv7vxwg
CBS: Will @Jason_Aldean, @garthbrooks, @LukeBryanOnline, @ChrisStapleton, or @KeithUrban be named Entertainer Of The Yea… https://t.co/rMD8zjeX3s
CBS: RT @thegoodfight: It feels good to be back. ?????? The season 2 premiere of #TheGoodFight is now streaming, exclusively on CBS All Access: htt…
CBS: RT @thegoodfight: Tomorrow, #TheGoodFight is back. Stream the season 2 premiere only on CBS All Access: https://t.co/tNFR8LBJO2 https://t.c…
CBS: Who are the trailblazing women in your life that inspire you? Join CBS and the ANA's #SeeHer initiative, celebratin… https://t.co/M0KqZ41Bes
CBS: Join @maria_bello, @aishatyler and @TeaLeoni in celebrating the accomplishments of women who have contributed to th… https://t.co/MefESBeFL3
CBS: In honor of Women's History Month, CBS and the Association of National Advertisers' (ANA) #SeeHer initiative will p… https://t.co/2wtYxKJVuO
CBS: RT @ZoeListerJones: Tonight’s an all new Life In Pieces and it’s directed by my ride or die @nataliaanderson!!!… https://t.co/2LPfmyLWrY
CBS: RT @MarenMorris: Hot damn! Woke up from my post-wisdom teeth haze to find out I’m up for 4 @ACMawards ! So honored, especially for the Dear…
CBS: RT @KelseaBallerini: Ohhhhh goodness. Incredible. Thank you thank you thank you. #female https://t.co/1ZTYjNfQeF
CBS: RT @KeithUrban: ACMs...... HOLY SMOKES!!!!! MAD LOVE TO U ALL THIS MORNING  FOR THESE INCREDIBLE NOMINATIONS. I’M EXTREMELY GRATEFUL!!!!!!!…
CBS: RT @ACMawards: Congratulations to this year’s #ACMawards Video of the Year nominees:
“Black” - @DierksBentley
“It Ain’t My Fault” - @Brothe…
CBS: RT @ACMawards: Please give a round of applause to this year’s #ACMawards Entertainer of the Year nominees: @Jason_Aldean, @GarthBrooks, @Lu…
CBS: .@ChrisStapleton, @ThomasRhett, @mirandalambert and more are all nominated for awards at Country Music's Party of t… https://t.co/Vm1vXRUDYJ
CBS: The Queen of Country, @Reba, is returning to host the 53rd #ACMawards on Sunday, April 15 at 8/7c. Here are a few o… https://t.co/Iqzz6Gql01
CBS: RT @survivorcbs: It’s time! #Survivor https://t.co/YPk6cGWrUA
CBS: RT @CBSThisMorning: TOMORROW: The nominees for the 2018 @ACMawards will be announced live by the one-and-only, @Reba! 

Watch on @CBS in ou…
CBS: RT @thegoodfight: From the set design and costumes to hair and makeup, the production quality is truly next-level. Take a peek inside the u…
CBS: RT @LivinBiblically: The fun continues on Facebook! The #LivingBiblically cast is live to talk about tonight’s premiere. Tune in here: http…
CBS: RT @KevinCanWaitCBS: Can you get all the way through these #KevinCanWait bloopers without laughing?! @KevinJames,@LeahRemini and the rest o…
CBS: RT @ACMawards: That’s right! @Reba is headed to @CBSThisMorning on Thursday, March 1 to announce this year’s #ACMAwards' nominees. Tune in…
CBS: RT @ScorpionCBS: You can't hack your way to a 197 IQ, but you are well on your way with these Genius Facts from #TeamScorpion! ?? You can be…
CBS: RT @SuperiorDonuts: You can always count on @DavidKoechner for a laugh! Did your favorite Tush moment make the list? Catch a new #SuperiorD…
CBS: RT @TheTalkCBS: TODAY: We loved them together then &amp; we love seeing them together now! Welcome back to the show @THESaraGilbert?'s good fri…
CBS: RT @thegoodfight: As foundations begin to crumble, our characters struggle to make sense of this new dystopian world. The cast teases what'…
CBS: #LivingBiblically's @linzkraft and @jrfergjr appeared on @KCBS's Facebook Live this morning, talking all about what… https://t.co/4RebcHuuMQ
CBS: RT @CBSSports: Introducing CBS Sports HQ, a New 24/7 Direct-to-Consumer Streaming Network for Sports News, Highlights, &amp; Analysis.

Stream…
CBS: RT @CBSBigBrother: It’s down to the final 5 celebrity Houseguests, and anyone could take home the grand prize! Tune in NOW to watch the #BB…
CBS: RT @startrekcbs: Binge the entire first season of #StarTrekDiscovery. All episodes now streaming exclusively on CBS All Access: https://t.c…
CBS: RT @thegoodfight: #TheGoodFight returns in 1 week. Season 2 premieres Sunday, March 4. https://t.co/nomCao1GWp https://t.co/BOn6bOe9Tb
CBS: RT @thegoodfight: This is our new favorite thing. Christine Baranski debuted #TheGoodFight the Musical on @colbertlateshow last night! ????…
CBS: RT @LivinBiblically: Confession time: have YOU ever hit the "close door" button in an elevator while somebody was approaching? The cast of…
CBS: RT @CBSEyeSpeak: Mark your calendars! #CBSEyeSpeak kicks off March 14 with The EYE Speak Summit. Follow our page for more details! https://…
CBS: RT @CBSEyeSpeak: Proud to announce a new CBS initiative, promoting female empowerment and developing the next generation of leaders through…
CBS: RT @LivinBiblically: When you're living by the Bible, it's good to have a priest and a rabbi on call (provided they answer their phones, th…
CBS: RT @thegoodfight: Chicago lawyers are being hunted and the world is going insane. 

The new season of #TheGoodFight premieres Sunday, March…
CBS: Ready for some larger than life competition? This new series from @MarkBurnettTV will premiere in summer 2018.… https://t.co/gDXHLdIJ5v
CBS: With tournament dreams on the line, make sure to stream these college basketball matchups on CBS All Access:… https://t.co/SGkYUZrQWB
CBS: RT @LivinBiblically: While Chip's sticking to the Bible's original rules, the cast of #LivingBiblically has given them a more modern makeov…
CBS: Casting News! Peter Mark Kendall, Michael Gaston, Greg Wise, Rade Šerbedžija, Zack Pearlman, and Keye Chen join the… https://t.co/GFob2KrD8H
CBS: RT @BullCBS: The verdict is in...#Bull is the perfect Valentine! ?? Happy #ValentinesDay! https://t.co/poEejI4AnC
CBS: RT @NoActivityCBS: Car 27 reporting: Season 2 of #NoActivity coming soon!

Binge season one now on CBS All Access: https://t.co/yvxoQMeyhN…
CBS: RT @LivinBiblically: Against all odds (and the advice of his God Squad), Chip is determined to live life by the Good Book. Think you could…
CBS: RT @thegoodfight: Christine Baranski reflects upon the spectacular metamorphosis of her character in #TheGoodFight's first season. Revisit…
CBS: RT @startrekcbs: Binge the entire first season of #StarTrekDiscovery. All 15 episodes now streaming on CBS All Access: https://t.co/lKLaptP…
CBS: RT @SuperiorDonuts: Looking for a #Valentine? Tush is here to help you land your dream date just in time for the day of love! #SuperiorDonu…
CBS: RT @CBSBigBrother: The pressure is on as the Houseguests battle each other for victory in the first HOH competition. Stream the season prem…
CBS: RT @startrekcbs: Sunday, this season's epic journey reaches its final reckoning. Catch up before the season finale: https://t.co/4Ea5wpmAep…
CBS: Are you a sucker for jaw-dropping talent competitions? Announcing The World's Best, a first-of-its-kind new global… https://t.co/fagCMklm2Z
CBS: RT @BullCBS: Tonight, one of these 3 TAC employees will end up incarcerated. Who do you think it will be? Tune into a new episode of #Bull…
CBS: RT @thegoodfight: There's no season like lawyer season. #TheGoodFight returns March 4, exclusively on CBS All Access. https://t.co/XAlrg1nB…
CBS: RT @thegoodfight: The acclaimed series returns in 1 month. #TheGoodFight is back Sunday, March 4. https://t.co/5BNLTYRd8p https://t.co/yInP…
CNN: The key players in the Stormy Daniels scandal https://t.co/4k8CTDlFVi https://t.co/gOFDXmglmx
CNN: What happens when the world's two biggest economies turn on each other https://t.co/kGu99fYZvv https://t.co/JgzxQmVohv
CNN: Cabinet wives swept up in secretaries' woes https://t.co/gRHqqfoIly https://t.co/zlGvUYxnQS
CNN: Mark Warner, the top Democrat on the Senate Intelligence Committee, says Mark Zuckerberg needs to testify about Fac… https://t.co/QZBstaZDg1
CNN: "I hope. ... they know that there is light at the end of the tunnel."

CNN's Ed Lavandera followed a group of survi… https://t.co/OOo7eRjDKZ
CNN: Ohio Gov. John Kasich says politicians "should be held absolutely accountable at the ballot box" for their inaction… https://t.co/KHTlD7iUuh
CNN: A driver's dramatic rescue from his SUV was caught on camera as floodwaters came rushing through Santa Clarita, Cal… https://t.co/vP9wOndR4x
CNN: The marching students wowed this security mom https://t.co/nRBizoN4s5 | via @CNNOpinion https://t.co/OVjQzh5nq9
CNN: Why the Stormy Daniels interview should scare Republicans https://t.co/z6li30k8qv | via @CNNOpinion https://t.co/tIcn4gfX6Q
CNN: A day after March for Our Lives, the Pope urges youth to speak out https://t.co/MZxgyIY78e https://t.co/ntsRpwZN3L
CNN: "(President Trump) is either lying or he is completely delusional." Democratic Sen. Tim Kaine says Trump's blaming… https://t.co/faQhA18ng9
CNN: "If keeping our children's safe was truly Trump's 'top priority,' why did he play golf instead of attend the March… https://t.co/wt25Y1iJoZ
CNN: What we know about Emma Gonzalez, the fiercely outspoken teen who stunned America with her silence… https://t.co/KqUj4NlgjT
CNN: Ohio Gov. John Kasich says politicians "should be held absolutely accountable at the ballot box"… https://t.co/543rARLzMr
CNN: Russia in the headlines, and a tense meeting between world leaders about nuclear disarmament. Are the events of 196… https://t.co/PT4S6W2dmN
CNN: The Austin bomber called himself a "psychopath" in his confession video https://t.co/7h52eBFkiP https://t.co/umrIxGQrnh
CNN: Former Brexit volunteer alleges campaign "cheated" https://t.co/fCxTXOTDNK https://t.co/60a1wBlFba
CNN: A new heroine is flying alongside Wonder Woman and Superman to pull Puerto Rico through hurricane Maria's aftermath… https://t.co/w4mdgO6vMm
CNN: A former cancer patient is now a doctor at the hospital that helped her survive https://t.co/QpZ6HqzylV https://t.co/xWPV9fs5Vz
CNN: These New York police officers were outnumbered in this adorable snowball fight https://t.co/heByQBkT9a
CNN: There has been, on average, 1 school shooting every week this year https://t.co/WOw2gtl9hc https://t.co/CU9U4yCMhP
CNN: This robotic fish is designed to swim near real aquatic creatures and spy on them without raising suspicions or dis… https://t.co/RNhdKMTc4A
CNN: About half of all plants and animals in 35 of the world's most biodiverse places are at risk of extinction due to c… https://t.co/eZuNKpx4rK
CNN: Ohio Gov. John Kasich on former California Gov. Arnold Schwarzenegger calling for him to run for president in 2020:… https://t.co/UTWxFZYmcM
CNN: Ohio Gov. John Kasich says incoming national security adviser John Bolton should understand that "America "cannot b… https://t.co/KDokXGRpna
CNN: Ohio Gov. John Kasich on the March For Our Lives protests: “If they do not bring about change, I think people shoul… https://t.co/OILRSi8KRs
CNN: “He is either lying or he is completely delusional,” Sen. Tim Kaine says of President Trump blaming Democrats for f… https://t.co/6r895RQPep
CNN: Sen. Tim Kaine questions if President Trump’s new pick for national security adviser can get a security clearance:… https://t.co/RH2ORJTpW6
CNN: "The activism of these young people is actually changing the equation ... they're not going away," Sen. Tim Kaine s… https://t.co/LoTcR2u12c
CNN: An animatronic T .rex went up in flames at this dinosaur park in Colorado. The park says the blaze was caused by el… https://t.co/3Xs9dMEKY5
CNN: "Black Panther" is the the most-tweeted about movie of all time, Twitter says https://t.co/Ffh5z9Chys https://t.co/2hhcrpczIX
CNN: A Tennessee man who was wrongfully imprisoned for 31 years and initially given $75 to start over has been awarded $… https://t.co/Xxitou66Jv
CNN: Bank of America Merrill Lynch doctored paperwork on 16 million orders to fool institutional clients into thinking s… https://t.co/EW6uyUvuDd
CNN: Republican Rep. Ryan Costello will drop his bid for reelection in Pennsylvania https://t.co/2tYW2a6mrd https://t.co/8XKF9V45dE
CNN: Researchers finally solve mystery of "alien" skeleton https://t.co/Ymts1gegBE https://t.co/kBJpwYKGyC
CNN: In Sacramento and in Austin, black people just want this https://t.co/QY2mnt7vH1 | via @CNNOpinion https://t.co/NcbVhzuzYE
CNN: In a new memoir, Hillary Clinton's former campaign communications director says the email scandal was a like "a box… https://t.co/2qEKrRaoiP
CNN: This case shows why dog breeders need to be regulated, writes Randi Kaye for @CNNOpinion https://t.co/gqfOi4Kid4 https://t.co/VTIzke2a8c
CNN: China and the United States are on the brink of a trade war — and Apple chief Tim Cook is calling on the countries… https://t.co/emYdvRdY0y
CNN: I downloaded 14 years of my Facebook data and here's what happened https://t.co/CatT9piwSb https://t.co/iYlZLl8bkv
CNN: The lawyer President Trump wants to represent him has been dead for 32 years https://t.co/ZYSNTnMfcR https://t.co/zZ4nvZlPkT
CNN: Take a look at this week in politics https://t.co/kcprtfGNys https://t.co/l9sn1TwkeS
CNN: "I need allies." Fresh off a staggering loss for Republicans in Pennsylvania's deep-red 18th district, President Tr… https://t.co/Kx2Fm2p7mM
CNN: Tesla to slow shipments in Norway due to unsafe delivery trucks https://t.co/9JSC3KFih1 https://t.co/8ZXKLq1XNU
CNN: Australian beaches pose dangers to newcomers https://t.co/wv6ILLo3Lg https://t.co/esYlq0aT9m
CNN: Here's what you may have missed at the March for Our Lives rallies https://t.co/ja0geb22RQ https://t.co/aLQN2TqGJB
CNN: "I have a dream that enough is enough. And that this should be a gun-free world. Period." - Martin Luther King Jr.'… https://t.co/QNGeEGkvMM
CNN: Samantha Fuentes, who was wounded in the mass shooting at Marjory Stoneman Douglas High School, asks the crowd to j… https://t.co/dRFdWpk0QZ
CNN: These grandmothers in Texas have had enough of gun violence https://t.co/GrjeoktRf5 https://t.co/fZtTBJKT6V
CNN: George Clooney, Paul McCartney and more celebrities join March for Our Lives https://t.co/WabPC0OUEk https://t.co/EemR2GmHLv
CNN: Gun violence can happen to anybody, says singer Jennifer Hudson https://t.co/OADln4miDu https://t.co/sD7QJN9rUR
CNN: While others marched for their lives, these people marched for their guns https://t.co/GiGWjFDzG3 https://t.co/3TXIISsdi8
CNN: Some of the most powerful signs from the March for Our Lives https://t.co/DhbwVpMOlZ https://t.co/meFpCoHKht
CNN: World Trade Center glows orange for the March for Our Lives rallies https://t.co/xO7kt2NboP https://t.co/MFbYZhnw73
CNN: "Keep at it. You're leading us forward. Nothing can stand in the way of millions of voices calling for change." For… https://t.co/Amnd5zbDYL
CNN: 11-year-old Naomi Wadler says she speaks at Washington DC rally to "represent the African-American girls whose stor… https://t.co/WUwqmanlpW
CNN: "One of my best friends was killed in gun violence right around here, so it's important to me," says Paul McCartney… https://t.co/CZfsYBXMNL
CNN: "We cannot make America safe until we arm our teachers. ... with pencils, paper and the money they need. ... to sup… https://t.co/WLEW14rwG3
CNN: (??: Atilgan Ozdil/Anadolu Agency/Getty Images)
CNN: "One of my best friends was killed in gun violence right around here, so it's important to me." Former Beatle Paul… https://t.co/E03daVJ6L2
CNN: Gun violence victim Jennifer Hudson on the Parkland student campaigners: "I love so much that they're using their e… https://t.co/xDLiKm1KaY
CNN: Gun violence victim Jennifer Hudson on the Parkland student campaigners: "I love so much that they're using their e… https://t.co/hKkoALRNAL
CNN: "It's not easy to keep seeing. What is it gonna be next week? Next month?" an emotional Jennifer Hudson asks… https://t.co/YhNWMRaGfG
CNN: "For people who are watching ... know that it can be anybody ... to me, the saddest thing is, no one ever reacts un… https://t.co/mHXLxhqo6l
CNN: At the March for Our Lives rally in Washington, Parkland survivor Emma Gonzalez weeps quietly for the majority of h… https://t.co/vuywFdHAFE
CNN: “I kind of felt the pain that they (Parkland survivors) feel because at the end of the day it's not about who gets… https://t.co/L2m8gSb9yS
CNN: Reflecting on today’s March for Our Lives, Parkland survivor Samantha Fuentes tells Van Jones she was “terrified” b… https://t.co/e52P9eyCs9
CNN: GOP donor launches gun reform group to coincide with March for Our Lives https://t.co/xI1wPhNmGn https://t.co/N6AXZPFU8r
CNN: Why I march: People reveal what compelled them to join March for Our Lives https://t.co/KU2nQLcKIM https://t.co/L9UxYiqix2
CNN: Martin Luther King Jr.'s granddaughter addresses March for Our Lives in Washington: "I have a dream that enough is… https://t.co/jyXfB8onIg
CNN: Aerial footage shows the turnout at various March for Our Lives across the US today https://t.co/50KflY3S4X https://t.co/MVxCufnaIQ
CNN: "When politicians send their thoughts and prayers with no action, we say 'no more,'" says Parkland survivor David H… https://t.co/njlvsdWpd6
CNN: This Parkland shooting victim would have turned 18 today https://t.co/8Q3uetdopL https://t.co/arLlrW0Thl
CNN: "One of my best friends was killed in gun violence right around here, so it's important to me," says Paul McCartney… https://t.co/JJd58rPbiJ
CNN: This marcher is only 6. But as her sign says, so were the Sandy Hook victims. https://t.co/zKUpta5M60 https://t.co/yP4kxLeTjf
CNN: Those who couldn't attend the March for Our Lives — for health reasons or otherwise — found alternative ways to cal… https://t.co/3sdZyPtiFj
CNN: "We cannot make America safe until we arm our teachers. ... with pencils, paper and the money they need. ... to sup… https://t.co/VtPhBU4IZ8
CNN: Demonstrators have gathered in Washington DC and across the US to demand stricter gun laws. Follow along for live u… https://t.co/SCzfyryyAZ
CNN: When a gunman killed 26 at her school, Lauren Milgram, then just 6, hid in a bathroom. Now, the 12-year-old marched… https://t.co/3FKM9sWYq8
CNN: "I feel like I'm closer to being an adult than I should be at my age. I should be hanging out with my girlfriends,… https://t.co/HfoSzBM89B
CNN: Here's what the NRA had to say today about the March for Our Lives https://t.co/QLvGtGOar9 https://t.co/TMGtJd15hK
CNN: The Parkland kids keep checking their privilege https://t.co/uyUQ1yGJHo https://t.co/u6vVVHKwW1
CNN: This Parkland survivor threw up on stage and then finished her speech at the March for Our Lives rally in Washingto… https://t.co/0n4W9blvUI
CNN: Parkland school shooting survivor Emma Gonzalez stood on stage for 6 minutes and 20 seconds — the time it took the… https://t.co/53EVcEL3v7
CNN: Samantha Fuentes, who was wounded in the mass shooting at Marjory Stoneman Douglas High School, asks the crowd to j… https://t.co/0DfmSFip9b
CNN: These grandmothers in Texas have had enough of gun violence https://t.co/6u7JSeRtFn https://t.co/FiwF9BvIsS
CNN: This 6-year-old is marching in London today carrying a sign with the names of the victims of the 2012 Sandy Hook ma… https://t.co/JzyXgOHDkT
CNN: These politicians have weighed in on March for Our Lives rallies calling for stricter gun control… https://t.co/WDopvkFLH0
CNN: At the March for Our Lives rally in Washington, Florida school survivor Emma Gonzalez weeps quietly for the majorit… https://t.co/eYtm2kTleE
CNN: There's a large sign outside the capitol in Minnesota that says "ENOUGH" — one of the catchwords for those rallying… https://t.co/a0L6fBY1aM
CNN: "I have a dream that enough is enough. And that this should be a gun-free world. Period." - Martin Luther King Jr.'… https://t.co/ZCbCc1csZM
CNN: "Stand for us or beware — the voters are coming." Florida school shooting survivor Cameron Kasky gives an impassion… https://t.co/3LClliCYd1
CNN: "Keep at it. You're leading us forward. Nothing can stand in the way of millions of voices calling for change." For… https://t.co/NFiRsDTQhG
CNN: Here's why some of the March for Our Lives demonstrators are wearing $1.05 price tags https://t.co/iMH5IYTu2Z https://t.co/aJFIQsY2Gq
CNN: Here's what US lawmakers have done about gun control since the Parkland shooting https://t.co/lgxaZnrmO6 https://t.co/YaqSErD1e9
CNN: 11-year-old Naomi Wadler says she speaks at Washington DC rally to "represent the African-American girls whose stor… https://t.co/V4quaN3SJU
CNN: Alex Wind, a student at Marjory Stoneman Douglas High School, gives a passionate speech at the March for Our Lives… https://t.co/fzvj8i3Twn
CNN: "One of my best friends was killed in gun violence right around here, so it's important to me," says Paul McCartney… https://t.co/KIadLzcfFn
CNN: Are you a student taking part in today's March for Our Lives? Share your photos with CNN, along with your name, age… https://t.co/kihpHSkqPb
CNN: Martin Luther King Jr.'s granddaughter addresses March for Our Lives in Washington, DC: "I have a dream that enough… https://t.co/PyLJSuNE9C
FoxNews: .@DarrellIssa: "How do Republicans win? They win by not only embracing @POTUS but helping him go further." https://t.co/G24L1tqyi8
FoxNews: New Tavis Smiley witnesses detail sexual misconduct https://t.co/Krf1IVY13E
FoxNews: .@KimStrassel: "Whenever you're talking about regulating an organization like [@Facebook}, you are in essence talki… https://t.co/YSM7THzQzZ
FoxNews: .@JudgeJeanine Rips Ryan, McConnell: Your Omnibus Spending Package Is 'A Total Betrayal' of Trump
https://t.co/88ds6UHWN4
FoxNews: Trump administration backs UK after ex-spy poisoning, considers 'options' against Russia https://t.co/N0NZ36bxip
FoxNews: .@SecondLady and @charlipence talk to Chris Wallace about #MarlonBundoBook. https://t.co/3UqdgZ8A7k
FoxNews: #PalmSunday procession marks start of Holy Week https://t.co/B3rUP0w0AV
FoxNews: 30 of the 71 living Medal of Honor recipients receive an honor guard in New York before flying to Washington, to ma… https://t.co/dylF19nH3c
FoxNews: 'Maybe That's the Way to Run a Reality Show': Dem Sen Rips Trump, Says WH 'Chaos' Hurts America
https://t.co/ykPvj5gixy
FoxNews: Jason Miller on Russia investigation: "Right now the only one who's telling the story are President… https://t.co/SxejNkYzK4
FoxNews: On @WattersWorld, @DiamondandSilk sounded off about the @JoeBiden-@realDonaldTrump feud. https://t.co/QXi7utrBKu https://t.co/7sV3oKK6jg
FoxNews: State Rep. Susan Lynn: “’In God We Trust’ is a guiding principle for our nation.” https://t.co/Y1LSJgFwod https://t.co/Z1JA6oGQ1B
FoxNews: .@newtgingrich on Pompeo, @AmbJohnBolton: "They'll be going in the room saying [to @POTUS] how can we help get what… https://t.co/6vulhVudPs
FoxNews: .@stevenmnuchin1 on spending bill: "It was a difficult decision for the president, and I understand that, because t… https://t.co/GSPJZtfbFm
FoxNews: China's space station expected to hit Earth soon -- possibly in Europe https://t.co/ZdgOxvcFyU
FoxNews: Apple's Tim Cook calls for regulation on data, says Facebook incident is 'dire' https://t.co/Aog20fdyhj (via @christocarbone)
FoxNews: .@SecondLady: "The only thing better than one bunny book that benefits charity is two bunny books that benefit char… https://t.co/85O4vdgyCx
FoxNews: TONIGHT: 'Legends &amp; Lies' Returns With a Riveting Look at The Civil War - Hosted by Brian @Kilmeade, it all begins… https://t.co/9rpGvpUdpi
FoxNews: .@stevenmnuchin1 on China tariffs: "In a negotiation, you have to be prepared to take action. And that's what Presi… https://t.co/SErLJp0A1D
FoxNews: .@stevenmnuchin1: "This is a president that absolutely believes in free trade, but wants free and fair trade, and h… https://t.co/uAn0hJEc7h
FoxNews: .@DevinNunes: "We also found no collusion between the Trump campaign but we did find links between the Clinton [cam… https://t.co/D2LyvqOsSW
FoxNews: On "Cavuto Live," @cvpayne gave his take on the U.S.'s approach to economic competition from China.… https://t.co/m0gr5hCtGB
FoxNews: .@newtgingrich: "There are five cities in America that have most of the killings in America, five cities. All five… https://t.co/Q69jm2YyA2
FoxNews: Drunk man steals beef jerky from 7-Eleven, breaks into New York home and urinates on porch, cops say https://t.co/rxJ1amJw8H
FoxNews: .@delaneytarr: "We can never go back to school and feel the same that we once did. That’s just not a possibility an… https://t.co/cqO1H0wJF5
FoxNews: .@delaneytarr on Maryland school shooting: "I'm glad that that sheriff had a gun, because he is a person who should… https://t.co/IhNEAXgNkJ
FoxNews: .@cameron_kasky: "We are not just marching to end school violence. We are marching to end violence all over the cou… https://t.co/qYUNffCkYl
FoxNews: .@cameron_kasky on school safety: "There's no specific mental health problem that makes all these shootings happen,… https://t.co/6KHyUVsPKb
FoxNews: Fox News Poll: 45% approve of President @realDonaldTrump's job performance. https://t.co/xUdGnR4tgC https://t.co/yzbJdWMwsa
FoxNews: Florida's action on guns since the Parkland shooting. #FoxNewsSunday https://t.co/8Ax1ZJ3Ewf
FoxNews: National action taken on guns since the Parkland shooting. #FoxNewsSunday https://t.co/Pe8uHGSrf6
FoxNews: .@cameron_kasky on #MarchForOurLives: "The fact that young people everywhere were taking initiative, standing up an… https://t.co/GITQcjOOyV
FoxNews: Fox News Poll: Proposals to reduce gun violence - percent saying "favor." https://t.co/GBFEtQnnmL https://t.co/gCFO4BRMZZ
FoxNews: Rapper @KillerMike, who endorsed @BernieSanders for president, ripped supporters of the school walkouts in favor of… https://t.co/XeLni8Eyn3
FoxNews: Roughly 100,000 Puerto Ricans still without power after hurricane hit 6 months ago; @BryanLlenas reports. https://t.co/ObWOE3JJcz
FoxNews: First direct flight from Australia to London touches down https://t.co/UeV4OWo6iR
FoxNews: On @foxandfriends?, @GovMikeHuckabee? called for focusing on facts rather than emotion in the gun control debate.… https://t.co/gsxyP4nEJE
FoxNews: Man sucker punches 5-year-old in face on New York City subway: cops https://t.co/yzcyCvzbJR
FoxNews: Fox News Poll: 37% favor allowing teachers to carry guns. https://t.co/GBFEtQnnmL https://t.co/x0xksOQfCE
FoxNews: China conducts air force drills again in disputed South China Sea https://t.co/ZzKmtRUE1E (via @christocarbone)
FoxNews: Roughly 800,000 people participated in the #MarchforourLives rally in Washington; @GillianHTurner reports. https://t.co/ntPYN1CEaM
FoxNews: Fox News Poll: Which is more important to protect? https://t.co/GBFEtQnnmL https://t.co/MIr3umHnxQ
FoxNews: Christians mark #PalmSunday as Holy Week begins; @ConormPowell reports. https://t.co/r7oxk12u82
FoxNews: On @foxandfriends, @robertjeffress praised President @realDonaldTrump's relationship to people of faith.… https://t.co/LyXDe5XBfl
FoxNews: Fox News Poll: Gap narrows on 2018 vote preference https://t.co/xUdGnR4tgC https://t.co/degCXgs9Xw
FoxNews: Huntington Beach Mike Posey: "The biggest consequence for me of course is the Constitutional overreach and the lack… https://t.co/GRDIgUPVvG
FoxNews: $1M in fentanyl seized from Texas trio plotting to mail drugs back from Ohio, authorities say https://t.co/HTldA6B9Nk
FoxNews: Dramatic South Carolina school bus crash caught on camera https://t.co/LxbXIJYPqy
FoxNews: Matthew Schrier is the first American to escape Al Qaeda captivity in Syria. Now he’s speaking out about his claims… https://t.co/pycSo8K1Xu
FoxNews: Joseph DiGenova and Victoria Toensing not joining @realDonaldTrump's legal team. https://t.co/dTKLt4Frnl https://t.co/WjQG5j4CRJ
FoxNews: On "Sunday Morning Futures," @LindseyGrahamSC told @MariaBartiromo that he wants to "prove that the @FBI investigat… https://t.co/W1boo88JFD
FoxNews: TONIGHT on @NextRevFNC, @SteveHiltonx talks to Arnold @Schwarzenegger - Tune in at 9p ET on Fox News Channel! https://t.co/CEnEwePyUU
FoxNews: Fox News Poll: 48% approve of President @realDonaldTrump on taxes. https://t.co/xUdGnR4tgC https://t.co/37rmnmdGar
FoxNews: .@GovMikeHuckabee: "Emotion is a terrible substitute for truth. It is a terrible substitute for facts... Five times… https://t.co/64c4KUUTQ0
FoxNews: Austin bomber called himself a 'psychopath,' had no remorse, congressman says https://t.co/IopCW7KyGG
FoxNews: Chrissy Teigen quits Snapchat amid Rihanna ad scandal, recent update https://t.co/UjOhHfkd3z
FoxNews: 'I Went Through Hell': Former FBI Agent Says Andrew McCabe 'Targeted', 'Slandered' Her
https://t.co/Sf05PC158b
FoxNews: .@IvankaTrump: Skill-based education is crucial to putting more Americans on a path to promising careers https://t.co/fwoS2Ee3xd
FoxNews: .@PeterRoff: Reading the tea leaves on Bolton and other Trump staff changes 
https://t.co/rf4GbodILR
FoxNews: Fox News Poll shows President @realDonaldTrump's approval up on job performance and taxes. https://t.co/KuSKFJP5m4 https://t.co/rjbprWvbEA
FoxNews: NEWS ALERT: Joseph DiGenova and Victoria Toensing not joining @realDonaldTrump's legal team. https://t.co/D3gUfozUs2
FoxNews: Heir to Anheuser-Busch fortune charged with assaulting 6th-grader https://t.co/yg0xYrPkSh
FoxNews: 30 of the 71 living Medal of Honor recipients receive an honor guard in New York before flying to Washington, to ma… https://t.co/fvkynFQkcY
FoxNews: March for Our Lives organizers rally for 'common sense' actions on guns via @FoxNewsSunday https://t.co/9MJs7BU0DF
FoxNews: NBA G League player collapses on court, remains under care by doctors https://t.co/3MWWvpMGNG
FoxNews: .@robertjeffress: "@POTUS is the most faith-friendly president we've ever had, and that includes Ronald Reagan and… https://t.co/UV4gNHfewe
FoxNews: Texas teen was beaten, had hot cooking oil poured on her after refusing arranged marriage: police https://t.co/TCIuI1UFM0
FoxNews: On @foxandfriends, @PeteHegseth strongly defended the Second Amendment. https://t.co/YRyHLDkaUa https://t.co/42RhHbhwY5
FoxNews: .@stevenmnuchin1: President @realDonaldTrump will impose China tariffs, not worried about recent market losses
https://t.co/WyjnKE80tF
FoxNews: .@susanferrechio: "President Obama congratulated Putin in 2012 - there was blatant voter fraud, well-documented."… https://t.co/by7I82sRaz
FoxNews: Peter Navarro: "@POTUS orchestrated one of the most brilliant tax cuts in history." #SundayFutures @MariaBartiromo https://t.co/M7aVyd2aoA
FoxNews: .@LindseyGrahamSC: "I want to be able to prove that the FBI investigation of the Clinton email scandal was a sham.… https://t.co/ly2UNUKgRn
FoxNews: .@LindseyGrahamSC: "The North Koreans know without a doubt that John Bolton sees their nuclear program as a threat… https://t.co/CfqBkWgp0x
FoxNews: .@DevinNunes: "Why do we have the Logan Act on the books when we know that it's selectively enforced?"… https://t.co/LeireZR17e
FoxNews: .@DevinNunes: "We also found no collusion between the Trump campaign but we did find links between the Clinton [cam… https://t.co/T1QDA2emKs
FoxNews: .@DevinNunes: "Let's remember - every president has said that they're going to get tough on people who cheat on tra… https://t.co/wTLrzmLwBL
FoxNews: TONIGHT: 'Legends &amp; Lies' Returns With a Riveting Look at The Civil War - Hosted by Brian @Kilmeade, it all begins… https://t.co/39fRNwFBy4
FoxNews: Peter Navarro: "@POTUS orchestrated one of the most brilliant tax cuts in history." #SundayFutures @MariaBartiromo https://t.co/XRLN2JAmCM
FoxNews: .@LindseyGrahamSC: "We know that @Comey had made a decision to let [@HillaryClinton] off long before he said he did… https://t.co/rWm3B6Siqf
FoxNews: .@LindseyGrahamSC: "We know that Steele lied about the role he played in handling the dossier. We know that the FBI… https://t.co/Oskl6vAj81
FoxNews: .@LindseyGrahamSC: "If you had done what [@HillaryClinton] had done you'd probably be in jail now." #SundayFutures… https://t.co/vu0fpyo3HD
FoxNews: .@LindseyGrahamSC: "I want to be able to prove that the FBI investigation of the Clinton email scandal was a sham.… https://t.co/v4u82uxpxt
FoxNews: .@LindseyGrahamSC: "The North Koreans know without a doubt that John Bolton sees their nuclear program as a threat… https://t.co/hLrRecqUjw
FoxNews: .@LindseyGrahamSC: "@POTUS has been a terrific Commander-in-Chief. John Bolton sees North Korea for the threat they… https://t.co/qZzvnrvV4U
FoxNews: .@LindseyGrahamSC: "This is the strongest down payment on rebuilding the military since Ronald Reagan. The biggest… https://t.co/hafTn3O08U
FoxNews: Dust and sand create eerie, 'apocalyptic' scenes at Russian ski resorts https://t.co/nHr60IuYw3 (via @christocarbone)
FoxNews: .@DevinNunes: "Why do we have the Logan Act on the books when we know that it's selectively enforced?"… https://t.co/2ktcwyQFDC
FoxNews: .@DevinNunes: "We also found no collusion between the Trump campaign but we did find links between the Clinton [cam… https://t.co/Iop2B2TzvQ
FoxNews: .@DevinNunes: "Fusion GPS was paid by the Democratic Party and the Clinton campaign to collude and interact with Ru… https://t.co/JVWgKPUFiI
FoxNews: .@DevinNunes: "Let's remember - every president has said that they're going to get tough on people who cheat on tra… https://t.co/XIHwvZpviD
FoxNews: .@DevinNunes: "Most Americans know that China is in fact stealing our intellectual property. They're spreading glob… https://t.co/0Ulnhn0vj5
FoxNews: .@SenWarren ?slammed President @realDonaldTrump for his order banning most transgender troops from serving in the m… https://t.co/6Jhl89WPXv
FoxNews: RT @FoxNewsSunday: NEW: Fox News Poll: Voters approve of President Trump's meeting with North Korea's Kim Jong-Un, 42% believe Trump will g…
FoxNews: RT @FoxNewsSunday: NEW: Fox News Poll: Voters approve of President Trump's meeting with North Korea's Kim Jong-Un, 42% believe Trump will g…
FoxNews: RT @EricShawnTV: At 12 Noon EDT @FoxNews: The parents of Taylor Force, Robbi and Stuart, join me to talk about the law that honors their so…
FoxNews: Moments ago, President @realDonaldTrump wished our heroes a happy National #MedalofHonorDay. https://t.co/RCkQDCbdL3
FoxNews: Fox News Poll: Gap narrows on 2018 vote preference https://t.co/KuSKFJP5m4 https://t.co/Is0jNxZNDC
FoxNews: RT @FoxNewsSunday: .@cameron_kasky: I think that the fact that young people everywhere were taking initiatives, standing up and leading in…
FoxNews: RT @FoxNewsSunday: On Tariffs' effect on the economy Secretary Mnuchin says: I don't expect to see a big impact on the economy, we've been…
FoxNews: RT @FoxNewsSunday: On trade, Sec Mnuchin says President Trump "has been very clear since our first meeting at Mar-A-Lago with President Xi…
NYTimes: The military strike signals a possibly significant expansion of the American counterterrorism campaign in Libya https://t.co/qBhryVi3mN
NYTimes: Three explosions in 4 days have shattered the Somalian capital and left a trail of carnage in their wake https://t.co/aDUJFEImSS
NYTimes: As Republicans struggle on guns, a conservative donor warns: “The NRA is really out of step with suburban GOP voter… https://t.co/WD2QKH2wn4
NYTimes: Immigration begins and ends well beyond the physical border — a line where fear and hope collide to shape American… https://t.co/UYXGwpqPWG
NYTimes: A Cambridge Analytica-linked company was allegedly used by pro-Brexit campaigners to evade British election spendin… https://t.co/NUZv8NGou3
NYTimes: RT @nickconfessore: Facebook took out ads in the @nytimes (and @washingtonpost + British papers) apologizing for Cambridge Analytica breach…
NYTimes: Qantas Airways made a giant leap forward in long-haul travel with its first non-stop flight between Australia and B… https://t.co/a8fz0npCK2
NYTimes: “I hope in the future for some form of reconciliation. Because I think all men are guilty. I’m not talking about ra… https://t.co/Pmjn6Q666o
NYTimes: RT @nytopinion: Even if trans issues don’t top the list of things you’re worried about, you should be appalled by Donald Trump's latest epi…
NYTimes: “It’s true — Jared has been a positive influence,” said Gerónimo Gutiérrez, Mexico’s ambassador to Washington https://t.co/YWy04Ly1lI
NYTimes: Burt Reynolds on the one that got away: "I’ve had an affair [on the set] with two women in 50 years. Sally Field an… https://t.co/7M1pQ2xiOI
NYTimes: The "Roseanne" reboot premieres on Tuesday. Spend this weekend with some of the classic family sitcom's best episod… https://t.co/kOXRbBygDe
NYTimes: Here are some recipe suggestions to kick off your week in cooking plans https://t.co/WUyuwyYeHl
NYTimes: One reader's reaction to hundreds and thousands of demonstrators flooding streets across the globe in protests on S… https://t.co/Wfql4amZPD
NYTimes: Four members of an Iowa family whose bodies were recently found in a condominium in Mexico died of inhalation of to… https://t.co/A9pOcXBoly
NYTimes: RT @jessicabennett: Their teachers cleared the room of cars and dolls. They put the boys in charge of the play kitchen. They made the girls…
NYTimes: Joshua Tree is one of the U.S.’s most popular parks, just 2 hours from Los Angeles. So how did one hiker simply dis… https://t.co/R4NCdUqGAj
NYTimes: Canada's outdoor rinks are melting. And with them, so is a way of life. https://t.co/peilIX4NeE
NYTimes: At a time when women cyclists were viewed as improper, Lillias Campbell Davidson founded the first cycling organiza… https://t.co/bhWOmb8saS
NYTimes: “Right now, you are allowed to buy the milk, but you can’t know anything about the cow,” says a lawmaker in favor o… https://t.co/qMOQZoYgMU
NYTimes: The Austin bomber and his first victim went to the same barber shop. Investigators are still trying to figure out w… https://t.co/twBHGD2GWj
NYTimes: The man who kayaked across the Atlantic at 70. David Bowie in 3-D. The women who invented the chocolate chip cookie. https://t.co/goxJYvyWiK
NYTimes: In Opinion, 
Op-Ed contributor Fredrik Logevall writes, "Johnson did what modern American presidents are never supp… https://t.co/mrWm6kizLN
NYTimes: They had a mantra: believe, believe, believe. Now the captivating underdog of the N.C.A.A. basketball tournament ha… https://t.co/qr8ktOcLWK
NYTimes: Breaking News: President Trump won't be hiring 2 lawyers he named just days ago in the Mueller inquiry, indicating… https://t.co/PVzhDbfMKX
NYTimes: Five North Koreans set out on the dangerous journey through China to South Korea. They never made it. Their fate is… https://t.co/LJxw5mvkcj
NYTimes: "Chicago has been plagued with gun violence way before the Parkland shooting. Suddenly, people are talking about st… https://t.co/mSp3NPcyNF
NYTimes: It was a crazy week in Washington, even by Washington standards https://t.co/TmrPiG2sT4
NYTimes: "People with dementia also need adventures. They need to get out, just like us." https://t.co/8lumDhOq3l
NYTimes: RT @nytopinion: Unlike other industries, gun manufacturers and sellers are shielded from legal accountability. Bowing to years of intensive…
NYTimes: "Most teenagers talk about drama about girlfriends and boyfriends. And we’re talking about bomb threats and guns."… https://t.co/7CRXvr2rkD
NYTimes: The first American woman to win an Olympic championship died without ever knowing what she had achieved https://t.co/Y8VUBYNj3z
NYTimes: To many in Washington, Stephanie Clifford, better known as Stormy Daniels, has become an unexpected force. It is sh… https://t.co/IbxjNDzVSK
NYTimes: China Splits Top Jobs at Central Bank, Adding Another Reformer https://t.co/kqJZn15u7I
NYTimes: "We’re going to be the generation that takes down the gun lobby." https://t.co/rn5c6E4iCH
NYTimes: One Houston suburb devastated by Harvey is sure to flood again, yet speculators are making a killing buying and res… https://t.co/nH2iYLmP6e
NYTimes: Using Digital Firm, Brexit Campaigners Skirted Spending Laws, Ex-Employee Says https://t.co/ioWAG54LPm
NYTimes: Slammed in September by Hurricanes Irma and Maria, this lush, wild bit of Puerto Rico is still recovering https://t.co/cdiZ3pR3gQ
NYTimes: There was no way around the buzz-kill query: Had Steven Spielberg set out to prove that he hadn’t lost his touch? https://t.co/CK6eQYcO7J
NYTimes: Internet companies were built on a model in which people gave up their information for free services. Now, that ide… https://t.co/LudqMS4Osj
NYTimes: Photos from the #MarchForOurLives protests around the world https://t.co/2b8lrc9V0k https://t.co/42Bl4MZVB8
NYTimes: Washington is now consumed by a debate over whether Trump’s new team plans to govern as far to the right as it talks https://t.co/WKM1QDhokY
NYTimes: In one of Sweden's gender-free schools, a girl had gotten so loud that she drowned out the boys in the class. The g… https://t.co/sDnpGPBZoS
NYTimes: City Kitchen: A Crisp Cool-Weather Twist for a Classic Summer Salad https://t.co/GwCas2J716
NYTimes: The U.S. and China are waging a cold war for global dominance in the tech industry. This week's tariffs duel height… https://t.co/zuhsChWGAX
NYTimes: Greenhouse Gas Emissions Rose Last Year. Here Are the Top 5 Reasons. https://t.co/Q2L0l8bPcS
NYTimes: “How can this be? How can we have so much information about where he was going to go, or at least where he said he… https://t.co/NwPn5MbZzy
NYTimes: There are substantial coverage gaps in traditional Medicare. One of them is care for your teeth. https://t.co/D0v4zTSjMK
NYTimes: Where do these Mets players go when they're hungry for some home cooking? Bravo, of course. https://t.co/aBPw61UmSr
NYTimes: You'll probably need to do a little shopping to make this traditional dish. But it's well worth it. https://t.co/76aUzX0OB0
NYTimes: Sharing is caring. It's also become a trend at fancy restaurants, and not everyone is thrilled. https://t.co/CV9LAUqxYA
NYTimes: Can Facebook be fixed? https://t.co/0BKiz8K04B
NYTimes: Sketch Guy: Resistance Is Futile. To Change Habits, Try Replacement Instead. https://t.co/AeoPk8GlFj
NYTimes: Greenhouse gas emissions rose last year. Here are the top 5 reasons. https://t.co/AVc5lUFm2K
NYTimes: The Great Australian Bight, a pristine stretch of ocean, is believed to have enormous natural gas reserves. The loc… https://t.co/AbefSqKOOO
NYTimes: The Trump administration raised fears of a trade war after it authorized a series of tariffs explicitly — and impli… https://t.co/pzK3Csxgd5
NYTimes: In a story with parallels to that of the American soldier Bowe Bergdahl, Gennady Tsevma walked off a Soviet Army ba… https://t.co/nwna00SbqH
NYTimes: Is it worth making pita at home? Absolutely. https://t.co/nrB0HnpeTl
NYTimes: How do you remove 200,000 pounds of trash from Everest? Recruit yaks. https://t.co/HfCnzbSrck
NYTimes: There will always be something gray and Dickensian about a bowl of morning porridge. Unless, that is, you add choco… https://t.co/xBATIFiZ8R
NYTimes: Need a dinner idea? Try this salmon https://t.co/bHxc5qRygf
NYTimes: For those of us pinching our pennies, dining out can seem like an impossible luxury, but it doesn’t have to be https://t.co/vyi0czqvi7
NYTimes: 40% of Americans were obese in 2015 and 2016, a sharp increase from a decade earlier https://t.co/Rsql03shu8
NYTimes: France is celebrating the memory and the courage of Arnaud Beltrame, a 44-year-old police officer who died of his w… https://t.co/RXCLm92WzK
NYTimes: The Saturday Profile: Shining a Cleansing Light on China’s Dark Secrets https://t.co/lUO49suD7U
NYTimes: Emma González spoke for just under 2 minutes. Then she was silent for 4 minutes and 26 seconds. https://t.co/c0XOh6iP0s
NYTimes: Ruth Wakefield took an ice pick to a chocolate bar and invented an instant classic: the chocolate chip cookie https://t.co/Heiwepqtvm
NYTimes: RT @mattfleg: “At first I thought I wanted to be a journalist," Stormy told us. Didn't break that way. How Stephanie Gregory became Stormy…
NYTimes: Photos from the #MarchForOurLives protests around the world https://t.co/FlH4sFfhhY https://t.co/VE5r9usSCa
NYTimes: RT @nytimesworld: "Some noise or incident would remind me of what happened and I would begin shaking all over. People thought I looked cold…
NYTimes: Put Ziggy Stardust in your living room, and zoom around his glammest looks https://t.co/X4lMkeJ8g7 https://t.co/XtbhAulQvj
NYTimes: "I am here today to acknowledge and represent the African-American girls whose stories don't make the front page of… https://t.co/8ebVDCSlJa
NYTimes: Before her head hits the pillow, Sister Jean has one last obligation: As always, she thanks God for the peace in he… https://t.co/cjVwGoMimf
NYTimes: Just 2 female northern white rhinos remain. But scientists are hoping to resurrect the population with advanced ste… https://t.co/gk7mEVrhER
NYTimes: Speaker after speaker at the Chicago protest against gun violence mentioned relatives or classmates who had been wo… https://t.co/bPQOXszfvY
NYTimes: A Top Candidate for New York Fed’s Leader: San Francisco’s https://t.co/UdjKhz3q8s
NYTimes: RT @NYTSports: Loyola-Chicago is in the Final Four. The captivating underdog of the NCAA tournament, 11th-seeded Loyola rolled over ninth-s…
NYTimes: At Rallies, Students With a Different View of Gun Violence: As Urban Reality https://t.co/TTiUxRyQfu
NYTimes: Native American women are running for office in record numbers. Some are fighting pipelines. Others are fighting en… https://t.co/4AXNNJKsqM
NYTimes: Hundreds of thousands of people marched in cities to protest gun violence, but they were not the only ones to demon… https://t.co/zn3nGpyO0D
NYTimes: Is Facebook too big to quit? Here are answers to some #DeleteFacebook questions. https://t.co/Mw43uhKFIi
NYTimes: They juggle homework with activism. They wince at loud noises. Sometimes, they sleep.

On Saturday, hundreds of stu… https://t.co/jVB7dm2m22
NYTimes: Michel Temer, Brazil’s Deeply Unpopular President, Signals Run for a New Term https://t.co/3WX8XR74W4
NYTimes: Roxanne Shanté paved the way for female rappers like Foxy Brown, Lil' Kim and Cardi B. And now, her story is being… https://t.co/f3IIAWB6hy
NYTimes: Nella Larsen published her first novel "Quicksand" about mixed-raced identity in 1928. It was widely and positively… https://t.co/xfVZixjAFc
NYTimes: Loyola-Chicago Is in the Final Four After a Rout of Kansas State https://t.co/ccjB7XlK1P
NYTimes: Vivica A. Fox: "I’m a woman now in my 50s, and I’m kind of like a phoenix. Whenever they count me out, I always hav… https://t.co/kwlJ6lhN9H
NYTimes: Demonstrators Who Brought Guns and an Opposing Message https://t.co/uyjdwQBO7j
NYTimes: Why did this man kayak across the Atlantic Ocean 3 times?
 https://t.co/k6Un2uC2rq
NYTimes: ‘Done Hiding’: Students Lead Huge Rallies for Gun Control Across the U.S. https://t.co/FN6yU1G5CO
NYTimes: Opinion: Stop Asking About My Kid’s College Plans https://t.co/fvcCOifNMm
NYTimes: Review: ‘Trust’ Is Flashy but Ephemeral https://t.co/9jpCgqoesA
NYTimes: For Parkland Students, a Surreal Journey From ‘Normal’ to a Worldwide March https://t.co/LHAkPTdePS
NYTimes: Drilling in ‘Australia’s Galápagos’ Raises Hopes of Jobs and Fears of Spill https://t.co/0srPvP3wRo
NYTimes: 4 easy ways to cut down your sugar intake https://t.co/diMb2EhNnJ
NYTimes: At the march in Washington, survivors of mass shootings, including the one in Florida, rallied a whooping crowd and… https://t.co/nupqHWoYm1
NYTimes: Gary Lincoff, who spread his joy of mushrooms, has died at 75. He led hunts as far afield as Siberia and found more… https://t.co/txArwxKNII
NYTimes: Rahysa Vargas was introduced to her husband, Christopher Cheng, in September 2006. She was not impressed. https://t.co/Lnq80b4k2Q
NYTimes: A federal appeals court, rejecting the position of the Trump administration, ruled that transgender people are prot… https://t.co/0t6xg2byxo
NYTimes: RT @jillburkealaska: The student activists are fired up, well spoken and getting to the heart of the matter. Here, Hannah Goodrum, 17, minc…
Creat Dataframe

1
# Creat Dataframe
2
tweet_df = pd.DataFrame()
3
tweet_df["NewsOrg"] = tweeting_newsorg
4
tweet_df["Tweets"] = tweets
5
tweet_df["Time"] = tweet_time
6
tweet_df.head()
NewsOrg	Tweets	Time
0	BBC	Could this be an answer to global water shorta...	Sun Mar 25 19:44:01 +0000 2018
1	BBC	Tonight, @regyates meets people whose lives ha...	Sun Mar 25 19:15:06 +0000 2018
2	BBC	Tonight, @mcgregor_ewan and @McgColin celebrat...	Sun Mar 25 18:40:04 +0000 2018
3	BBC	The first ever statue of David Bowie has been ...	Sun Mar 25 18:13:03 +0000 2018
4	BBC	When you're enjoying being single and people j...	Sun Mar 25 17:30:07 +0000 2018
Set up for Sentiment Analysis

1
# Set up for Sentiment Analysis
2
compound = []
3
pos = []
4
neu = []
5
neg = []
6
?
7
for x in tweet_df["Tweets"]:
8
    scores = analyzer.polarity_scores(x)
9
    #print(scores)    
10
    compound.append(scores['compound'])
11
    pos.append(scores['pos'])
12
    neu.append(scores['neu'])
13
    neg.append(scores['neg']) 
14
?
Create Dataframe

1
# Create Dataframe
2
tweet_df["Compound Score"] = compound
3
tweet_df["Positive Score"] = pos
4
tweet_df["Negative Score"] = neg
5
tweet_df["Neutral Score"] = neu
6
tweet_df.head()
7
?
NewsOrg	Tweets	Time	Compound Score	Positive Score	Negative Score	Neutral Score
0	BBC	Could this be an answer to global water shorta...	Sun Mar 25 19:44:01 +0000 2018	0.1280	0.101	0.077	0.821
1	BBC	Tonight, @regyates meets people whose lives ha...	Sun Mar 25 19:15:06 +0000 2018	-0.7506	0.000	0.286	0.714
2	BBC	Tonight, @mcgregor_ewan and @McgColin celebrat...	Sun Mar 25 18:40:04 +0000 2018	0.5719	0.163	0.000	0.837
3	BBC	The first ever statue of David Bowie has been ...	Sun Mar 25 18:13:03 +0000 2018	0.0000	0.000	0.000	1.000
4	BBC	When you're enjoying being single and people j...	Sun Mar 25 17:30:07 +0000 2018	0.5267	0.185	0.000	0.815
Creat CSV

1
# Creat CSV
2
tweet_df.to_csv("Tweets_Sentiment.csv")
Do My GroupBy

1
# Do My GroupBy
2
tweet_df['Tweets Ago'] = tweet_df.groupby('NewsOrg')['Time'].rank(ascending=False)
Create date format

# Create date format
1
# Create date format
2
date = dt.date.today
3
date = dt.datetime.today().strftime("%m/%d/%Y")
Set up my colors for plot

# Set up my colors
tweet_df["coloring"]= tweet_df["NewsOrg"]
tweet_df.loc[:, 'coloring'].replace(["BBC", "CBS", "CNN", "FoxNews", "NYTimes"], ["blue", "violet", "orange", "gray","gold"],
                                  inplace=True)
colors= tweet_df["coloring"].values
1
# Set up my colors
2
tweet_df["coloring"]= tweet_df["NewsOrg"]
3
tweet_df.loc[:, 'coloring'].replace(["BBC", "CBS", "CNN", "FoxNews", "NYTimes"], ["blue", "violet", "orange", "gray","gold"],
4
                                  inplace=True)
5
colors= tweet_df["coloring"].values
Create My Plot

# Create My Plot
1
# Create My Plot
2
plt.figure(figsize=(12,8))
3
?
4
#plt.colors
5
plt.scatter(tweet_df['Tweets Ago'], tweet_df['Compound Score'], marker='o'
6
            ,c=colors, edgecolors='black',s=200)
7
?
8
one = mpatches.Patch(color='blue', label='BBC')
9
two = mpatches.Patch(color='violet', label='CBS')
10
three = mpatches.Patch(color='orange', label='CNN')
11
four = mpatches.Patch(color='gray', label='Fox News')
12
five = mpatches.Patch(color='gold', label='New York Times')
13
?
14
# Incorporate the other graph properties
15
plt.title('Sentiment Analysis of Media Tweets ('+ date+")")
16
plt.ylabel('Tweet Polarity')
17
plt.xlabel('Tweets Ago')
18
plt.grid(True)
19
plt.xlim(105, -5)
20
plt.ylim(-1.05, 1.05)
21
?
22
plt.legend(title="Media Sources", handles=[one, two, three, four, five],
23
          bbox_to_anchor=(1.05, 1), loc=2, borderaxespad=0.)
24
?
25
?
26
# Save the figure
27
plt.savefig('Sentiment_analysis_scatter_plot.png')
28
?
29
# Show plot
30
plt.show()

Do My GroupBy

1
# Do My GroupBy
2
pd.options.display.float_format = '{:,.4f}'.format
3
tweet_df_new = tweet_df.groupby("NewsOrg")
4
tweet_df_new = tweet_df_new["Compound Score"].mean()
5
tweet_df_new = pd.DataFrame(tweet_df_new)
6
tweet_df_new.head()
Compound Score
NewsOrg	
BBC	0.0679
CBS	0.3355
CNN	-0.0658
FoxNews	-0.0113
NYTimes	-0.0233
Set up my colors

1
# Set up my colors
2
tweet_df_new["coloring"]= tweet_df_new.index
3
tweet_df_new.loc[:, 'coloring'].replace(["BBC", "CBS", "CNN", "FoxNews", "NYTimes"], ["blue", "violet", "orange", "gray","gold"],
4
                                  inplace=True)
5
colors_new= tweet_df_new["coloring"].values
6
ticks=["BBC", "CBS", "CNN", "Fox", "NYT"]
Create My Plot

1
# Create My Plot
2
fig, ax = plt.subplots()
3
?
4
rects = ax.bar(tweet_df_new.index,tweet_df_new["Compound Score"],edgecolor=['black']*len(x),color=colors_new,
5
       tick_label=ticks, width=1.0)
6
?
7
plt.ylim(-0.05, 0.45)
8
?
9
plt.title('Overall Media Sentiment Based on Twitter ('+ date+")")
10
plt.ylabel('Tweet Polarity')
11
plt.xlabel('NewsOrg')
12
?
13
?
14
labels = round(tweet_df_new["Compound Score"], 5)
15
?
16
?
17
for rect, label in zip(rects, labels):
18
    height = rect.get_height()
19
    ax.text(rect.get_x() + rect.get_width()/2, height + 0.02, label, ha='center', va='bottom')
20
?
21
    fig = plt.gcf()
22
fig.set_size_inches(12,8)
23
?
24
plt.savefig('Overall_Sentiment_barplot.png')
25
?
26
plt.show()
