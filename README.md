
klassen und objekte

_______________________________________________________________________

assoziation und vererbung

_______________________________________________________________________

aggregation und Komposition

_______________________________________________________________________

Datenstruktur: Feld (array)(speicher festgesetzt aber schneller als eine Liste, man kann gezielt eine stelle des Arrays anpeilen ohne die anderen zu berücksichtigen), 
verkettete Liste (speicher variabel aber langsamer als Array, weil man adie liste von oben nach unten durchgehen muss ohne direkt auf eine stelle zu springen),
Stapel (first in last out), Schlange (first in first out)

_______________________________________________________________________

Templates und generische Programmierung

_______________________________________________________________________

Nicht-Sequentielle Programmierung

_______________________________________________________________________

struct(kann ich nicht vererben(sind wertetypen)) vs. Klasse (reference type)

_______________________________________________________________________

Kapselung

_______________________________________________________________________

Konstructor (ist eine Methode die nur aufgerufen wird wenn das Objekt erstellt wird(heißt immer wie die Klasse))/ Destrcuktor

_______________________________________________________________________

call by value, call by references

_______________________________________________________________________

Properties: Get & Set methode

_______________________________________________________________________

vererbung

_______________________________________________________________________

Polymorphismus

_______________________________________________________________________

Inkrement/ Deskrement 

//prefix 
j1 : int = 2;
k1 : int;
k1 = ++j1;          // k1 ist 3

//postfix
j2 : int = 2;
k2 : int;
k2 = j2++;          // k2 ist 2


Softwaretechnik
_______________________________________________________________________

Entwickler: 
setzen konkrete vorgaben um
arbeiten problemorientiert
zumeist reine coder 
verdienst 15-26k Euro

Software Engineer:

erarbeitet modelle testfälle konzepte
involviert in projektmanagmet, Anforderungsmanagment und QA
wie der Entwickler involviert in Coding, Testing und Entwicklung
Arbeitet auf höherem Abstraktionsniveau
gehalt: 40 - 66k Euro

Software Architekt:

trifft grundlegende Entscheidungen
Konzipiert bei großen Projekten Systeme und das Zusammenspiel der Komponenten
arbeitet auf nochmals höherem Abstraktionsniveau
Arebiette potentiell projekt-,team- systemübergreifend
Gehalt: 36-55k Euro


Projektplanung
Anforderungs Management
Risiko Management
Teamorganisiation
Code Design
Testing
Deplyment (wie baue ich meine software aus)
Wartung & Lifecycle Management 


Bitmask

_______________________________________________________________________

Eigene währung programmieren

variablen: 

		          	||
		      _______________________
		       |  Element	    |
		       |<Objekte> 	    |
		       |  Name String:      |
		       |  Wert(Divisor) int:|
          	       |____________________|

			Currency
		      ------------
	Definition: Element [Array] (Reihenfolge ist WICHTIG)
			
		 Anzahl Münzen 14203
		14203 % 10 = 3 Kupfer
		14203 / 10 = 1420

		1420 % 100 = 20 Silber
		1420 / 100 = 14

		14 % 1000 = 14 Gold
			
			



			||

Anzahl der Kupfermünzen die man bekommt
Zwischenspeicher

Erstelle ein neues Objekt mit den gegeben Daten



      			||

Eingabe der Währungen (z.B. Kupfer, Silber, Gold, Diamant) 

			||

10   Kupfer = 1 Silber 	
100  silber = 1 Gold
1000 Gold   = 1 Diamant	

			||

Anzahl Münzen 14203
14203 % 10 = 3 Kupfer
14203 / 10 = 1420

1420 % 100 = 20 Silber
1420 / 100 = 14

14 % 1000 = 14 Gold


			||

Ausgabe: 14 Gold, 20 Silber, 3 Kupfer

_______________________________________________________________________

		        	|Lösung|
		       _______________________
		       |  Element	    |
		       |<Objekte> 	    |
		       |  Name String:      |
		       |  Wert(Divisor) int:|
           	       |____________________|

			 Currency
		      ------------
	Definition: Element [Array] (Reihenfolge ist WICHTIG)
			
		 Anzahl Münzen 14203
		14203 % 10 = 3 Kupfer
		14203 / 10 = 1420

		1420 % 100 = 20 Silber
		1420 / 100 = 14

		14 % 1000 = 14 Gold

_______________________________________________________________________

			
			|Code:|

internal class Element
    {
        public string Name;
        public int Divisor;
    }
    class Currency 
    {
        private List<Element> Definition;
        
        public Currency()
        {
            Definition = new List<Element>();
        }

        public void AddDefinition(string name, int divisor = int.MaxValue)
        {
            Element element = new Element();
            element.Name = name;
            element.Divisor = divisor;
            Definition.Add(element);
        }

        public string Decompose(int amount)
        {
            string output = "";
            //12014

           for (int i = 0; i < Definition.Count; i++)
            {
                Element e = Definition[i];
                int fraction = amount % e.Divisor;

                if(fraction > 0)
                {
                    output = amount % e.Divisor + " " + e.Name + " " + output;
                    amount /= e.Divisor;
                }
            }
            if (output.Trim().Length == 0)
                output = "Kein Wert";
            return output;
        }

    }

_______________________________________________________________________

 class Program
    {
       

        static void Main(string[] args)
        {
            Currency lunz = new Currency();
            lunz.AddDefinition("Kupfer", 10);
            lunz.AddDefinition("Silber", 100);
            lunz.AddDefinition("Gold", 1000);
            lunz.AddDefinition("Diamant");

            Console.WriteLine(lunz.Decompose(Anzahl der Münzen));


            Console.ReadKey();

        }
    }
_______________________________________________________________________
