
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

_______________________________________________________________________


Softwaretechnik
_______________________________________________________________________

Entwickler: 

setzen konkrete vorgaben um

arbeiten problemorientiert

zumeist reine coder 

verdienst 15-26k Euro

_______________________________________________________________________

Software Engineer:

erarbeitet modelle testfälle konzepte

involviert in projektmanagmet, Anforderungsmanagment und QA

wie der Entwickler involviert in Coding, Testing und Entwicklung

Arbeitet auf höherem Abstraktionsniveau

gehalt: 40 - 66k Euro

_______________________________________________________________________


Software Architekt:

trifft grundlegende Entscheidungen

Konzipiert bei großen Projekten Systeme und das Zusammenspiel der Komponenten

arbeitet auf nochmals höherem Abstraktionsniveau

Arebiette potentiell projekt-,team- systemübergreifend

Gehalt: 36-55k Euro

_______________________________________________________________________

Projektplanung

Anforderungs Management

Risiko Management

Teamorganisiation

Code Design

Testing

Deplyment (wie baue ich meine software aus)

Wartung & Lifecycle Management 

_______________________________________________________________________

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
_______________________________________________________________________
_______________________________________________________________________
_______________________________________________________________________
_______________________________________________________________________



20.11.2017 Hummes

__________________________________________________________________________________

"for( ; n > 0; c++, n&=(n-1)){}"

das ";" hinter dem for, darf weg gelassen werden, da keine gegebene häufigkeit des schleifendruchlaufs gegeben ist. 

Bit weise Und = &
schnelle möglichkeit für die CPU

__________________________________________________________________________________

!!!!!!!!!!!!!!!!!!!Erste Abgabe 07.12.2017 23:59 Uhr!!!!!!!!!!!!!!!!!!!!


Thema: WeightedPicker
Problemstellung: Arbeiten mit gewichteten Wahrscheinlichkeiten
		 Spawning von Gegnern mit unterschiedlicher Häufigkeit("Rare-Mobs")
		 Erzeugen von Item-Drops mit unterschiedlichen Häufigkeiten("Epic-Loot")

Aufgabenstellung:
Programmiert eine Datenstruktur, die Elemente mit einem zugeordneten Wert aufnehmen kann.
Intern werden die Werte in passender Relation umgerechnet. ein Pick()-Methode
liefert dann ein zufälliges Element unter der Berücksichtigung der relativen Wahrscheinlichkeit.



Tipp:
Mit Zahlenwerten Prüfen, doch am ende zahlen durch variable "T" ersetzen

 public static class Helper
    {
        public static void Shuffle<T>( this T[] array)
        {
            int n = array.Length;
            Random random = new Random();
            for(int i = 0; i < n; i++)
            {
                int r = i + random.Next(n - i);
                T t = array[r];
                array[r] = array[i];
                array[i] = t;
                   
            }
        }
    }



__________________________________________________________________________________



__________________________________________________________________________________

Conways Game of Life:

1. Feld erzeugen mehrdemansionales Array

2. Zellen erzeugen welche leben und sterben (Boole true, false)
	wenn die Zelle lebt steht sie auf "true" und wird mit einem Wert oder einem Zeichen ausgegeben. z.B. "o". Auf "false" wird
	nichts angezeigt.

	2.1. die Regeln:        Eine leere Zelle mit 2 lebenden Nachbarn wird in der Folgegeneration neu geboren.
        			Eine lebende Zelle mit weniger als zwei lebenden Nachbarn stirbt in der Folgegeneration an Einsamkeit.
        			Eine lebende Zelle mit zwei oder drei lebenden Nachbarn bleibt in der Folgegeneration unverändert.
        			Lebende Zellen mit mehr als drei lebenden Nachbarn sterben in der Folgegeneration an Überbevölkerung. 

__________________________________________________________________________________

Mitschrift Tafel
Board erstellen
	Fill
	Rendern
	while(true)
		für JEDES einzelne Feld, Anzahl der Nachbarn bestimmen == Move/Update
		-> Zelle lebt/stirbt 
		Flip (Nächste Generation wird zur Aktuellen und umgekehrt)
		Render
		(ResetCursor)

Console
		

__________________________________________________________________________________

!!!!!!!!!!!!!!!!!!!!!!!!!!!!Nacharbeiten!!!!!!!!!!!!!!!!!!!!!!!!!!!!
__________________________________Code____________________________________________

__________________________________________________________________________________

25.11. 
__________________________________________________________________________________
Shader Hard Surface

Code: 

Shader "Silhouette"

{

	Properties
	{
		_Color("Color", Color) = (1, 1, 1, 0.5)

	}

	SubShader
	{
		Tags { "Queue" = "Transparent" }
		Pass
		{
			ZWrite Off
			Blend SrcAlpha OneMinusSrcAlpha
			CGPROGRAM

			#pragma vertex vert
			#pragma fragment frag

			float4 _Color;
			
			struct vertexInput
			{
				float4 vertex : POSITION;
				float3 normal : NORMAL;
			};

			struct vertexOutput 
			{
				float4 pos : SV_POSITION;
				float3 normal : TEXCOORD;
				float3 viewDir : TEXCOORD1;
			};

			vertexOutput vert(vertexInput input)
			{
				
				vertexOutput output; 

				output.pos = UnityObjectToClipPos(input.vertex);
				output.normal = normalize(mul(float4(input.normal, 0.0), unity_WorldToObject).xyz);
				output.viewDir = normalize(_WorldSpaceCameraPos - mul(unity_ObjectToWorld, input.vertex).xyz);
				return output;
			}

			float4 frag(vertexOutput input) : COLOR
			{
				float3 normalDirection = normalize(input.normal);
				float3 viewDirection = normalize(input.viewDir);

				float newAlpha = min(1.0, _Color.a / abs(dot(viewDirection, normalDirection)));

				return float4(_Color.rgb, newAlpha);
			}

			ENDCG
		}
	}
}






