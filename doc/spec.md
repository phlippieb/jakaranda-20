# Specification - Jakaranda Wynproegulde Proegids

Note: This spec only reflects the scope to be implemented for the current milestone (currently, this is milestone 1). As subsequent milestones move into scope, this spec doc will be updated.

## Overview

For the first milestone, the app simply guides users through tasting and scoring a single wine at a time. The guide is based on the WSET systematic wine tasting guide, asking users to evaluate the wine on various criteria. Some of these criteria are then factored into an automatically-calculated score. After the evaluation is complete and the score has been computed, the users can then finally adjust this score based on their personal impression of the wine on the three main dimensions, namely appearance, nose, and palate.

## Interface description

There is a single screen for the evaluation of a single wine. The screen is divided into sections:

1. Wine info
1. Tasting guide
   1. Appearance
   1. Nose
   1. Palate
   1. Conclusion
1. Score

This spec includes English and *Afrikaans* terminology for easy reference during implementation.

### Section 1: Wine Info / *Wyn Inligting*

The **Wine Info** section presents the user with editable fields for the following basic identifiers of the wine:

1. Producer / *Produsent*
1. Name of wine / *Naam van wyn*
1. Varietal or blend (just a text field) / *Kultivar of versnit*
1. Vintage / *Jaar*
1. Notes (freeform textfield) / *Notas*

After this are more advanced fields:

1. Alcohol (percent) / *Alkohol*
1. Residual sugar (grams per liter) / *Residuele suiker*
1. Total acid (grams per liter) / *Totale suur*

### Section 2: Tasting guide / *Proegids*

Criteria as per the WSET rubrik are shown here. The criteria are subdivided into categories for appearance, nose, palate, and conclusions. For most criteria, the user picks the one option which best describes the wine. For some options, marked "pick multiple", the user can pick any (or none). Some options, when selected, open a sub-menu with further options to refine the evaluation. Some options are required for scoring purposes, and others can be elided.

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

### Section 3: Score

This section shows the wine's score along the criteria that are considered for the gild's version of the 20-point scoring system. As the user completes the tasting evaluation in the previous section, some criteria will automatically set the corresponding criteria in this section. Any criteria which haven't been evaluated yet will receive the default score. The user can manually set the score for each criteria or the overall score, and each item can be reset to the default. Once an item has been manually edited, it will not be automatically changed until it is reset to the default; for example, if a user has manually added 0.5 to the "nose open" score, and then modifies the "nose intensity" evaluation in the previous section, that latter update won't override the manual score.

The scoring interface details below outline the elements of the scoring interface. 

The score criteria are grouped into categories (1-3). In brackets next to each category is the range of normally-allowed scores, with the lower score being the default, and the highest score being the maximum allowed. A score below the default is also indicated which can be assigned if the wine is faulty with regards to the category.

Within each category is the scoring criteria (i, ii, etc) from which the final score is computed. For each criterion, bullet points list all the allowed scores along with their quality descriptors; these are the messages that are displayed when a user assigns a specific score, to help users pick an appropriate score for each criterion. Some criteria are automatically set from the evaluation in the previous section; these mappings are noted in the bullet points. Criteria scores can be adjusted with +/- buttons and reset to the default (as per the evaluation in the previous section, if available, or to the default value for each score).

Lastly, the final score (4) is computed by adding all the criteria scores together. The final score can be manually adjusted with +/- buttons or reset to the default (as computed from the score criteria). Bullet points indicate the allowed values for the final score, and the quality descriptors displayed for each final score.

#### Scoring interface details

1. Appearance / *Voorkoms* (3; 2 if faulty)
   1. Condition / *Toestand* (3; 2 if faulty)
      - 3: Default
      - 2: Faulty / *Foutief*
      - Automatically set from "appearance: clarity" -- if faulty, assign 2
1. Nose / *Neus* (4-7; 3 if faulty)
   1. Condition / *Toestand* (1-2; 0 if faulty)
      - 1: Default
      - 0: Faulty / *Foutief*
      - Automatically set from "nose: condition" -- if faulty, assign 0
   1. Open / *Oop* (1-2)
      - 1: Default
      - 1.5: Very open / *Baie oop*
      - 2: Jumping out / *Sprint uit*
      - Automatically set from "nose: intensity" -- 1.5 for "medium" to "medium+"; 2 for "heavy/full/pronounced"
   1. Aroma / *Aroma* (1-2)
      - 1: Default
      - 1.5: Complex and/or good cultivar characteristics / *Kompleks en/of goeie kultivar kenmerke*
      - 2: ?
   1. Bouquet / *Bouquet* (1-2)
      - 1: Default
      - 1.5: Complex and/or good wood characteristincs / *Kompleks en/of goeie hout kenmerke*
      - 2: ?
1. Palate / *Smaak* (7-10; 6 if faulty)
   1. Balance / *Balans* (1-1.5; 0 if faulty)
      - 1: Default
      - 0: Unbalanced / *Ongebalanseerd*
      - 1.5: Very well balanced / *Uitstekend gebalanseerd*
   1. Complexity / *Kompleksiteit* (1-1.5)
      - 1: Default
      - 1.5: Very complex / *Baie kompleks*
   1. Body / *Lyf* (0.5-1)
      - 0.5: Default
      - 1: Very intense / *Baie intens*
      - Automatically set from "palate: body" -- 1 for "heavy"
   1. Character / *Karakter* (0.5-1)
      - 0.5: Default
      - 1: Markedly powerful, elegant, refined, etc. / *Merkbaar kragtig, elegant, verfynd, ens.*
   1. Finish / *Nasmaak* (1-2)
      - 1: Default
      - 1.5: Extended / *Lank*
      - 2: Lingering / *Besonder lank*
      - Automatically set from "palate: finish" -- 1.5 for "medium" to "medium+"; 2 for "long"
1. Final score / *Finale punt* (14-20; <14 if faulty)
   - 13 - 13.5: Ordinary / *Gewoon*
   - 14 - 14.5: Average; appealing / *Gemiddeld; aangenaam*
   - 15 - 15.5: Good to very good / *Goed to baie goed*
   - 16 - 17: Excellent; wine of distinction / *Uitstekend*
   - 17.5: Outstanding / *Besonders*
   - 18+: Superlative; top class; masterpiece / *Top klas; meesterlik*
