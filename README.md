# _Kalevala_ scansion

This is a short program that can often (but not always: see ‘Known deficiency’) correctly scan the tetrameter verse form used in the _Kalevala_ and other poems. Enter a line in Finnish: the program will display its metrical structure and identify the line as a normal tetrameter (one where all accents in non-first feet fall on metrical rises) or a broken tetrameter. If it can’t scan the input as a valid line, it will say `too long` (more than ten syllables), `too short` (fewer than eight), `illicit final syllable` (the line ends in a monosyllable or a syllable containing a long vowel), or `doesn't scan` (at least one accented syllable is metrically inadmissible). It may even be of some practical use, perhaps to people who are just getting started reading passages from the _Kalevala_ in Finnish; but I expect most people with any interest in the scansion of _Kalevala_-metre tetrameters can already scan them at least as well as the program can. It is intended more as an essay in using a programming language—in this case the term-rewriting functional language Refal—as a medium to express rules of this kind concisely, unambiguously, and (I hope) clearly. In the process it implicitly draws attention to the areas that are less amenable to straightforward formal treatment.

The program incorporates one supplement to the rules of scansion as I have found them stated in various places online: it scans a short vowel followed by _ts_ as a short syllable if the metre requires it (long otherwise). I hope this isn’t wrong: I’m not sure how else lines like _käy tänne kutsuttaessa_ (1:172) or _ikävä itsen Ukonki_ (47:50) can be made to scan at all.

### Usage

Versions are provided in both Refal-2 (slightly shorter) and Refal-5 (probably more readable). Run either from the command line as you would any other Refal program: for example, with Anton Todua’s Refal-2 interpreter (available in [source form](https://github.com/cmc-msu-ai/refal) or as a [Microsoft Windows executable](http://refal2.github.io)) just type `refal2 kalevala.ref`; with [the PZ version of Refal-5](https://github.com/muspellsson/refal5) use `refc kalevala` to compile the program and then `refgo kalevala` to run it. Any characters in the input other than basic Latin letters, _Ää Öö_, hyphens, apostrophes (which can be entered as `’` or `'`), and whitespace are ignored—even letters like _Šš_, which may occur in modern Finnish text but are not found in the _Kalevala_. An example interaction with the program:

```
Enter one tetrameter at a time, or a blank line to exit.
Tetrameter:
Hyvä on hylkehen eleä,
     /    /    /         
    (˘˘¯)(¯˘)(˘˘)(˘˘)   broken tetrameter
Tetrameter:
ve’en koiran viehkuroia:
     /   /   /          
    (˘¯)(¯¯)(¯˘)(¯˘)    normal tetrameter
Tetrameter:
luotansa lohia syöpi,
     /    /      /      
    (¯¯)(˘˘)(˘˘)(¯˘)    broken tetrameter
Tetrameter:
sivultansa siikasia.
     /       /          
    (˘¯)(¯˘)(¯˘)(˘˘)    normal tetrameter
Tetrameter:
Jumala sanoi: »Tulkoon valkeus»
     /  /   /   /         
    (˘˘˘˘)(¯¯)(¯¯)(˘˘)  doesn't scan
Tetrameter:
```

### Known deficiency

The major weakness of the program is that it can’t identify compound words (unless you artificially hyphenate them). A compound behaves in many ways like two separate words: for example, ‘first-syllable-only’ diphthongs can appear in the first syllable of each half, instead of being treated as two short vowels in hiatus. Total accuracy in scansion therefore requires the ability to recognize compound words and split them into their constituent parts. Unfortunately, I’m not aware of a reliable way to do that without knowing the vocabulary; I don’t think any exists. And giving the program a Finnish dictionary would change it from a simple hundred-line essay into a very different kind of project. The upshot is that this program cannot be relied upon to scan lines with compound words correctly unless you help it out with a hyphen. It also accepts purported tetrameters like *_vanha Väinämöinen lauloi_—which human readers would reject—as metrically valid, because it can’t tell that the four-syllable word is not a compound.

### Other _Kalevala_ resources

• Harri Perälä’s [Reading the _Kalevala_ in the Original Language](https://alboin.fi/kalevalaiset/reading/index.htm) is intended for beginners: it includes a discussion of the scansion as well as a fully glossed and parsed text of 43:1–134.

• If (like me) you can’t read Finnish as well as you would wish, you will need a text with a line-by-line translation into another language. I don’t know of one with parallel English, but there are complete online texts with [parallel German](https://www.hs-augsburg.de/~harsch/germanica/Chronologie/19Jh/Schiefner/sch_ka43.html) and [parallel Italian](https://bifrost.it/FINNI/Fonti/Kalevala01.html).

• If you’re interested in how the _Kalevala_ sounds when it is chanted or sung, the Library of Congress has a nice recording from 1939 of [John Soininen singing](https://www.loc.gov/item/2017701839/) 40:220–263. The sung rhythm is very strongly trochaic—not quite what you’d predict from the scansion on the page.

• Most Finnish language textbooks assume you want to be able to talk to people in twenty-first-century Helsinki, not in those glades of Väinölä. _A Finnish Grammar_ by Charles Eliot (originally published in 1890 and now freely available in several formats [from Project Gutenberg](https://www.gutenberg.org/ebooks/59795)) has its own eccentricities, but it makes no such assumption: in fact, it provides several annotated extracts from the _Kalevala_ as reading passages.

• A number of translations of the _Kalevala_ into English exist, but Keith Bosley’s (first published by OUP in 1989) is a life-changing book. Bosley does not, however, attempt to mimic the original scansion (which would scarcely be possible in English); so you’ll still need to look at the Finnish.
