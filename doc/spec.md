# Specification - Jakaranda Wynproegulde Proegids

Note: This spec only reflects the scope to be implemented for the current milestone (currently, this is milestone 1). As subsequent milestones move into scope, this spec doc will be updated.

## Overview

For the first milestone, the app simply guides users through tasting a single wine at a time. The guide is based on the WSET systematic wine tasting guide, asking users to evaluate the wine on various criteria. Some of these criteria are then factored into an automatically-calculated score. After the evaluation is complete and the score has been computed, the users can then finally tweak this score based on their overall impression of the wine on the three main dimensions, namely appearance, nose, and palate.

## Features

### Interface description

There is a single screen for the current wine evaluation. The screen is divided into sections:

1. Wine info
2. Tasting guide
   - Appearance
   - Nose
   - Palate
   - Conclusion
3. Score

#### Section 1: Wine Info

At the top are fields for the following basic identifiers of the wine:

1. Producer
1. Name of wine
1. Varietal or blend (just a text field)
1. Vintage
1. Freeform textfield for additional notes

After this are more advanced fields:

1. Alcohol (percent)
1. Residual sugar (grams per liter)
1. Total (grams per liter)

#### Section 2: Tasting/evaluation guide

The criteria as per the WSET rubrik is shown. The criteria are subdivided into categories for appearance, nose, palate, and conclusions. For most criteria, the user picks the one option which best describes the wine. For some options, marked "pick multiple", the user can pick any (or none). Some options, when selected, open a sub-menu with further options to refine the evaluation. Some options are required for scoring purposes, and others can be elided.

The spec includes English and *Afrikaans* terminology for easy reference.

Appearance  
*Voorkoms*
- Clarity: clear, hazy (faulty)  
  *Helderheid: helder, dof (foutief)*
- Intensity: light, medium-, medium, medium+, deep  
  *Intensiteit: lig, medium-, medium, medium+, diep*
- Color (depending on the type of wine)  
  *Kleur*
  - White: watery, straw, yellow, gold, amber  
    *Wit: waterig, strooi, geel, goud, amber*
  - White undertone: green, salmon, pink, red, brown  
    *Wit ondertoon: groen, salm, pienk, rooi, bruin*
  - Rosé: pale, light pink, pink, salmon, orange  
    *Rosé: bleek, ligpienk, pienk, salm, oranje*
  - Red: purple, ruby, granate, brick, amber  
    *Rooi: pers, robyn, granaatrooi, baksteen, amber*
- Other observations (pick multiple): tears, sediment, pétillance, bubbles  
  *Ander opmerkings: trane, sediment, pétillance, borrels*

Note: since the varietal/blend section is just a text field, the app cannot yet automatically determine whether the wine is white, red, or rosé; we will need to let the user choose, perhaps also as part of the info section. Keep in mind that there are others, such as orange wines.

Nose  
*Neus*
- Condition: clean, faulty  
  *Toestand: skoon, foutief*
  - If faulty (pick multiple): corked, volatile acidity, bret, alcoholic, other  
    *Indien foutief: gekurk, vlugtige suur, bret, alkoholies, ander*
- Intensity: shy, light, medium-, medium, medium+, heavy/full/pronounced  
  *Intensiteit: skaam, lig, medium-, medium, medium+, swaar/vol/duidelik*
- Aroma (pick multiple): floral, fruit, vegetal, spices, wood, malolactic fermentation  
  *Aroma: blomme, vrugte, plantaardig, speserye, hout, malolaktiese gisting*    
  Picking a top-level aroma will open a menu for users to refine their evaluation, as below. For each, the user can pick multiple.  
  Primary
    - Floral: acacia, honeysuckle, lilies, malva, blossoms, rose, violet  
      *Blomme: Akasia, kamferfoelie, lelies, malva, bloeisels, roos, viooltjie*
    - Fruit: greenfruit , citrus, stonefruit, tropical fruit, red fruit, black fruit, dried fruit  
      *Vrugte: groen vrugte, sitrus, steenvrug, tropiese vrug, rooi vrug, swart vrug, droë vrugte*  
      Each option opens a further sub-menu to refine the evaluation:
      - Green fruit: apple, pear, quince, gooseberry, grape  
        *Groen vrugte: appel, peer, kweper, appelliefie, druif*
      - Citrus: pomelo, lemon, lime, orange peel, lemon peel  
        *Sitrus: pomelo, suurlemoen, lemmetjie, lemoenskil, suurlemoenskil*
      - Stonefruit: peach, apricot, nectarine  
        *Steenvrug: perske, appelkoos, nektarien*
      - Tropical fruit: banana, litchi, mango, canteloupe, melon, pineapple  
        *Tropiese vrug: piesang, lietsjie, mango, spanspek, groen spanspek (melon), pynappel*
      - Red fruit: red currant, cranberry, blackberry, strawberry, red cherry, red plum  
        *Rooi vrug: rooi aalbessie, bosbessie, braam, aarbei, rooi kersies, rooi pruim*
      - Black fruit: black currant, blackberry, blueberry, black cherry, black plum  
        *Swart vrug: Swart aalbessie (black currant), braam, bloubessie, swart kersie, swart pruim*
      - Dried fruit: dried figs, prune, raisin, sultana, kirsch, jam, stewed fruit, pickled fruit  
        *Droë vrugte: droë vye, pruimedant, rosyne, sultana, kirsch, konfyt, gestoofde vrugte, ingelegde vrugte.*
    - Vegetal: green pepper, cut grass, tomato leaves, asparagus, mushrooms, compost, forest floor, farmyard, duck droppings, herbs  
      *Plantaardig: Groenpeper, gesnyde gras, tamatieblare, aspersie, sampioene, kompos, woudvloer, plaaswerf, eendemis, kruie*  
      Choosing "herbs" will open a sub-menu:
        - Herbs: dill, fennel, lavender, medicinal, mint, eucalyptus  
          *Kruie: Dille, vinkel, laventel, medisyne, ment, bloekom*
    - Spices: white pepper, black pepper, liquirice, smoked ham  
      *Speserye: witpeper, swartpeper, liquorice, gerookte spek*
  Secondary
    - Wood: vanilla, cloves, nutmeg, coconut, toffee (butterscotch), toast brea, cedar (pencil shavings), burnt wood, smoke, chocolate, coffee, resin  
      *Hout: vanilla, naeltjies, neutmuskaat, klapper, toffie (butterscotch), roosterbrood, seder (potlood skaafsels) gebande hout, rook, sjokolade, koffie, harpuis*  
    - Malo (malalactic fermentation, MLF): butter, cheese, cream  
      *Melksuur (malolaktiese) gisting: botter, kaas, room*
  Tertiary
    - Oxidation: almond, marzipan, hazelnut, walnut, chocolate, coffee, toffee, caramel  
      *Oksidasie: Amandel, marsepein,  haselneut, okkerneut, sjokolade, koffie, toffie, karamel*
    - Fruit development: dried apricot, marmelade, dried apple, baked apple  
      *Vrugte ontwikkeling: droë appelkoos, marmelade, droë appel, gebakte appel*
    - Fruit development (red): figs, prunes, tar, dried berries, baked or cooked red fruit, fruit cake  
      *Vrugte ontwikkeling (rooi) Vye, pruimedant, teer, droë bessies, gebakte / gekookte rooi vrug, vrugtekoek*
    - Bottle aging (white): petrol, parafin, turpentine, cinamon, ginger, toast, nuts, straw, mushrooms, honey  
      *Bottel veroudering (wit): petrol, paraffien, terpentyn, kaneel, gemmer, roosterbrood, neute, strooi, sampioen, heuning*
    - Bottle aging (red): leather, forest, wet soil, mushroom, tabacco, wet leaves, compost, salted meat, bacon, farmyard  
      *Bottelveroudering (rooi):  leer, woud, nat grond, sampioen, tabak, nat blare, kompos, sampioen, soutvleis, spek, plaaswerf*

Palate  
*Smaak*
- Sweetness: dry, off-dry, medium sweet, sweet, luscious  
  *Suiker: droog, af van droog, half droog, halfsoet, soet, volsoet*
- Acidity: low, medium-, medium, medium+, high  
  *Suur: laag, medium-, medium, medium+, hoog*
- Tanin level: soft, medium-, medium, medium+, hard  
  *Tannien: sag, medium-, medium, medium+, hard*
- Tanin nature: ripe, soft, smooth, unripe, green, coarse, stalky, chalky, fine-grained  
  *Karakter van tannien: ryp, sag, glad, onryp, groen, grof, takke, bordkryt, fyn*
- Alcohol: low, medium-, medium, medium+, high  
  *Alkohol: Laag, medium-, medium, medium+, hoog*
- Body: thin/light, medium-, elegant/medium, full/medium+, heavy*  
  *Gewig: dun/lig, medium-, elegant/medium, vol/medium+, swaar*
- Flavour intensity: weak/light, medium-, medium, medium+, intense/pronounced  
  *Intensiteit van geure: flou, medium-, medium, medium+, intens*
- Flavour characteristics (pick any): fruit driven, secondary flavours, bottle aging  
  *Geurprofiel vrug gedrewe, sekondêre geure, bottel veroudering*
- Finish: short, medium-, medium, medium+, long  
  *Lengte van nasmaak: kort, medium-, medium, medium+, lank*

Conclusions  
*Gevolgtrekkings*
- Quality: faulty, poor, acceptable, good, very good, excellent  
  *Kwaliteit: foutief, swak, aanvaarbaar, goed, baie goed, uitstekend*
- Aging potential: too young, good now and can be aged, must be drank now, too old  
  *Verouderingspotensiaal: Te jonk, drink nou maar kan verouder, drink nou, oor die muur*

#### Score

Once the tasting guide has been completed, a score out of 20 is calculated and displayed. The score is subdivided into the following categories:

1. Appearance (max score: 3)
2. Nose (max score: 7)
3. Palate (max score: 10)

The user can tweak the score for each category; this allows for a more intuitive scoring in the event that they do not agree with the auto-calculated score.

### Score calculation logic

This section describes the logic for deriving a 20-point score from the evaluation provided by the user during the WSET evaluation.

<!-- TODO: Define the logic -->
