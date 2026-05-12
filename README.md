# E-Parduotuvės (Barbora) programos ataskaita

## 1. Introduction
**What is your application?** 
Ši programa yra elektroninės parduotuvės simuliacija, "Barbora" analogas. Ši programa leidžia pirkėjui rinktis prekes iš katalogo ir dėti jas į krepšelį, o apsipirkimo pabaigoj gaunamas pirkimo kvitas.

**How to run the program?** 
1. Turėti įdiegtą Python 3.
2. Turėti paruoštą `produktai.csv` failą tame pačiame aplanke su pagrindine programa.
3. Paleisti pagrindinį programos failą terminale: `python main.py`.
4. Testavimui naudokite komandą: `python -m unittest test_shop.py`.

**How to use the program?** 
Paleidus programą, reikia įvesti miesto ir gatvės pavadinimus. Tuomet iš prekių katalogo išsirinkti prekės numerį, kurį norite pridėti į krepšelį, o norint baigti apsipirkimą, reikia įvesti `0`. Programa sukurs `.txt` formato kvitą ir išsaugos jį kompiuteryje.

## 2. Body/Analysis
Programa pilnai realizuoja objektinio programavimo (OOP) principus ir atitinka funkcinius reikalavimus:

* **Abstraction (Abstrakcija):**
Sukurta abstrakti klasė `Product` naudojant `ABC` modulį. Joje apibrėžtas abstraktus metodas `get_details()`, kurį privalo realizuoti vaikinės klasės.

* **Encapsulation (Inkapsuliacija):**
`Product` klasėje prekės kaina apsaugota privačiu kintamuoju `self.__price`, o pasiekiama tik per getterį `get_price()`.

* **Inheritance (Paveldėjimas):**
Klasės `FoodProduct` ir `HouseholdProduct` paveldi bazines savybes iš 
`Product` klasės.

* **Polymorphism (Polimorfizmas):**
Metodas `get_details()` yra perrašytas abiejose vaikinėse klasėse, kad grąžintų skirtingai suformatuotą informaciją priklausomai nuo prekės tipo.

**Design Pattern:** 
Panaudotas *Factory Method* šablonas (`ProductFactory` klasė).  

*Kodėl jis tinkamiausias?* Tais atvejais, kai turime skirtingas prekių rūšis(food ir household), Factory šablonas leidžia patogiai kurti joms objektus vienoje vietoje, tiesiog pažiūrėjus į prekės tipą CSV faile. Tai padeda kodą išlaikyti tvarkingą ir ateityje norint pridėti daugiau prekių kategorijų tai nėra taip sudėtinga.

**Composition and Aggregation:**
*Kompozicija:* Klasėje `Order` tiesiogiai sukuriama `Address` instancija. Jei užsakymas ištrinamas, jo pristatymo adresas taip pat praranda prasmę.
*Agregacija:* `Order` klasė kaupia `Product` objektus sąraše `self.products`. Prekės egzistuoja parduotuvės asortimente nepriklausomai nuo to, ar jos yra užsakyme.

**File I/O:** 
Prekės nuskaitomos iš `produktai.csv` failo panaudojant `csv` biblioteką. Apsipirkimo pabaigoje kvitas įrašomas į sugeneruotą `.txt` failą.

## 3. Results and Summary
* Programa sėkmingai perskaito duomenis iš CSV failo ir paverčia juos objektais naudojant Factory šabloną.
* Vartotojas programa naudojas interaktyviai, bet taip pat programa apsaugo nuo klaidų (pvz., įvedus ne skaičių).
* Sėkmingai sugeneruojamas kvitas su visa reikiama informacija (adresas, prekių sąrašas, galutinė suma).

* **Iššūkiai:**
Vienas iš iššūkių buvo teisingai suformatuoti kvitą ir išlaikyti lygiavimą terminale, tam padėjo f-string formatavimas (pvz. ':<30').

## 4. Conclusion
Šio darbo metu buvo sėkmingai įtvirtintos Python objektinio programavimo žinios. Sukurta veikianti ir lengvai plečiama e-parduotuvės sistema. 

**Ateities perspektyvos:**
Programą būtų galima išplėsti pridedant duomenų bazę (pvz., SQLite) vietoj `.csv` failo, bei sukuriant grafinę vartotojo sąsają (GUI) su `Tkinter` ar website'ą.
