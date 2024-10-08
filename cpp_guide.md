
---

<h2 style="text-align: center;"><b>Livello Beginner</b></h2>

---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### I commenti

</div>

I commenti sono delle parti di testo inserite nel codice il cui unico scopo è quello di fornire informazioni sul codice, vengono ignorati dal compilatore e perciò non influiscono sull'esecuzione del programma.

Per scrivere un commento si può precedere la frase dal simbolo ```//``` oppure racchiudere la frase tra ```\*``` e ```*\```.

Esempio:

```cpp
// questo è un commento su una riga
/*
    questo è un commento
    su più righe
*/
/* questo è un altro commento */
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le basi del linguaggio C++

</div>

<div style="text-align: center;">

#### ***Hello World***

</div>

Ecco un semplice programma che scrive “Hello World!”:

```cpp
#include <iostream>

int main()
{
    std::cout << "Hello, World!";

    return 0;
}
```

<div style="text-align: center;">

#### ***Spiegazione***

</div>

**```iostream```** (input output stream) è un file esterno, che è necessario includere per usare **```std::cout```**.

**```main```** rappresenta il programma, e contiene ciò che deve essere eseguito, **```int```** segnala che il tipo restituito dalla funzione è un numero intero.

**```return 0```** termina il programma con codice 0 che significa che non si sono verificati errori.

**```std```** è uno spazio di nomi che contiene l'oggetto **```cout```**, si scrive **```std::```** prima di ```cout``` per indicare che ```cout``` appartiene allo spazio di nomi ```std``` (standard).

**```std::cout```** è utilizzato per scrivere nella console, in questo caso ```Hello, World!```, le cose da scrivere sono concatenate con l'operatore ```<<```.

Il punto e virgola dopo ```Hello, World!``` indica che l'istruzione è terminata, infatti il compilatore distingue le istruzioni grazie al punto e virgola e non al carattere di nuova linea.

```#include <iostream>``` non ha un punto e virgola alla fine perché è una direttiva, si possono riconoscere le direttive perché iniziano con ```#```.

<div style="text-align: center;">

#### ***```using namespace std```***

</div>

Esiste un modo per evitare di scrivere ```std::``` prima di ogni variabile\funzione\enumerazione\unione\struttura\classe\oggetto dello spazio di nomi standard:

```cpp
using namespace std;
```

<div style="page-break-after: always;"></div>

In questo caso il programma diventa:

```cpp
#include <iostream>
using namespace std;
int main()
{
    cout << "Hello, World!";
    return 0;
}
```

In questa guida non useremo ```using namespace std``` perché in questo modo è più chiaro.

Un'alternativa preferibile a ```using namespace std``` potrebbe essere questa:

```cpp
using std::cout;
```

Oppure:

```cpp
using std::cout, std::cin;
```

Chiaramente scrivendo ciò la regola vale SOLO per gli variabili\funzioni\enum\unioni\strutture\classi\oggetti riportati dopo **```using```**

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### L'output (o stampa a video)

</div>

In C++ esistono quattro oggetti principali per eseguire l'output:
**```cout```**, **```cerr```**, **```wcout```**, **```wcerr```**.  
(```cout``` = c output, ```cerr``` = c error, ```wcout``` = wide c output, ```wcerr``` = wide c error).

```cout``` e ```wcout``` sono usati per l'output normale mentre ```cerr``` e ```wcerr``` sono usati per i messaggi di errore,  
```cout``` e ```cerr``` sono usati con le stringhe normali e ```wcout``` e ```wcerr``` con stringhe larghe, vale a dire stringhe che supporatano una maggiore quantità di caratteri (come ad esempio lettere accentate).

Esempio:

```cpp
#include <iostream>
int main()
{
    std::cout <<  "questa e' una stringa normale"        << std::endl;
    std::cerr <<  "questa e' una stringa di errore"      << std::endl;

    setlocale(0, "");

    std::wcout << L"questa è una stringa wide"           << std::endl;
    std::wcerr << L"questa è una stringa wide di errore" << std::endl;

    return 0;
}
```

Notare l'aggiunta di ```L``` prima delle stringhe wide, in generale bisogna aggiungere **```setlocale(0, "");```** solo una volta prima di usare stringhe wide, ed è buona pratica non mescolare ```cout``` con ```wcout``` o ```cerr``` con ```wcerr```.

**```std::endl```** (end of line) serve per andare a capo.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le sequenze di escape

</div>

Le sequenze di escape rappresentano dei caratteri speciali non stampabili:

+ **```\n```**: aggiunge una nuova riga (va a capo)
+ ```\r```: sposta il cursore all'inizio della riga
+ ```\b```: carattere backspace
+ ```\a```: suono di errore
+ ```\t```: tab
+ ```\\```: carattere backslash
+ ```\"```: virgolette (per distinguerle da quelle che delimitano la stringa)
+ ```\'```: apice (viene è usato per delimitare un singolo carattere invece di una stringa)
+ ```\0```: carattere nullo (non uno spazio)

Ha particolare importanza ```\n```, che è un'alternativa in genere preferibile a ```std::endl```.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### La tabella ASCII

</div>

La tabella ASCII assegna un numero a ogni carattere:

<br><br><br><br><br><br><br><br><br><br>
<br><br><br><br><br><br><br><br><br><br>
<br><br><br>

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### I datatype

</div>

I datatype sono i tipi tra cui bisogna scegliere quando si dichiara una variabile, esistono dei datatype primari, forniti dal linguaggio C++, e datatype secondari che possono essere definiti nei file header esterni oppure direttamente nel codice.

<div style="text-align: center;">

#### ***I datatype primari***

</div>

Tipi interi:

+ **```__int16```**: un intero compreso tra -32.768 e 32.767
+ **```__int32```**: un intero compreso tra -2.147.483.648 e 2.147.483.647
+ **```__int64```**: un intero compreso tra -2^63 e 2^63 - 1

+ **```short```**: ```__int16```
+ **```int```**: ```__int32```
+ **```long```**: di solito ```__int32```, ma su alcuni sistemi ```__int64```
+ **```long long```**: ```__int64```

Tipi decimali:

+ **```float```**: un numero decimale con precisione di 6 o 7 cifre decimali
+ **```double```**: un numero decimale con precisione di 15-16 cifre decimali
+ **```long double```**: varia, ma in genere ha una precisione decimale di 18-19 cifre

Altro:

+ **```char```**: un carattere
+ **```bool```**: può essere solo vero (```true``` o 1) oppure falso (```false``` o 0)

E' possibile aggiungere la parola chiave **```unsigned```** prima del tipo, in questo modo il datatype non potrà mai contenere valori negativi, ma può contenere valori positivi con un range doppio

Esempio:

```__int64``` va da **-9.223.372.036.854.775.808** a **9.223.372.036.854.775.807**,  
ma ```unsigned __int64``` va da **0** a **18.446.744.073.709.551.615**.

<div style="text-align: center;">

#### ***I ```typedef``` e gli alias***

</div>

Per definire un datatype secondario è possibile utilizzare un ```typedef```:  
**typedef *\<datatype\>* *\<nome\>*;**

Esempio:

```cpp
typedef unsigned long long size_t;
```

Qui si definisce **```size_t```** come ```unsigned long long```.

Esiste un altro modo (alias) per definire un datatype secondario con la parola chiave **```using```**:  
**using *\<nome\>* = *\<datatype\>*;**

L'esempio di prima diventa

```cpp
using size_t = unsigned long long;
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le variabili e le costanti

</div>

<div style="text-align: center;">

#### ***Che cosa sono***

</div>

In C++ le variabili vengono dichiarate con questa sintassi:  
***\<datatype\>* *\<nome\>*;**

In questo modo si dichiara una variabile che però non ha un valore, a cui si può assegnare un valore con l'inizializzazione:  
***\<datatype\>* *\<nome\>* = *\<espressione\>*;**

Il nome di una qualsiasi cosa (non solo una variabile) può contenere solo lettere, numeri o underscore (```_```) e non può iniziare con un numero.  
Il C++ è un linguaggio **case sensitive** cioè esiste una differenza tra le lettere minuscole e quelle maiuscole.

Per dichiarare una costante bisogna aggiungere la parola chiave **```const```** all'inizio ed è obbligatorio assegnare un valore:  
**const *\<datatype\>* *\<nome\>* = *\<espressione\>*;**

Le variabili possono cambiare il loro valore durante l'esecuzione del programma, al contrario delle constanti.

<div style="text-align: center;">

#### ***Inizializzazione***

</div>

Si può usare la parola chiave **```auto```** al posto del datatype, dove il compilatore proverà a dedurre il tipo dall'espressione, perciò è obbligatorio assegnare un valore, ad esempio è errato scrivere:

```cpp
auto Variable;
const double Pi;
```

Ma è corretto scrivere:

```cpp
auto Variable = 1;
const double Pi = 3.1415926535;
int NewVariable = Variable;
long lines;
```

Se due o più variabili sono dichiarate con lo stesso datatype si può usare una virgola per separarle e scrivere una sola volta il datatype:

```cpp
int A = 1, B = 2, _i, __i;
```

Esistono altri due modi per inizializzare le variabili, l'inizializzazione per copia e uniforme, ma il datatype dell'espressione deve essere uguale a quello della variabile:  

Inizializzazione per copia:

```cpp
int A(1), B(2);
```

Inizializzazione uniforme:

```cpp
int A{ 1 }, B{ 2 };
```

Nell'inizializzazione uniforme si può omettere il valore tra le parentesi:

```cpp
int x{}; // stessa cosa di int x{ 0 };
```

<div style="text-align: center;">

#### ***Cambiare il valore***

</div>

Per cambiare il valore di una variabile si può usare l'operatore **```=```**, esempio:

```cpp
x = 1; // vuol dire "x è impostato a 1" non "x è uguale a 1"
```

Vediamo come è possibile scambiare il valore di due variabili:

```cpp
int main()
{
    int x = 5, y = 10;

    auto temp = x; // x = 5   y = 10  temp = 5
    x = y;         // x = 10  y = 10  temp = 5
    y = temp;      // x = 10  y = 5   temp = 5

    // x = 10   y = 5

    return 0;
}
```

<div style="text-align: center;">

#### ***L'ambito delle variabili***

</div>

In C++ una variabile viene creata con una dichiarazione e distrutta quando esce dal proprio ambito, che è definito dalle parentesi graffe, una variabile dichiarata fuori da una funzione si dice **globale** mentre una variabile dichiarata in una funzione si dice **locale**.

Se due variabili, una locale e una globale hanno lo stesso nome ma ambiti diversi, è possibile utilizzare l'**operatore di risoluzione dell'ambito ```::```** per accedere a quella globale, ciò funziona anche con le funzioni, o con una funzione e una variabile:

<div style="page-break-after: always;"></div>

```cpp
#include <iostream>
const double       Variable = 10.2; // variabile globale

int main()
{
    int Variable = 7;
    std::cout <<   Variable << '\n'; // output = 7
    std::cout << ::Variable << '\n'; // output = 10.2

    return 0;
}
```

In questo caso abbiamo due variabili con lo stesso nome, una locale e una globale, possiamo accedere a quella locale con ```variable``` e a quella globale con ```::variable```.

Due variabili non possono avere lo stesso nome all'interno dello stesso ambito.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Namespace

</div>

In C++ un namespace si dichiara con questa sintassi:

**namespace *\<nome\>*
{  
    *\<variabili, funzioni, enum, unioni, strutture, classi, oggetti\>*  
}**

Esempio:

```cpp  
namespace MyNamespace
{
    const int lenght = 10;
    const double e = 2.7182182;
}
```

Per accedere alle variabili di un namespace dall'esterno si precede la variabile dal nome del namespace e dall'operatore di risoluzione dell'ambito oppure si può usare ```using namespace```:

```cpp
int main()
{
    auto locallenght = MyNamespace::lenght;

    using namespace MyNamespace;
    auto const_e = e; // invece di usare MyNamespace::e

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### L'input utente

</div>

In C++ l'input viene eseguito con **```std::cin```**, necessario includere  **```<iostream>```**:

```cpp
#include <iostream>

int main()
{
    int Number1, Number2;
    std::cin >> Number1 >> Number2;

    return 0;
}
```

In questo modo l'utente inserisce da console due valori per le variabili Number1 e Number2, tuttavia l'input si blocca se l'utente inserisce dei caratteri, ma per risolvere questo si può eseguire l'input con una stringa e poi convertirla in numero (vedi stringhe).

E' buona pratica inserire sempre un output prima di ogni input per far capire all'utente cosa deve fare:

```cpp
#include <iostream>

int main()
{
    int Number1;
    std::cout << "inserisci un numero\n";
    std::cin >> Number1;
    std::cout << "hai inserito: " << Number1;
    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Gli operatori matematici

</div>

In C++ ci sono 5 operatori matematici **primari (```+```, ```-```, ```*```, ```/```, ```%```)**, 5 operatori matematici **composti (```+=```, ```-=```, ```*=```, ```/=```, ```%=```)** e 2 operatori **unari (```++``` e ```--```)**.

<div style="text-align: center;">

#### ***Gli operatori matematici primari***

</div>

Gli operatori **(```+```, ```-```, ```*```, ```/```)** indicano rispettivamente addizione, sottrazione, moltiplicazione e divisione.  
L'operatore **```%```** indica il resto della divisione intera.

Gli operatori **```*```, ```/```** e **```%```** hanno la precedenza sugli operatori **```+```** e **```-```**.

Esempio di utilizzo:

```cpp
#include <iostream>

int main()
{
    int A = 10, B = 5;

    std::cout << A + B << '\n'; // output = 15
    std::cout << A - B << '\n'; // output = 5
    std::cout << A * B << '\n'; // output = 50
    std::cout << A / B << '\n'; // output = 2
    std::cout << A % B << '\n'; // output = 0

    return 0;
}
```

Gli operatori composti e unari abbreviano alcune espressioni:

<div style="text-align: center;">

#### ***Gli operatori matematici composti***

</div>

```cpp
    Var += i;   // Var = Var + i
    Var -= i;   // Var = Var - i
    Var *= i;   // Var = Var * i
    Var /= i;   // Var = Var / i
    Var %= i;   // Var = Var % i
    Var++;      // Var = Var + 1
    Var--;      // Var = Var - 1
    ++Var;      // Var = Var + 1
    --Var;      // Var = Var - 1
```

<div style="text-align: center;">

#### ***Gli operatori unari***

</div>

Tuttavia esiste una leggera differenza tra ```++Variabile``` e ```Variabile++``` e tra ```--Variabile``` e ```Variabile--```:

<div style="page-break-after: always;"></div>

```cpp
    int Var, i;

    // prima si incrementa i, quindi si assegna il risultato a Var
    // i = 3 --> i = 4 --> Var = 4
    i = 3;
    Var = ++i;

    // prima si assegna il risultato a Var, quindi si incrementa i
    // i = 3 --> Var = 3 --> i = 4
    i = 3;
    Var = i++;
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### La conversione tra datatype

</div>

Alcune volte può essere necessario effettuare la conversione tra due datatype, in C++ esistono vari modi per fare ciò, ma qui ne vedremo solo due: il **type cast** e lo **static cast**.

<div style="text-align: center;">

#### ***Il type cast***

</div>

Il type cast può effettuare qualsiasi tipo di conversione.  
**(*\<datatype\>*)*\<espressione\>***  
oppure  
__*\<datatype\>*(*\<espressione\>*)__

Esempio: divisione decimale tra due interi

```cpp
#include <iostream>

int main()
{
    const int A = 7, B = 5;
    std::cout << A / B << '\n'; // output = 1
    std::cout << double(A) / B; // output = 1.4

    return 0;
}
```

Nel primo output viene visualizzato 1 (un intero) perché entrambi i numeri sono interi; ma nel secondo, ```A``` viene convertito in double, e quindi anche il risultato sarà double: 1.4.

<div style="text-align: center;">

#### ***Lo static cast***

</div>

E' preferibile utilizzare lo **static cast** quando possibile, perché è più sicuro consentendo solo conversioni ben definite: **static_cast< *\<datatype\>* >(*\<espressione\>*);**

```cpp
#include <iostream>

int main()
{
    const int A = 7, B = 5;
    std::cout << A / B << '\n';
    std::cout << static_cast<double>(A) / B;

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### I concetti di base delle stringhe

</div>

In C++ una stringa è un datatype secondario per una variabile che contiene del testo, esistono due classi per questo dette **```std::string```** e **```std::wstring```**, per usare le stringhe bisogna includere **```<string>```**.

<div style="text-align: center;">

#### ***Output***

</div>

Esempio:

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string   str =  "questa e' una stringa";
    std::wstring wstr = L"questa è una stringa wide";

    std::cout  <<  str <<  '\n';

    setlocale(0, "");
    std::wcout << wstr << L'\n';
    return 0;
}
```

Se si vuole una stringa di caratteri uguali e lunghezza finita si può fare così:

```cpp
std::string  str(5, ',');  // stessa cosa di std::string str = ",,,,,";
std::string wstr(9, L','); // stessa cosa di std::string str = L",,,,,,,,,";
```

<div style="text-align: center;">

#### ***Input***

</div>

Si esegue l'input di una stringa normale con ```std::cin``` e quello di una stringa wide con **```std::wcin```**:

```cpp
#include <iostream>
#include <string>

int main()
{
    setlocale(0, "");

    std::string str;
    std::wstring wstr;

    std::cout << "inserisci due stringhe\n";
    std::cin >> str;
    std::wcin >> wstr;

    std::cout  << str  <<  '\n';
    std::wcout << wstr << L'\n';

    return 0;
}
```

Tuttavia c'è un problema: ```std::cin``` e ```std::wcin``` fermano l'input non appena leggono un carattere di spazio, ma questo si risolve con la funzione **```std::getline```**:

```cpp
#include <iostream>
#include <string>

int main()
{
    setlocale(0, "");

    std::string str;
    std::wstring wstr;

    std::cout << "inserisci due stringhe\n";
    std::getline(std::cin, str);
    std::getline(std::wcin, wstr);

    std::cout  << str  << '\n';
    std::wcout << wstr << '\n';

    return 0;
}
```

<div style="text-align: center;">

#### ***Input senza ```cin```***

</div>

Esiste un altro modo per eseguire l'input di un carattere, che è strettamente legato alle stringhe, con il file header **```<conio.h>```**:

+ **```_getch()```** legge un carattere dalla tastiera senza scriverlo sullo schermo (al contrario di **```_getche()```**), e non un carattere wide al contrario di **```_getwch()```**:

```cpp
#include <conio.h>

int main()
{
    _getch(); // ferma il programma fino a quando un carattere viene premuto
    return 0;
}
```

<div style="page-break-after: always;"></div>

```cpp
#include <conio.h>

int main()
{
    char c = _getch(); // legge un carattere e lo assegna a c
    return 0;
}
```

Molto importante anche la funzione **```_kbhit()```** (non ```_kbhit```), che resituisce ```true``` se un carattere è stato premuto ed è in attesa di essere letto da una funzione di input:

```cpp
#include <conio.h>
#include <iostream>

int main()
{
    if (_kbhit()) {
        char c = _getch();
        std::cout << "hai premuto " << c;
    }

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le istruzioni IF-ELSE

</div>

<div style="text-align: center;">

#### ***Che cos'è***

</div>

Un'istruzione if-else è un modo per eseguire determinate parti di codice in base alla verità di una condizione:

**if (*\<condizione\>*) {  
    *\<istruzioni da eseguire se la condizione è vera\>*  
}  
else {  
    *\<istruzioni da eseguire se la condizione è falsa\>*  
}**

Ecco un esempio di if-else, un programma per indicare il segno di un numero:

```cpp
#include <iostream>

int main()
{
    long long Number;
    std::cin >> Number;

    if (Number > 0) {
        std::cout << "il numero e' positivo\n";
    }
    else if (Number < 0)
    {
        std::cout << "il numero e' negativo\n";
    }
    else std::cout << "il numero e' 0\n";

    return 0;
}
```

<div style="text-align: center;">

#### ***Le parentesi graffe***

</div>

Qui possiamo vedere i 3 principali stili di un if-else quanto a parentesi graffe, che valgono anche per i **cicli**, che saranno descritti in seguito:  

+ con la parentesi graffa aperta davanti alla condizione
+ con le parentesi graffe a capo
+ senza parentesi graffe, tuttavia deve essere presente una sola istruzione

<div style="page-break-after: always;"></div>

E' anche possibile annidare due istruzioni if in questo modo:

```cpp
    if (Number > 0)
        if (Number % 2 == 0)
        {
            Number++;
            std::cout << Number;
        }
```

Qui vediamo che il primo if non ha le parentesi graffe, questo perché al suo interno c'è un solo if, nonostante le due istruzioni all'interno di quest'ultimo if.

<div style="text-align: center;">

#### ***Gli operatori***

</div>

Negli if vengono usati gli **operatori di confronto** e gli **operatori logici**:

Operatori di confronto:  

+ **```<```**: minore di,
+ **```<=```**: minore o uguale di,
+ **```==```**: uguale a,
+ **```>=```**: maggiore o uguale di,
+ **```>```**: maggiore di,
+ **```!=```**: diverso da.

Operatori logici:

+ **```&&```** o **```and```**: AND logico (il risultato è vero se e solo se entrambi gli input sono veri)
+ **```||```** o **```or```**: OR logico (il risultato è vero se uno dei due input è vero)
+ **```!```** o **```not```**: NOT logico (il risultato è vero se e solo se l'input è falso)  
Per lo XOR logico si utilizza l'operatore ```!=```.

Grazie agli operatori logici i due if precedenti si possono compattare così:

```cpp
    if (Number > 0 && Number % 2 == 0)
    {
        Number++;
        std::cout << Number;
    }
```

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Gli IF-ELSE e le eccezioni***

</div>

Tuttavia esistono dei casi in cui è meglio usare due if invece di uno solo, come in questo esempio:

```cpp
#include <iostream>

int main()
{
    int A, B;
    std::cin >> A >> B;

    if (B != 0) if ((A / B) % 2 == 1)
    {
        A--;
        B++;
    }

    return 0;
}
```

L'espressione ```(A / B) % 2 == 1``` non può essere eseguita se ```B``` è 0, e solleverebbe un'**eccezione ```std::invalid_argument```**, per prevenire ciò bisogna controllare che ```B``` sia diverso da 0 PRIMA dell'elaborazione dell'espressione e non nella stessa istruzione if.

<div style="text-align: center;">

#### ***Gli IF-ELSE e l'assegnazione***

</div>

Nella condizione degli if si può anche assegnare un valore a una variabile, poi si controlla se il risultato non è nullo.

```cpp
#include <iostream>

int main()
{
    int x;
    
    if (x = 5)  // 5 viene assegnato a x, poi si verifica se x non è nullo
        std::cout << "5 è stato assegnato a x\n";
    
    return 0;
}
```

<div style="page-break-after: always;"></div>

Per questo bisogna fare attenzione a non confondere gli operatori ```==``` e ```=``` perché non ci sarà nessun errore di compilazione in caso di assegnazione accidentale dentro un if.  
Per evitare questo errore può aiutare scrivere:

```cpp
    if (1 == x) // if (1 = x) è un errore: non si può assegnare a un numero
```

Invece di:

```cpp
    if (x == 1) // if (x = 1) non genera l'errore
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### L'operatore ternario

</div>

In C++ esiste un'alternativa rispetto alle istruzioni if-else detta operatore ternario.  
***\<condizione\>* ? *\<se vero\>* : *\<se falso\>*;**

<div style="text-align: center;">

#### ***Senza assegnazione***

</div>

Esempio: programma per trovare l'inverso di un numero

```cpp
#include <iostream>

int main()
{
    long long   number;
    std::cin >> number;

    number == 0 ?
        std::cout << "non e' possibile dividere per 0\n" :
        std::cout << "l'inverso e' " << 1.0 / number << '\n';

    return 0;
}
```

<div style="text-align: center;">

#### ***Con l'assegnazione***

</div>

E' possibile utilizzare l'operatore ternario per assegnare un valore, qui viene riportato un programma per calcolare il massimo tra due numeri:

```cpp
#include <iostream>

int main()
{
    int A, B;
    std::cout << "inserisci due numeri\n";
    std::cin >> A >> B;

    int max = A > B ? A : B;
    std::cout << "il massimo e' " << max;

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Gli operatori bitwise

</div>

**Attenzione**: è necessario conoscere come funziona il codice binario.

In C++ esistono degli operatori detti **bitwise** che eseguono delle operazioni logiche su ogni bit di uno o due numeri scritti in codice binario.

Supponiamo di avere due variabili A = 9 e B = 10  
Riscrivendoli in binario otteniamo A = 1001 e B = 1010

Vediamo come si comporta ciascun operatore bitwise con A e B:

**BITWISE AND**  
Si esegue l'AND logico su ogni bit rispettivamente:  
```A & B``` = ```1001 & 1010``` = 1000 = 8 (in base 10)

**BITWISE OR**  
Si esegue l'OR logico su ogni bit rispettivamente:  
```A | B``` = ```1001 | 1010``` = 1011 = 11 (in base 10)

**BITWISE NOT**  
Si inverte ogni bit di un numero:  
```~A``` = ```~1001``` = 0110 = 6 (in base 10)

**BITWISE XOR**  
Si esegue l'XOR logico su ogni bit rispettivamente:  
```A ^ B``` = ```1001 ^ 1010``` = 0011 = 3 (in base 10)

**LEFT SHIFT**  
Si spostano tutti i bit verso sinistra di tante posizioni quanto lo shift:  
```A << 2``` = ```001001 << 2``` = 100100 = 36 (in base 10)

**RIGHT SHIFT**
Si spostano tutti i bit verso destra di tante posizioni quanto lo shift:  
```B >> 1``` = ```1010 >> 1``` = 0101 = 5 (in base 10)

Ovviamente esistono anche gli operatori **```&=```, ```|=```, ```^=```, ```<<=``` e ```>>=```**:  
**A = A *\<operatore\>* B → A *\<operatore\>*= B**

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### L'istruzione GOTO

</div>

In C++ esiste un modo per trasferire il controllo a una certa istruzione quando ci si trova a un certo punto del codice, per fare questo si utilizza un **```goto```**.  
**Attenzione**: utilizzare molti goto può rendere il codice poco leggibile.

Esempio di goto:

```cpp
#include <iostream>

int main()
{
    size_t some_number{};
    std::cin >> some_number;

    if (some_number == 0) goto stop;
    else {
        some_number <<= 3;
        std::cout << "eseguito left shift 3 volte\n";
        std::cout << "il numero e' " <<  some_number;
        return 0;
    }

stop:
    std::cout << "il programma e' stato interrotto\n";
    return 1;
}
```

In questo caso se il numero è 0, il controllo viene trasferito al punto ```stop``` da cui termina il programma con codice di errore 1, chiaramente questo è un esempio di goto utilizzato in modo errato, ma era giusto per capire come funziona questa istruzione.

Se tra il goto e l'istruzione del goto, viene inizializzata una variabile, si otterrà un errore di compilazione perché se si trasferisce il controllo viene ignorata l'inizializzazione di quella variabile.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Il ciclo WHILE

</div>

Un ciclo while è una sezione di codice che viene ripetuta finché una condizione rimane vera:

**while (*\<condizione\>*)  
{  
 *\<istruzioni da ripetere\>*  
}**

Può essere utilizzato per creare del codice che si ripete all'infinito, come questo:

```cpp
#include <iostream>

int main()
{
    while (true)
    { 
        size_t some_number{};
        std::cin >> some_number;

        std::cout << "hai inserito il numero ";
        std::cout << some_number << '\n';
    }
}
```

Questo codice ripeterà all'infinito all'utente di inserire un numero, perché la condizione all'interno del ciclo è sempre vera.

<div style="page-break-after: always;"></div>

Ecco un codice che calcola i primi numeri della sequenza di Fibonacci:

```cpp
#include <iostream>

int main()
{
    long long x = 0, y = 1, i{};
    while (y >= 0) {
        std::cout << "numero di Fibonacci #" << i;
        std::cout << " = " << x << '\n';

        auto temp = x + y;
        x = y;
        y = temp;
    }

    std::cout << "numero di Fibonacci #" << i + 1;
    std::cout << " = " << x << '\n';
    std::cout << "si e' verificato un overflow\n";

    return 0;
}
```

Poiché la variabile y è intera, ha un limite, quando il limite viene superato si riparte a contare dal minimo e quindi la variabile diventa negativa, rendendo falsa la condizione del ciclo e di conseguenza si esce dal ciclo.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Il ciclo DO WHILE

</div>

Questo è un ciclo simile al while, con la differenza che qui si verifica la condizione dopo aver eseguito il codice e non prima.

**do {  
 *\<istruzioni da ripetere\>*  
} while (*\<condizione\>*);**

Questo ciclo può essere usato per il controllo dell'input, dove si ripete l'input fino a quando è corretto, ecco un codice che esegue l'input controllato di un numero positivo:

```cpp
#include <iostream>

int main()
{
    int pos_number;
    do {
        std::cout << "inserisci un numero\n";
        std::cin >> pos_number;

        if (pos_number <= 0)
        {
            std::cout << "hai inserito un numero sbagliato!\n";
        }
    } while (pos_number <= 0);

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Il ciclo FOR

</div>

Questo è il ciclo più importante tra quelli visti finora, permette di ripetere un blocco di codice finché una condizione è vera ed eseguendo una certa operazione su di una variabile a ogni iterazione.

**for (*\<inizializzazione variabile\>*; *\<condizione\>*; *\<operazione\>*)  
{  
 *\<istruzioni da ripetere\>*  
}**

Si può lasciare vuota qualsiasi informazione tra le tre presenti.  
Ecco un semplice esempio d'uso del for:

```cpp
#include <iostream>

int main()
{
    int low, high;
    do {
        std::cout << "inserire il limite inferiore\n";
        std::cin >> low;
        std::cout << "inserire il limite superiore\n";
        std::cin >> high;
    } while (low >= high);

    for (int i = low; i <= high; ++i) std::cout << i << '\n';
    return 0; 
}
```

L'iterazione inizia con la variabile ```i``` inizializzata a ```low```, ogni volta che l'iterazione è completata ```i``` aumenta di 1 e l'iterazione continua finché ```i``` è minore o uguale a ```high```, a ogni iterazione si stampa il valore di ```i```.

Vediamo adesso un esempio più complesso: il riempimento di una regione della console con asterischi, l'utente sceglie la posizione della regione e le sue dimensioni:

```cpp
#include <iostream>

int main()
{
    // input dimensioni
    unsigned short X, Y, lenght, width;
    std::cout << "inserire la posizione del primo vertice\n";
    std::cin >> X >> Y;
    std::cout << "inserire la dimensione della regionw\n";
    std::cin >> lenght >> width;

    // riduzione delle dimensioni per evitare l'overflow
    X %= 50;
    Y %= 50;
    lenght %= 50;
    width %= 50;

    // spostamento in giù
    for (int i = 0; i < Y; ++i) std::cout << '\n';

    // output di ogni riga
    auto limitX(lenght + X);
    for (int i = 0; i < width; ++i) {
        
        // spostamento di lato
        int j{};
        for (; j < X; ++j) std::cout << ' ';

        // output asterischi
        for (; j < limitX; ++j) std::cout << '* ';

        // termine riga
        std::cout << '\n';
    }

    return 0;
}
```

Possiamo vedere i due for all'interno del for più grande, che usano la stessa variabile ```j``` (è la stessa perché dichiarata fuori dal for), come per dimostrare che non è necessario fornire tutte e 3 le informazioni del for.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le parole chiave ```break``` e ```continue```

</div>

In C++ l'utilizzo dei cicli è reso più semplice dalle parole chiave ```break``` e ```continue```: un'istruzione ```break``` esce dal ciclo mentre ```continue``` salta il giro, vediamo come si possono utilizzare con questo esempio:

```cpp
#include <iostream>

int main()
{
    for (double i = -1.0;; i += 1.35)
    {
        if (i > 10) i /= 10;
        if (int(i) == 0) continue;

        double number;
        std::cout << "inserisci un numero\n";
        std::cin >> number;

        if (number == i) continue;
        i += number;

        if (i > 100) {
            std::cout << "hai inserito un numero troppo grande\n";
            break;
        }
    }

    std::cout << "fine\n";
    return 0;
}
```

In questo programma l'utente deve indovinare il valore della variabile ```i``` per terminare il programma, e il valore cambia a ogni iterazione, un'istruzione **```continue```** viene utilizzata per saltare ogni iterazione dove ```i``` è vicino a 0, e due istruzioni **break** sono utilizzate per uscire dal ciclo se l'utente indovina il numero o se il numero suggerito è troppo grande.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### L'istruzione SWITCH

</div>

In C++ esiste un'istruzione detta ```switch``` che è un'alternativa più veloce delle istruzioni if-else, tuttavia se le ottimizzazioni del compilatore sono attivate, il tempo di esecuzione rimane lo stesso, è utile quando ci sono molti if-else.

**switch(*\<espressione\>*) {  
case *\<caso_1\>*:  
 *\<istruzioni\>*  
    break;  
…  
case *\<caso_n\>*:  
 *\<istruzioni\>*  
    break;  
default:  
 *\<istruzioni\>*  
}**

L'espressione deve essere di tipo integrale (intero o carattere).  
Ecco due codici equivalenti, uno con gli if-else, l'altro con uno switch:

```cpp
#include <iostream>

int main()
{
    int month;
    std::cout << "inserisci un numero di mese\n";
    std::cin >> month;

    if      (month == 1)  std::cout << "e' gennaio\n";
    else if (month == 2)  std::cout << "e' febbraio\n";
    else if (month == 3)  std::cout << "e' marzo\n";
    else if (month == 4)  std::cout << "e' aprile\n";
    else if (month == 5)  std::cout << "e' maggio\n";
    else if (month == 6)  std::cout << "e' giugno\n";
    else if (month == 7)  std::cout << "e' luglio\n";
    else if (month == 8)  std::cout << "e' agosto\n";
    else if (month == 9)  std::cout << "e' settembre\n";
    else if (month == 10) std::cout << "e' ottobre\n";
    else if (month == 11) std::cout << "e' novembre\n";
    else if (month == 12) std::cout << "e' dicembre\n";
    else                  std::cout << "quello non e' un mese\n";

    return 0;
}
```

<div style="page-break-after: always;"></div>

```cpp
#include <iostream>

int main()
{
    int month;
    std::cout << "inserisci un numero di mese\n";
    std::cin >> month;

    switch (month) {
    case 1:  std::cout << "e' gennaio\n";
        break;
    case 2:  std::cout << "e' febbraio\n";
        break;
    case 3:  std::cout << "e' marzo\n";
        break;
    case 4:  std::cout << "e' aprile\n";
        break;
    case 5:  std::cout << "e' maggio\n";
        break;
    case 6:  std::cout << "e' giugno\n";
        break;
    case 7:  std::cout << "e' luglio\n";
        break;
    case 8:  std::cout << "e' agosto\n";
        break;
    case 9:  std::cout << "e' settembre\n";
        break;
    case 10: std::cout << "e' ottobre\n";
        break;
    case 11: std::cout << "e' novembre\n";
        break;
    case 12: std::cout << "e' dicembre\n";
        break;
    default: std::cout << "quello non e' un mese\n";
    }

    return 0;
}
```

E' molto importante l'utilizzo di ```break``` perché tutte le etichette **```case```** dello switch sono come dei goto, quindi il programma trasferirà il controllo all'etichetta giusta, ma per evitare di svolgere tutte le altre istruzioni sotto, bisogna uscire dallo switch.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Alcune funzioni esterne utili

</div>

<div style="text-align: center;">

#### ***Per gli interi***

</div>

+ **```std::swap```** scambia il valore di due variabili, necessario includere **```<algorithm>```**:

```cpp
#include <algorithm>
#include <iostream>

int main()
{
    int A = 1, B = 2;
    std::swap(A, B);
    //  A = 2, B = 1

    return 0;
}
```

+ **```std::min```** e **```std::max```** calcolano il minimo e il massimo tra due variabili:

```cpp
#include <iostream>

int main()
{
    int A, B;
    std::cin >> A >> B;

    std::cout << "il minimo e' "  << std::min(A, B) << '\n';
    std::cout << "il massimo e' " << std::max(A, B) << '\n';
    return 0;
}
```

<div style="text-align: center;">

#### ***Per i caratteri***

</div>

+ ```isalpha``` permette di controllare se un carattere è alfabetico
+ ```isdigit``` controlla se un carattere è numerico
+ ```isalnum``` controlla se un carattere è alfanumerico
+ ```tolower``` e ```toupper``` trasformano un carattere nelle sue versioni in minuscolo o maiuscolo rispettivamente

<div style="page-break-after: always;"></div>

```cpp
#include <iostream>

int main()
{
    char character;
    do {
        std::cout << "inserisci una lettera\n";
        std::cin >> character;
    } while (!isalpha(character));

    std::cout << "la lettera in minuscolo e' ";
    std::cout << tolower(character) << '\n';

    std::cout << "la lettera in maiuscolo e' ";
    std::cout << toupper(character) << '\n';

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le costanti matematiche

</div>

In C++ il namespace ```std::numbers``` (necessario includere ```<numbers>```) contiene molte costanti matematiche utili:

+ ```std::numbers::e```: il numero di nepero (e)
+ ```std::numbers::log2e```: logaritmo in base 2 di e
+ ```std::numbers::log10e```: logaritmo in base 10 di e
+ ```std::numbers::pi```: il pi greco
+ ```std::numbers::inv_pi```: inverso del pi greco
+ ```std::numbers::inv_sqrtpi```: inverso della radice del pi greco
+ ```std::numbers::ln2```: logaritmo naturale di 2
+ ```std::numbers::ln10```: logaritmo naturale di 10
+ ```std::numbers::sqrt2```: radice quadrata di 2
+ ```std::numbers::sqrt3```: radice quadrata di 3
+ ```std::numbers::inv_sqrt3```: inverso della radice quadrata di 3
+ ```std::numbers::egamma```: costante di Euler-Mascheroni
+ ```std::numbers::phi```: la costante aurea

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le funzioni matematiche

</div>

In C++ esistono delle funzioni matematiche che per usare è necessario includere **```<cmath>```**, eccone alcuni esempi:

<div style="text-align: center;">

#### ***Arrotondamento***

</div>

+ **```std::floor```** arrotonda per difetto
+ **```std::ceil```** arrotonda per eccesso
+ **```std::round```** arrotonda per difetto o per eccesso

```cpp
#include <cmath>
#include <iostream>

int main()
{
    double number = 13.9;

    std::cout << std::floor(number) << '\n'; // output = 13
    std::cout << std::ceil(number)  << '\n'; // output = 14
    std::cout << std::round(number) << '\n'; // output = 14

    return 0;
}
```

Ecco un altro esempio dell'uso di queste funzioni: capire se un numero in virgola mobile (un ```float``` \ ```double``` \ ```long double```) è intero

```cpp
#include <cmath>
#include <iostream>

int main()
{
    double number;
    std::cin >> number;

    if (std::floor(number) == std::ceil(number))
        std::cout  << "il numero e' intero";
    else std::cout << "il numero non e' intero";

    return 0;
}
```

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Valore assoluto***

</div>

+ **```std::fabs```** calcola il valore assoluto di un numero:

```cpp
#include <cmath>
#include <iostream>

int main()
{
    std::cout << std::fabs(-10.5) << '\n'; // output = 10.5
    std::cout << std::fabs(+71)   << '\n'; // output = 71

    return 0;
}
```

<div style="text-align: center;">

#### ***Esponenti***

</div>

+ **```std::pow```** calcola l'elevamento a potenza  
(base e esponente possono anche essere negativi o decimali):

```cpp
#include <cmath>
#include <iostream>

int main()
{
    std::cout << std::pow(3, 3) << '\n'; // output = 3^3 = 27
    std::cout << std::pow(2, 5) << '\n'; // output = 2^5 = 32

    return 0;
}
```

+ **```std::sqrt```** calcola la radice quadrata e **```std::cbrt```** la radice cubica:

```cpp
#include <cmath>
#include <iostream>

int main()
{
    // la radice quadrata di 25 è 5
    std::cout << std::sqrt(25) << '\n';

    // la radice cubica di 64 è 4
    std::cout << std::cbrt(64) << '\n';

    return 0;
}
```

+ **```std::hypot```** calcola l'ipotenusa di un triangolo rettangolo dati i cateti:

```cpp
#include <cmath>
#include <iostream>

int main()
{
    std::cout << std::hypot(3, 4)  << '\n'; // 3, 4  e 5
    std::cout << std::hypot(5, 12) << '\n'; // 5, 12 e 13

    return 0;
}
```

<div style="text-align: center;">

#### ***Logaritmi e trigonometria***

</div>

+ Per calcolare il logaritmo si possono usare **```std::log2```**, **```std::log10```** e **```std::log```**.

+ Tra le funzioni trigonometriche ci sono **```std::sin```**, **```std::sinh```**, **```std::cos```**, **```std::cosh```**, **```std::tan```**, **```std::tanh```**, **```std::asin```**, **```std::acos```**, **```std::atan```**, **```std::asinh```**, **```std::acosh```** e **```std::atanh```**.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### La complessità temporale di un'operazione

</div>

La notazione **O grande** è uno strumento per descrivere il comportamento asintotico di una funzione:

<br><br>

Esempi di ordini:

+ O(1): **tempo costante**, cioè non dipende dalla dimensione dell'input
+ O(log(n)): **tempo logaritmico** come la ricerca binaria
+ O(n): **tempo lineare**, il tempo di esecuzione è direttamente proporzionale alla dimensione dell'input, come la ricerca lineare
+ O(n * log(n)): **tempo semilogaritmico** come il merge sort
+ O(n^2): **tempo quadratico** come due cicli for annidati
+ O(b^n): **tempo esponenziale**.

---
---

<div style="page-break-after: always;"></div>

---

<h2 style="text-align: center;"><b>Livello Intermediate</b></h2>

---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le funzioni

</div>

Una funzione è un blocco di codice che si può riutilizzare, che elabora degli input detti **parametri** e restituisce un output tramite la parola chiave **```return```**.

<div style="text-align: center;">

#### ***Le basi***

</div>

Vediamo come si scrivono le funzioni **void** (una funzione void non restituisce nessun valore):

```cpp
#include <iostream>

void Function()
{
    std::cout << "questa e' una funzione\n";
}

int main()
{
    Function(); // chiamata di funzione
    return 0;
}
```

Quando viene chiamata una funzione, il controllo viene trasferito a quella funzione, e viene eseguito tutto il codice che c'è all'interno di questa.

<div style="text-align: center;">

#### ***I parametri***

</div>

Vediamo adesso come passare dei parametri a una funzione:

```cpp
#include <iostream>

void PrintNumbers(double param1, double param2)
{
    std::cout << "paramtero 1: " << param1 << '\n';
    std::cout << "paramtero 2: " << param2 << '\n';
}

int main()
{
    double A, B;
    std::cin >> A >> B;

    PrintNumbers(A, B);
    return 0;
}
```

In questo caso la funzione ```PrintNumbers``` accetta come parametri due numeri decimali e li scrive.

<div style="text-align: center;">

#### ***```return```***

</div>

Si usa la parola chiave **```return```** per restituire il valore calcolato dalla funzione:

```cpp
#include <iostream>

double Add(double param1, double param2)
{
    return param1 + param2;
}

int main()
{
    double A, B;
    std::cin >> A >> B;

    auto res = Add(A, B);
    std::cout << res;
    return 0;
}
```

In questo esempio viene chiamata la funzione Add per sommare i due numeri decimali, che restituisce con ```return``` la loro somma, e il valore restituito viene assegnato a una variabile per essere scritto.

<div style="text-align: center;">

#### ***Passare parametri per riferimento***

</div>

Per restituire più di un valore NON si può usare due volte ```return```, questo perché in un'istruzione ```return``` il controllo esce dalla funzione, e ciò che viene dopo è ignorato; l'approccio giusto è passare dei parametri aggiuntivi per riferimento.

Perché quando viene chiamata una funzione, viene eseguita una copia dei due input per non modificarli, ma ciò non succede se si fornisce l'**indirizzo**, esempio:

```cpp
#include <iostream>

void Divide(int dividend, int divisor, int& quotient, int& rest)
{
    if (divisor == 0) return;
    quotient = dividend / divisor;
    rest = dividend - divisor * quotient;
}

int main()
{
    int A, B;
    std::cout << "inserisci due numeri\n";
    std::cin >> A >> B;

    int Quotient, Rest;
    Divide(A, B, Quotient, Rest);

    std::cout << "quoziente = " << Quotient << '\n';
    std::cout << "resto = "     << Rest     << '\n';
    return 0;
}
```

Poiché i parametri ```dividend``` e ```divisor``` non sono preceduti dall'**operatore di indirizzo ```&```**, viene eseguita una copia di ```A```  e ```B```, invece i parametri ```Quotient``` e ```Rest``` non vengono copiati, ma modificano il loro valore secondo le operazioni di ```quotient``` e ```rest```.  
in questo modo non c'è bisogno di utilizzare il ```return```.

<div style="text-align: center;">

#### ***Funzione parametro***

</div>

Ogni funzione ha una sua **firma**, che contiene le informazioni riguardo il nome, il tipo restituito e i datatype dei parametri, quando due funzioni hanno lo stesso nome ma firme diverse, si dice che la funzione è **sovraccaricata**, non si può sovraccaricare la funzione ```main```.

E' possibile passare una funzione come parametro di un'altra funzione, in questo caso bisogna scrivere la firma della funzione parametro nell'elenco dei parametri e alla chiamata della funzione non si mettono le parentesi alla funzione parametro.

Esempio:

```cpp
#include <iostream>

void func1(int x)
{
    std::cout << "chiamata funzione 1 con parametro " << x << '\n';
}

void func2(int x)
{
    std::cout << "chiamata funzione 2 con parametro " << x << '\n';
}

void Printer(void function(int param))
{
    std::cout << "queste sono le funzioni: \n";
    function(1);
    function(2);
    function(3);
}

int main()
{
    Printer(func1);
    Printer(func2);
    return 0;
}
```

<div style="text-align: center;">

#### ***La ricorsione***

</div>

Una funzione può chiamare se stessa, quando ciò accade si dice che la funzione è **ricorsiva**, esempio:

```cpp
#include <iostream>

size_t Factorial(size_t number)
{
    if (number < 2) return 1;
    return number * Factorial(number - 1);
}
```

Bisogna fare molta attenzione alla ricorsione, questo perché

+ Utilizzare due ricorsioni nella stessa espressione è molto lento
+ Quando avvengono troppe ricorsioni si verifica l'errore di **stack overflow**

Ecco un esempio di codice che genera l'errore di stack overflow:

```cpp
int main() { main(); }
```

Qui avviene una ricorsione infinita, che eventualmente riempie la memoria disponibile e il programma va in crash.

<div style="text-align: center;">

#### ***Dichiarazione e definizione***

</div>

E' possibile staccare la dichiarazione della funzione dalla definizione, ad esempio la funzione di prima

```cpp
void Divide(int dividend, int divisor, int& quotient, int& rest)
{
    if (divisor == 0) return;
    quotient = dividend / divisor;
    rest = dividend - divisor * quotient;
}
```

Si può riscrivere così:

```cpp
void Divide(int dividend, int divisor, int& quotient, int& rest);

/*
il resto del codice...
......
*/

void Divide(int dividend, int divisor, int& quotient, int& rest)
{
    if (divisor == 0) return;
    quotient = dividend / divisor;
    rest = dividend - divisor * quotient;
}
```

Questo è molto utile, infatti non si può chiamare una funzione in una riga di codice prima della dichiarazione, ma si possono spostare tutte le dichiarazioni all'inizio del codice e definire la funzione in seguito

E' possibile creare dei parametri facoltativi, che però devono essere messi per ultimi nell'elenco dei parametri di una funzione, riscriviamo l'esempio di prima supponendo che ```dividend``` sia predefinito a 1 così come ```divisor```:

```cpp
void Divide(int& quotient, int& rest, int dividend = 1, int divisor = 1);

void Divide(int& quotient, int& rest, int dividend, int divisor)
{
    if (divisor == 0) return;
    quotient = dividend / divisor;
    rest = dividend - divisor * quotient;
}
```

In questo modo si può fare una chiamata di funzione senza dover per forza specificare quali siano ```dividend``` e ```divisor```, ricordare che non si può fare così con quotient e rest perché sono passati per riferimento e devono essere **lvalue modificabili** quindi non costanti (e quindi neanche numeri dato che essi sono costanti).

<div style="text-align: center;">

#### ***Gli specificatori***

</div>

Una funzione può essere contrassegnata da alcune parole chiave dette **specificatori**, tra le quali troviamo **```inline```**, **```constexpr```** e **```static```**.

Se una funzione è inline, vuol dire che il compilatore sostituirà con il corpo della funzione tutte le chiamate (se possibile), ad esempio questo codice:

```cpp
#include <iostream>
inline void PrintNumbers(double param1, double param2) {
    std::cout << "paramtero 1: " << param1 << '\n';
    std::cout << "paramtero 2: " << param2 << '\n';
}
int main() {
    double A, B;
    std::cin >> A >> B;

    PrintNumbers(A, B);
    return 0;
}
```

Viene considerato come:

```cpp
#include <iostream>
int main() {
    double A, B;
    std::cin >> A >> B;

    std::cout << "paramtero 1: " << A << '\n';
    std::cout << "paramtero 2: " << B << '\n';
    return 0;
}
```

Se una funzione è constexpr, vuol dire che il compilatore la eseguirà prima di far partire il programma (a tempo di compilazione), questo si fa di solito con funzioni piccole:

```cpp
#include <iostream>

constexpr double Square(double number)
{
    return number * number;
}

int main()
{
    const double number = 5;

    // questo è calcolato a tempo di compilazione (25)
    std::cout << Square(number);
    
    return 0;
}
```

Una funzione statica è visibile solo dal file in cui è dichiarata (e quindi non può essere messa in un file header); una variabile statica conserva il suo valore tra diverse chiamate di funzione.

<div style="text-align: center;">

#### ***Gli attributi***

</div>

Oltre agli specificatori esistono anche gli **attributi**, che vanno racchiusi tra una coppia di doppie parentesi quadre, vediamo quelli delle funzioni:

+ **```[[nodiscard]]```**  
  Indica che il valore di ritorno di una funzione non dovrebbe essere ignorato.

```cpp
[[nodiscard]] int ReturnSpecialValue() { return 100; }



int main()
{
    // non genera warning del compilatore
    std::cout << "valore speciale del programma: ";
    std::cout << ReturnSpecialValue() << '\n';

    // warning: valore restituito ignorato
    ReturnSpecialValue();

    // si può fare così per sopprimere il warning
    (void)ReturnSpecialValue();
}
```

+ **```[[deprecated]]```**  
  Indica che una funzione è **deprecata** cioè non dovrebbe essere più utilizzata.

```cpp
[[deprecated("use NewFunct() instead")]] void OldFunct()
{
    // questa funzione non verrà più utilizzata utilizzata
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le direttive

</div>

In C++ le direttive sono istruzioni che vengono valutate dal **preprocessore**, che modifica il codice secondo le istruzioni e lo fornisce al compilatore.

Elenco di direttive:

+ ```#define```
+ ```#elif```
+ ```#else```
+ ```#endif```
+ ```#error```
+ ```#if```
+ ```#ifdef```
+ ```#ifndef```
+ ```#include```
+ ```#line```
+ ```#pragma```
+ ```#undef```

Abbiamo già visto ```#include```, quindi descriveremo le altre direttive.

La direttiva ```#define``` permette di definire una **macro** mentre ```#undef``` la annulla, esempio:

```cpp
#define SIZE
```

```SIZE``` è una macro, in generale i nomi di macro utilizzano lettere maiuscole.

La direttiva ```#ifdef``` controlla se una macro è definita o meno, e deve essere sempre presente una direttiva ```#endif``` dopo l'```#ifdef```, il codice presente tra ```#ifdef``` e ```#endif``` viene eseguito se e solo se la macro in questione è definita:

```cpp
#ifdef SIZE

// questo codice viene eseguito solo se SIZE è definito

#endif
```

La direttiva ```#ifndef``` controlla se una macro NON è definita (contrario di ```#ifdef```), come in questo esempio:

```cpp
#ifndef __cplusplus
#error error STL1003: Unexpected compiler, expected C++ compiler.
#endif
```

Qui ```__cplusplus``` è una macro definita dal compilatore C++, quindi se il compilatore è sbagliato, si usa la direttiva ```#error``` per generare un errore

La direttiva ```#if``` attiva il codice non se la macro è definita ma se è veritiera (cioè si espande in un valore non nullo):

```cpp
#if _HAS_CXX23
#include <optional>
#endif
```

```_HAS_CXX23``` è una macro definita come 1 solo se il programma va dalla versione C++23 in poi, e solo in questo caso si include **```<optional>```**

E' possibile combinare ```#if``` e ```#ifdef``` con ```#elif``` ed ```#else```.

La direttiva ```#line``` serve per cambiare la linea del programma, è utile quando si vuole creare dei warning a una certa riga di codice di un'altro file:

```cpp
#line 100 "example.cpp"
// questa riga sarà vista come riga 100 in example.cpp
```

La direttiva ```#pragma``` è la più complessa, ne esistono molte varianti, ad esempio ```#pragma once``` rende impossibile includere il file più di una volta.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le macro

</div>

In C++ le macro vengono dichiarata con la direttiva ```#define```, e servono a definire simboli che vengono sostituiti dal preprocessore.  
**#define *\<nome\>* *\<espressione\>***

<div style="text-align: center;">

#### ***Macro come costanti***

</div>

Esempio di macro:

```cpp
#define M_PI 3.14159265358979323
```

Ogni volta che il preprocessore trova ```M_PI``` nel codice lo sostituirà con 3.14159265358979323.

<div style="text-align: center;">

#### ***Macro come funzioni***

</div>

Le macro possono anche accettare degli argomenti:

```cpp
#define SQUARE(x) (x * x)     // sbagliato
#define SQUARE(x) ((x) * (x)) // giusto
```

Le macro non sono delle funzioni, servono solo a sostituire del testo, per questo è sbagliato il primo esempio di macro:

```cpp
#define SQUARE(x) (x * x)

// si espande in 1 + 2 * 1 + 2 = 1 + 2 + 2 = 5
SQUARE(1 + 2);
```

```cpp
#define SQUARE(x) ((x) * (x))

// si espande in (1 + 2) * (1 + 2) = 3 * 3 = 9
SQUARE(1 + 2);
```

<div style="text-align: center;">

#### ***Operatori***

</div>

Con le macro è possibile utilizzare l'operatore ```##``` per concatenare due simboli:

```cpp
#define DECLARE_VARIABLE(x) int __##x{}
int Var{};
DECLARE_VARIABLE(Var); // si espande in 'int __Var{}';
```

Se una macro è molto lunga la si può mandare a capo con un backslash:

```cpp
#define DECLARE_VARIABLE(x) \
int __##x{}
```

<div style="text-align: center;">

#### ***Esempi***

</div>

Esistono alcune macro predefinite del preprocessore:

+ ```__FILE__```: il nome del file corrente
+ ```__LINE__```: il nome della linea corrente
+ ```__DATE__```: data di compilazione
+ ```__TIME__```: ora di compilazione

Altre macro sono definite esternamente, un esempio è **```_STD```** che si espande in ```::std::```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le enumerazioni

</div>

In C++ le enumerazioni sono un modo per rendere il codice più leggibile, dove invece di dichiarare un elenco di macro in questo modo:

```cpp
#define MONDAY    1
#define TUESDAY   2
#define WEDNESDAY 3
#define THURSDAY  4
#define FRIDAY    5
#define SATURDAY  6
#define SUNDAY    7
```

<div style="text-align: center;">

#### ***```enum```***

</div>

Si può dichiarare un enum:

```cpp
enum Day
{
    monday   ,
    tuesday  ,
    wednesday,
    thursday ,
    friday   ,
    saturday ,
    sunday
};
```

In un enum ogni parola viene associata implicitamente a un valore da 0 a n, per usare l'enum si può fare così:

```cpp
enum Day
{
    monday   ,
    tuesday  ,
    wednesday,
    thursday ,
    friday   ,
    saturday ,
    sunday
};

int main()
{
    int Day = monday;

    // oppure
    ::Day day = Day::monday;

    // il primo operatore di risoluzione dell'ambito è usato solo
    // perché c'è una variabile che ha lo stesso nome dell'enum

    return 0;
}
```

<div style="text-align: center;">

#### ***```enum class```***

</div>

Due enum non possono avere nessun elemento in comune, tuttavia questo si può risolvere rendendoli classi:

```cpp
enum class Day
{
    monday   ,
    tuesday  ,
    wednesday,
    thursday ,
    friday   ,
    saturday ,
    sunday
};
enum class DAY
{
    sunday   ,
    monday   ,
    tuesday  ,
    wednesday,
    thursday ,
    friday   ,
    saturday ,
};
int main()
{
    Day lastDay  = Day::sunday;
    DAY firstDay = DAY::sunday;

    return 0;
}
```

Gli enum e gli enum class sono due modi di definire dei datatype secondari.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le strutture

</div>

In C++ esiste sono un modo per raggruppare più variabili di datatype non necessariamente uguali, sotto lo stesso nome, il nome della struttura, che diventa un datatype secondario, un esempio è la struttura **```_COORD```** di **```<Windows.h>```** che si definisce così:

```cpp
struct _COORD {
    short X;
    short Y;
};
```

Questo è un tipico esempio di struttura, contiene due variabili ```short```, chiamate ```X``` e ```Y``` che sono le coordinate di un punto, (questa struttura è usata anche per indicare la posizione del cursore).

In realtà la definizione completa della struttura è questa:

```cpp
typedef struct _COORD {
    SHORT X;
    SHORT Y;
} COORD, *PCOORD;
```

Dove ```SHORT``` è un typedef per ```short```.

Per accedere agli elementi di una struttura si usa l'**operatore di accesso ai membri**:

```cpp
#include <iostream>
#include <Windows.h> // necessario per usare COORD

int main()
{
    COORD point{ 5, 2 };

    std::cout << point.X << '\n'; // output = 5
    std::cout << point.Y << '\n'; // output = 2

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le unioni

</div>

In C++ Le unioni sono simili alle strutture, tuttavia ogni variabile ha la stessa regione in memoria, questo significa che modificando una variabile, tutte le altre cambiano, questo è utile quando bisogna effettuare operazioni di conversione oppure operazioni di modulo.

Esempio:

```cpp
#include <iostream>

union variable {
    int number, copy;
};

int main()
{
    variable var;
    var.number = 123;

    // output = 123
    std::cout << var.number << ' ';
    
    // output = 123
    std::cout << var.copy;

    return 0;
}
```

In questo esempio tutte e due le variabili di ```variable``` sono state modificate.

<div style="page-break-after: always;"></div>

Esempio: conversione tra ```int``` e ```short```

```cpp
#include <iostream>

union variable {
    int number;
    short mod;
};

int main()
{
    variable var;
    var.number = 65537;

    // output = 65537
    std::cout << var.number << ' ';
    
    // output = 65537 % 32768 = 1
    std::cout << var.mod;

    return 0;
}
```

Quando si converte da ```int``` a ```short```, il numero 65537 è troppo grande per essere contenuto in ```mod```, quindi viene eseguita un'operazione di modulo (resto della divisione).

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Gli array

</div>

In C++ gli array sono degli insiemi di lunghezza costante che contengono valori dello stesso datatype, possono essere statici (allocati nella **stack**) oppure dinamici (allocati nell'**heap**), Per ora vedremo solo come creare array statici.  
__*\<datatype\>* *\<nome\>* [*\<dimensione\>*];__

<div style="text-align: center;">

#### ***Inizializzazione di un array***

</div>

Esempio: array di 1024 elementi

```cpp
int Array[1024]{};
```

Per riempire un array con dei valori si usa **```std::fill```**, necessario includere **```<algorithm>```**:

```cpp
#include <algorithm>
int main()
{
    int Array[1024]{};
    std::fill(Array, Array + 1023, 1);

    return 0;
}
```

Infatti in questo esempio, ```std::fill``` imposta a 1 tutti gli elementi di ```Array``` dall'indice 0 all'indice 1023.

<div style="text-align: center;">

#### ***Accesso agli elementi***

</div>

Per accedere a un elemento di un array si usa l'**operatore ```[]```** (Il primo elemento si trova alla posizione 0):

```cpp
#include <algorithm>
#include <iostream>

int main()
{
    int Array[1024]{};
    std::fill(Array, Array + 1024, 1);

    for (int i = 0; i < 1024; ++i) std::cout << Array[i] << '\n';

    return 0;
}
```

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Dimensione***

</div>

Per calcolare la dimensione di un array si usa **```sizeof```**, che calcola la dimensione in byte di una certa variabile o di un certo datatype:

```cpp
#include <algorithm>
#include <iostream>

int main()
{
    int Array[1024]{};
    std::fill(Array, Array + sizeof(Array) / sizeof(Array[0]), 1);

    for (int i = 0; i < sizeof(Array) / sizeof(Array[0]); ++i)
        std::cout << Array[i] << '\n';

    return 0;
}
```

Infatti la dimensione in byte di un array è pari al numero degli elementi moltiplicato per la dimensione in byte di uno qualsiasi degli elementi.

<div style="text-align: center;">

#### ***Passare un array a una funzione***

</div>

Per passare un array a una funzione bisogna aggiungere ```[]``` davanti al nome del parametro nella funzione, e bisogna fornire anche la dimensione, infatti quando si passa un'array a una funzione viene in realtà passato un **puntatore** al primo elemento dell'array, cioè una variabile che contiene l'indirizzo del primo elemento dell'array, ma questo significa che non si può più calcolare la dimensione dell'array con ```sizeof``` ed è necessario passare la dimensione come parametro.

Esempio:

```cpp
#include <algorithm>
#include <iostream>

static void print(int arr[], int size)
{
    std::cout << "L'array e' {";
    for (int i = 0; i < size - 1; ++i)
    std::cout << arr[i] << ' ';
    std::cout << arr[size - 1] << '}';
}

int main()
{
    int Array[16]{}, size = sizeof(Array) / sizeof(Array[0]);
    std::fill(Array, Array + size, 1);

    print(Array, size);
    return 0;
}
```

<div style="text-align: center;">

#### ***Il ciclo FOREACH***

</div>

Un ciclo **foreach** è un for che itera su ogni elemento di un array in ordine crescente.

**for (*\<datatype\>* *\<nome_elemento\>* : *\<nome_array\>*)  
{  
    *\<istruzioni da ripetere\>*  
}**

Esempio:

```cpp
    int Array[128], i{};

    for (auto& el : Array) {
        el = i;
        ++i;
    }
```

Questo ciclo riempie l'array di numeri interi consecutivi a partire da 0, viene usata la parola chiave **```auto```** come datatype, ed è presente l'**operatore di indirizzo ```&```** a indicare che la modificando la variabile, viene modificato anche l'array, in un foreach si può anche usare **```const```**, che indica che la variabile del ciclo non può essere modificata.

<div style="text-align: center;">

#### ***Array multidimensionali***

</div>

Un array multidimensionale è un array che ha come elementi degli altri array, e lo si dichiara così:

```cpp
int Array2d[10][3];     // due dimensioni
int Array3d[16][20][2]; // tre dimensioni
// ecc...
```

Supponendo di avere un array 2D, ```Arr```:

```cpp
int Arr[12][12];
```

E supponiamo di avere anche due indici ```i``` e ```j```, ```Arr[i]``` è un array 1D, quindi ```(Arr[i])[j]``` o più semplicemente ```Arr[i][j]``` è un elemento dell'array.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Algoritmi degli array

</div>

<div style="text-align: center;">

#### ***Algoritmi di ordinamento***

</div>

+ **Bubble Sort**  
Il Bubble Sort confonta ogni coppia di elementi adiacenti e li scambia se sono nell'ordine sbagliato.

```cpp
#include <algorithm>
static void BubbleSort(int arr[], int size)
{
    for (int i = 0; i < size - 1; ++i)
        for (int j = 0; j < size - i - 1; ++j)
            if (arr[j] > arr[j + 1])
                std::swap(arr[j], arr[j + 1]);
}
```

+ **Selection Sort**  
Il Selection Sort trova l'elemento minimo e lo riposiziona all'inizio e poi ripete il processo.

```cpp
static void SelectionSort(int arr[], int size)
{
    for (int i = 0; i < size - 1; ++i)
    {
        int min{ i };
        for (int j = i + 1; j < size; ++j)
            if (arr[j] < arr[min]) min = j;
        std::swap(arr[i], arr[min]);
    }
}
```

+ **Insertion Sort**  
L'Insertion Sort inserisce gli elementi già ordinati uno alla volta nella posizione corretta.

```cpp
static void InsertionSort(int arr[], int size)
{
    for (int i = 1; i < size; ++i)
    {
        int key = arr[i], j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```

+ **Quick Sort**  
Il Quick Sort seleziona un elemento come pivot e ordina l'array in modo che tutti gli elementi minori siano a sinistra del pivot e tutti gli elementi maggiori a destra.

```cpp
static int partition(int arr[], int low, int high)
{
    int pivot = arr[high], i = low - 1;
    for (int j = low; j < high; ++j) if (arr[j] <= pivot)
    {
        std::swap(arr[++i], arr[j]);
    }
    std::swap(arr[i + 1], arr[high]);
    return i + 1;
}

static void QuickSort(int arr[], int low, int high)
{
    if (low < high) {
        auto pi = partition(arr, low, high);
        QuickSort(arr, low, pi - 1);
        QuickSort(arr, pi + 1, high);
    }
}
```

Si può chiamare questa funzione ```QuickSort``` in questo modo:

```cpp
QuickSort(arr, 0, sizeof(arr) / sizeof(arr[0]) - 1);
```

+ Heap Sort  
L'Heap Sort costruisce una struttura dati a forma di albero (heap) dall'array ed estrae l'elemento massimo uno alla volta.

```cpp
static void Heapify(int arr[], int n, int i)
{
    int largest = i, left = 2 * i + 1, right = 2 * i + 2;

    if (left  < n && arr[left]  > arr[largest]) largest =  left;
    if (right < n && arr[right] > arr[largest]) largest = right;

    if (largest != i) {
        std::swap(arr[i], arr[largest]);
        Heapify(arr, n, largest);
    }
}




static void HeapSort(int arr[], int size)
{
    for (int i = size / 2 - 1; i >= 0; --i)
        heapify(arr, size, i);

    for (int i = size - 1; i > 0; --i)
    {
        std::swap(arr[0], arr[i]);
        heapify(arr, i, 0);
    }
}
```

<div style="text-align: center;">

#### ***Algoritmi di ricerca***

</div>

+ Ricerca lineare:  
Si controlla per ogni indice dell'array se l'elemento corrisponde, funziona con ogni tipo di array.

```cpp
static int LinearSearch(const int arr[], int size, int element)
{
    for (int i = 0; i < size; ++i) if (arr[i] == element)
        return i;
    return -1;
}
```

+ Ricerca binaria:  
Funziona solo su array ordinati, si parte dalla metà dell'array e dimezzando l'incremento a ogni iterazione si aumenta o si diminuisce l'indice, se l'elemento all'indice è maggiore o minore dell'elemento da trovare.

```cpp
static int BinarySearch(const int arr[], int size, int element)
{
    int left{}, right{ size - 1 };

    while (left <= right)
    {
        int mid = left + (right - left) / 2;

        if (arr[mid] == element) return mid;
        else if (arr[mid] < element) left = mid + 1;
        else right = mid - 1;
    }

    return -1;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### I puntatori

</div>

In C++ un **puntatore** è una variabile il cui valore è l'indirizzo di un'altra variabile.  

<div style="text-align: center;">

#### ***Sintassi di base***

</div>

***\<datatype\>*\* *\<nome\>* = nullptr;**

E' possibile dichiarare un puntatore senza inizializzarlo ma per sicurezza si dovrebbe sempre inizializzare a ```nullptr```.

Per assegnare un indirizzo a un puntatore si può utilizzare l'**operatore di indirizzo ```&```**:

```cpp
    int Variable{};
    int *pointer = &Variable;
```

Per ottenere il valore della variabile a cui punta il puntatore si usa l'**operatore di dereferenziazione ```*```**:

```cpp
    int Variable{};
    int *pointer = &Variable;
    int NewVariable = *pointer;
```

<div style="text-align: center;">

#### ***Puntatori che puntano a un array \ struttura***

</div>

Se un puntatore punta a un array, sta in realtà puntando al primo elemento di quell'array, e incrementando il puntatore si accede agli altri elementi dell'array:

```cpp
    int arr[5]{ 1, 2, 3, 4, 5 };
    int* pArr = &arr;         // pArr     punta a arr[0] = 1
    std::cout << *(pArr + 1); // pArr + 1 punta a arr[1] = 2
```

Se un puntatore punta a una struttura, si può accedere ai suoi elementi tramite l'**operatore di accesso tramite puntatore a membro ```->```**:

```cpp
#include <iostream>
struct point {
    double x, y, z;
};
int main()
{
    point P1{ 1, -1, 0 };
    point* ptr1 = &P1;
    ptr1->z = 3; // modifica di P1.z

    // output = {1, -1, 3}
    std::cout << '{'  << P1.x;
    std::cout << ", " << P1.y;
    std::cout << ", " << P1.z << "}\n";

    return 0;
}
```

<div style="text-align: center;">

#### ***Puntatori nell'heap***

</div>

Per dichiarare un puntatore nell'**heap** si usa l'operatore **```new```**:

```cpp
    int* ptr = new int; // alloca memoria per un singolo intero
    *ptr = 10; // assegnazione del valore
```

Se il puntatore punta a un array la sintassi cambia leggermente

```cpp
    int* Ptr = new int[7]; // alloca memoria per 7 interi
```

Per accedere a un elemento dell'array si fa come con gli array statici (operatore ```[]```).

Quando un puntatore non serve più deve essere deallocato:

```cpp
    delete ptr;   // operatore delete per deallocare puntatori
    ptr = nullptr;

    delete[] Ptr; // operatore delete[] per deallocare array
    Ptr = nullptr
```

<div style="text-align: center;">

#### ***Le eccezioni di ```<stdexcept>```***

</div>

E' buona pratica, ogni volta che si crea un puntatore nell'heap, di controllare se il puntatore è nullo, in questo caso si può sollevare un'eccezione, che ferma in automatico il programma quando si verifica un errore:

```cpp
    int* ptr = new int;
    if (!ptr) throw std::bad_alloc();
```

Esistono altri tipi di eccezioni come ad esempio queste:

+ ```std::invalid_argument```
+ ```std::out_of_range```
+ ```std::overflow_error```

E' possibile gestire queste eccezioni con dei blocchi **try-catch**, dove non si possono sottointendere le parentesi graffe, esempio:

```cpp
#include <iostream>
#include <stdexcept>

int main()
{
    try {
        throw std::out_of_range("this exception");
        throw std::exception();
    }
    catch (std::out_of_range E) // cattura solo out_of_range
    {
        // output = "eccezione catturata: this exception"
        std::cout << "eccezione catturata: " << E.what() << '\n';
        return 1;
    }
    catch (...) // cattura qualsiasi eccezione
    {
        std::cout << "eccezione sconosciuta catturata\n";
        return 2;
    }

    std::cout << "non si sono verificate eccezioni\n";
    return 0;
}
```

Ogni istruzione ```try``` deve avere almeno un'istruzione ```catch```.

<div style="text-align: center;">

#### ***Puntatori intelligenti***

</div>

In C++ l'utilizzo dei puntatori è facilitato dai puntatori intelligenti (necessario includere **```<memory>```**): **```std::unique_ptr```**, **```std::shared_ptr```** e **```std::weak_ptr```**:

**```std::unique_ptr```** è un puntatore che garantisce l'univocità del possesso di un oggetto, ciò significa che solo uno unique\_ptr può possedere un determinato oggetto alla volta, non si usa ```delete``` perché quando uno unique\_ptr esce dal suo ambito, l'oggetto a cui punta viene deallocato automaticamente.

Non si può copiare uno unique\_ptr ma lo si può spostare con **```std::move```**

Esempio:

```cpp
#include <iostream>
#include <memory>
#include <utility> // per std::move

int main()
{
    std::unique_ptr<int> ptr1 = std::make_unique<int>(10);
    std::cout << *ptr1 << '\n';

    std::unique_ptr<int> ptr2 = std::move(ptr1);

    // ptr1 è nullo e l'oggetto è spostato a ptr2
    
    return 0;
}
```

**```std::shared_ptr```** è un altro puntatore intelligente, e permette la condivisione delle proprietà dell'oggetto, non si usa delete perché l'oggetto a cui uno shared_ptr punta viene deallocato ogni volta che lo shared_ptr viene distrutto o diventa nullo.

```std::shared_ptr``` ha un contatore implementato per tenere il conto di quanti puntatori puntano allo stesso oggetto alla volta.

Esempio:

```cpp
#include <iostream>
#include <memory>

int main()
{
    std::shared_ptr<int> ptr1 = std::make_shared<int>(11);
    
    {
        auto ptr2 = ptr1;
        std::cout << ptr1.use_count() << '\n'; // output = 2
        std::cout << *ptr2 << '\n';            // output = 11
    
    } // ptr2 viene distrutto
    
    std::cout << ptr1.use_count() << '\n';     // output = 1

    // ptr1 viene distrutto, l'oggetto è deallocato
    return 0;
}
```

Tuttavia se ci sono due oggetti che puntano l'uno all'altro (riferimento circolare), il contatore non arriverà mai a zero, ma questo problema si può risolvere sostituendo uno shared_ptr con un weak_ptr.

**```std::weak_ptr```** non incrementa il contatore di riferimenti degli altri shared_ptr, ma può osservare se l'oggetto esiste ancora e può essere convertito in shared_ptr.

Esempio:

<div style="page-break-after: always;"></div>

```cpp
#include <iostream>
#include <memory>

struct StructA;
struct StructB;
struct StructA {
     // questo deve essere uno std::weak_ptr
    std::shared_ptr<StructB> b_ptr;
};
struct StructB {
    std::shared_ptr<StructA> a_ptr;
};

int main()
{
    std::shared_ptr<StructA> a = std::make_shared<StructA>();
    std::shared_ptr<StructB> b = std::make_shared<StructB>();

    // ogni oggetto punta all'altro
    a->b_ptr = b;
    b->a_ptr = a;
    
    return 0; // gli oggetti non verranno deallocati
}
```

Ecco un esempio dell'uso del metodo lock di weak_ptr:

```cpp
#include <iostream>
#include <memory>

int main()
{
    std::shared_ptr<int> sptr = std::make_shared<int>(1);
    std::weak_ptr wptr = sptr;

    // codice...
    // sptr.reset() per deallocare l'oggetto

    if (auto checkptr = wptr.lock()) // operatore = non ==
        std::cout << "l'oggetto è ancora vivo\n";
    // checkptr viene distrutto uscendo dall'ambito

    else std::cout << "l'oggetto è stato deallocato\n";

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### ```Windows.h```

</div>

**```<Windows.h>```** è un file header utilizzato per accedere alle API (Application Programming Interface) di Windows, per utilizzarle serve un **handle** (puntatore void) alla console, in questo modo:

```cpp
#include <Windows.h>
HANDLE hConsole = GetStdHandle(STD_OUTPUT_HANDLE);
```

<div style="text-align: center;">

#### ***Cambiare l'attributo della console***

</div>

Per cambiare il colore del testo e dello sfondo della console si utilizza la funzione **```SetConsoleTextAttribute```**, esempio:

```cpp
    SetConsoleTextAttribute(hConsole, BACKGROUND_RED | FOREGROUND_BLUE);
```

Le macro utilizzate sono queste:

+ Per il colore del testo
  + ```FOREGROUND_RED```
  + ```FOREGROUND_BLUE```
  + ```FOREGROUND_GREEN```
  + ```FOREGROUND_INTENSITY```

+ Per il colore dello sfondo
  + ```BACKGROUND_RED```
  + ```BACKGROUND_BLUE```
  + ```BACKGROUND_GREEN```
  + ```BACKGROUND_INTENSITY```

Queste macro vengono combinate utilizzando l'**operatore bitwise or**.

<div style="text-align: center;">

#### ***Riposizionare il cursore***

</div>

Per cambiare la posizione del cursore si utilizza la funzione **```SetConsoleCursorPosition```**.  
Esempio:

```cpp
    SetConsoleCursorPosition(hConsole, COORD{ 0, 10 });
```

Qui il cursore viene riposizionato alla coordinata (0, 10) sulla console, il ```COORD``` prima delle parentesi graffe è un **type cast**.

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Ottenere i dati della console***

</div>

Per ottenere dati come la posizione del cursore o la dimensione del buffer della console c'è un'unica funzione che si chiama **```GetConsoleScreenBufferInfo```**:

```cpp
#include <stdexcept>
#include <Windows.h>
HANDLE hConsole = GetStdHandle(STD_OUTPUT_HANDLE);
CONSOLE_SCREEN_BUFFER_INFO csbi;

int main()
{
    if (!GetConsoleScreenBufferInfo(hConsole, &csbi))
        throw std::runtime_error("failed to access info");

    csbi.dwSize;              // dimensioni del buffer
    csbi.dwCursorPosition;    // posizione del cursore
    csbi.wAttributes;         // attributo della console
    
    // SMALL_RECT con le posizioni dei vertici della finestra
    // nel buffer della console
    csbi.srWindow;

    csbi.dwMaximumWindowSize; // dimensioni massime della finestra

    return 0;
}
```

Notare che il ```CONSOLE_SCREEN_BUFFER_INFO``` ```csbi``` viene passato per riferimento.

<div style="text-align: center;">

#### ***Nascondere il cursore***

</div>

Si possono cambiare le informazioni del cursore con la funzione **```SetConsoleCursorInfo```**:

```cpp
#include <Windows.h>
HANDLE hConsole = GetStdHandle(STD_OUTPUT_HANDLE);
CONSOLE_CURSOR_INFO HideCursor{ 10, FALSE };
CONSOLE_CURSOR_INFO ShowCursor{ 10, TRUE  };

int main()
{
    SetConsoleCursorInfo(hConsole, &HideCursor); // nasconde il cursore

    // altro codice...

    SetConsoleCursorInfo(hConsole, &ShowCursor); // mostra il cursore
    return 0;
}
```

<div style="text-align: center;">

#### ***Pulire un'area dello schermo***

</div>

Per riempire una linea dello schermo esistono queste funzioni:  
```FillConsoleOutputCharacterA```, ```FillConsoleOutputCharacterW``` e ```FillConsoleOutputAttribute```.

Ecco le definizioni di queste funzioni:

```cpp
__declspec(dllimport) int __stdcall
FillConsoleOutputCharacterA(
    _In_  HANDLE hConsoleOutput,
    _In_  CHAR cCharacter,
    _In_  DWORD nLength,
    _In_  COORD dwWriteCoord,
    _Out_ LPDWORD lpNumberOfCharsWritten
);

__declspec(dllimport) int __stdcall
FillConsoleOutputCharacterW(
    _In_  HANDLE hConsoleOutput,
    _In_  WCHAR cCharacter,
    _In_  DWORD nLength,
    _In_  COORD dwWriteCoord,
    _Out_ LPDWORD lpNumberOfCharsWritten
);

__declspec(dllimport) int __stdcall
FillConsoleOutputAttribute(
    _In_  HANDLE hConsoleOutput,
    _In_  WORD wAttribute,
    _In_  DWORD nLength,
    _In_  COORD dwWriteCoord,
    _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

```_In_``` è una macro che indica che il parametro è di input, mentre ```_Out_``` indica che il parametro va passato per riferimento per ottenere un'informazione.

Bisogna fornire (in ordine) l'Handle, il carattere \ attributo da scrivere, quanti caratteri \ attributi scrivere, la coordinata di partenza e si ottiene il numero di caratteri \ attributi cambiati.

La differenza tra **```FillConsoleOutputCharacterA```** e **```FillConsoleOutputCharacterW```** è il fatto che la seconda funziona anche con i caratteri unicode (estensione della tabella ASCII), Tuttavia esiste la macro **```FillConsoleOutputCharacter```**, che sceglie in automatico qual è la funzione da utilizzare.

Si può utilizzare ```system("cls")``` per cancellare tutto ciò che è stato scritto sulla console.

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Inviare un input utente***

</div>

Si usa la funzione SendInput: il primo parametro indica quanti input inviare, il secondo è un array di ```INPUT``` e il terzo è ```sizeof(INPUT)```.

Esempio:

```cpp
INPUT input[2]{};

// pressione tasto 'A'
input[0].type = INPUT_KEYBOARD;
input[0].ki.wVk = 'A';

// rilascio tasto
input[1].type = INPUT_KEYBOARD;
input[1].ki.wVk = 'A';
input[1].ki.dwFlags = KEYEVENTF_KEYUP;

SendInput(2, input, sizeof(INPUT));
```

+ ```KEYEVENTF_KEYUP``` indica che il tasto viene rilasciato,
+ ```MOUSEEVENTF_LEFTDOWN``` preme il tasto sinistro del mouse,
+ ```MOUSEEVENTF_LEFTUP``` preme il tasto destro del mouse.

Per impostare il tipo di tasto da premere, si usano i caratteri della lettera maiuscola \ numero corrispondente al tasto, se il tasto è speciale si usano queste macro:

+ ```VK_SHIFT```
+ ```VK_CONTROL```
+ ```VK_MENU``` (tasto ALT)
+ ```VK_ESCAPE```
+ ```VK_SPACE```
+ ```VK_END```
+ ```VK_HOME```
+ ```VK_LEFT```
+ ```VK_UP```
+ ```VK_RIGHT```
+ ```VK_DOWN```
+ ```VK_PRINT```
+ ```VK_INSERT```
+ ```VK_DELETE```
+ da ```VK_F1``` a ```VK_F24```
+ ...

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***```MessageBox```***

</div>

```MessageBox``` è una funzione che crea una finestra di messaggio, ad esempio:

```cpp
MessageBox(
    NULL,                        // handle alla finestra proprietaria
    L"Il programma \
è terminato con successo.",      // messaggio
    L"info",                     // titolo           
    MB_OK | MB_ICONINFORMATION   // tipo di finestra MessageBox
);
```

Tipi di pulsanti:

+ ```MB_OK```: solo pulsante ```OK```
+ ```MB_OKCANCEL```: pulsanti ```OK``` e ```ANNULLA```
+ ```MB_YESNO```: pulsanti ```SI``` e ```NO```
+ ```MB_RETRYCANCEL```: pulsanti ```RIPROVA``` e ```ANNULLA```
+ ```MB_ABORTRETRYIGNORE```: pulsanti ```INTERROMPI```, ```RIPROVA``` e ```IGNORA```

Tipi di icone:

+ ```MB_ICONERROR```: un errore
+ ```MB_ICONWARNING```: un avviso
+ ```MB_ICONQUESTION```: un punto interrogativo
+ ```MB_ICONINFORMATION```: un'informazione

Il valore restituito dalla funzione indica il tasto che l'utente ha premuto, che può essere ```IDOK```, ```IDYES```, ```IDNO```, ```IDRETRY```, ```IDCANCEL```, ```IDABORT``` o ```IDIGNORE```.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le stringhe

</div>

In C++ la classe ```std::string``` e la classe ```std::wstring``` rappresentano un **array di caratteri**, e ci sono molti metodi utili per gestire queste stringhe.

<div style="text-align: center;">

#### ***Ottenere la dimensione di una stringa***

</div>

Si usa il **metodo ```size```** oppure la **funzione ```std::size```**:

```cpp
#include <iostream>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring Str;
    std::getline(std::wcin, Str);

    std::wcout << L"la dimensione della stringa è ";
    std::wcout << std::size(Str); // Str.size() va bene lo stesso

    return 0;
}
```

<div style="text-align: center;">

#### ***Capire se una stringa è vuota***

</div>

Si può controllare se la dimensione è 0 ma esiste anche il metodo **```empty```**:

```cpp
#include <iostream>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring Str;
    std::getline(std::wcin, Str);

    if (Str.empty()) std::wcout << L"la stringa è vuota";
    else std::wcout << L"la stringa non è vuota";

    return 0;
}
```

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Accesso agli elementi di una stringa***

</div>

Si usa il metodo **```at```** oppure l'operatore **```[]```**:

```cpp
#include <iostream>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring Str;

    do std::getline(std::wcin, Str);
    while (Str.empty());

    std::wcout << L"il primo carattere è " << Str.at(0)  << L'\n';
    std::wcout << L"l'ultimo carattere è " << Str[Str.size() - 1];

    return 0;
}
```

<div style="text-align: center;">

#### ***Convertire una stringa in un numero***

</div>

Se la stringa non è convertibile, la funzione di conversione solleverà un'eccezione **```invalid_argument```**, ci sono parecchie funzioni:

+ **```std::stoi```** converte in ```int```
+ **```std::stof```** converte in ```float```
+ **```std::stod```** converte in ```double```
+ **```std::stold```** converte in ```long double```
+ **```std::stol```** converte in ```long```
+ **```std::stoul```** converte in ```unsigned long```
+ **```std::stoll```** converte in ```long long```
+ **```std::stoull```** converte in ```unsigned long long```

Esempio d'uso:

<div style="page-break-after: always;"></div>

```cpp
#include <iostream>
#include <string>

int main()
{
    setlocale(0, "");

    wstring Num = L"123";
    std::wcout << stoi(Num); // output = 123
    return 0;
}
```

<div style="text-align: center;">

#### ***Convertire un numero in una stringa***

</div>

Si utilizza **```std::to_string```** per le stringhe normali e **```std::to_wstring```** per quelle wide.  
Questo è molto utile, per esempio, per calcolare la somma delle cifre di un numero:

```cpp
#include <iostream>
#include <string>

int main()
{
    setlocale(0, "");

    size_t Num, sum;
    std::cin >> Num;
    std::wstring Str = std::to_wstring(Num);

    // per convertire da carattere a numero si sottrae L'0' = 49
    for (const auto& ch : Num) sum += ch - L'0';

    std::wcout << L"la somma delle cifre è " << sum << L'\n';
    return 0;
}
```

<div style="text-align: center;">

#### ***Trovare un carattere in una stringa***

</div>

Si usa il metodo ```find```, che trova la prima occorrenza:

```cpp
#include <conio.h>
#include <iostream>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring string;
    std::wcout << L"inserisci una stringa\n";
    std::getline(std::wcin, string);
    std::wcout << L"inserisci il carattere da cercare\t";
    char c = _getche();
    std::wcout << '\n';

    int pos = string.find(c);
    if (pos == std::wstring::npos) {
        std::wcout << L"il carattere non è presente in quella stringa";
        return 0;
    }




    std::wcout << L"la prima occorrenza del carattere " << c;
    std::wcout << L"è alla posizione " << pos << L'\n';
    return 0;
}
```

Se il carattere non è presente, il metodo ```find``` restituisce ```std::string::npos``` o ```std::wstring::npos```.

<div style="text-align: center;">

#### ***Inserire un carattere in una stringa***

</div>

Si usa il metodo **```insert```**:

```cpp
#include <conio.h>
#include <iostream>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring string;
    std::wcout << L"inserisci una stringa\n";
    std::getline(std::wcin, string);

    int pos;
    do {
        std::wcout << L"inserisci la posizione del nuovo carattere\n";
        std::wcin >> pos;

        if (pos < 0 || pos >= string.size()) {
            std::wcout << L"la posizione non è valida";
            return 0;
        }
    } while (pos < 0 || pos >= string.size());

    std::wcout << L"inserisci il carattere da inserire\t";
    char c = _getche();
    std::wcout << '\n';

    string.insert(string.begin() + pos, c);
    std::wcout << L"la nuova stringa è " << string << L'\n';
    return 0;
}
```

Il metodo ```begin``` ritorna un **iteratore** al primo elemento della stringa, il metodo ```end``` ritorna un iteratore all'ultimo elemento, e si possono utilizzare gli operatori ```+``` e ```-``` per incrementare \ decrementare l'elemento dell'iteratore

<div style="text-align: center;">

#### ***Tagliare una stringa***

</div>

Si usa il metodo **```erase```**, che ha 4 varianti:

+ Cancellare tutto

```cpp
    str.erase(); // va bene anche str.clear()
```

+ Cancellare un singolo carattere nella stringa

```cpp
    str.erase(str.begin() + position);
```

+ Cancellare tutti i caratteri della stringa a partire da una posizione

```cpp
    str.erase(position);
```

+ Cancellare un determinato numero di caratteri a partire da una posizione

```cpp
    str.erase(position, amount);
```

Per cancellare l'ultimo carattere di una stringa si può usare il metodo **```pop_back```**:

```cpp
    str.pop_back();
```

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Aggiungere un carattere a una stringa***

</div>

Ci sono due modi per aggiungere un carattere a una stringa: con il metodo **```push_back```** e con l'**operatore ```+```**:

```cpp
#include <conio.h>
#include <iostream>
#include <string>
int main() {
    setlocale(0, "");

    std::wstring string;
    std::wcout << L"inserisci la stringa\n";
    std::getline(std::wcin, A);

    std::wcout << L"inserisci il carattere da aggiungere\n";
    char ch = _getche();

    std::wstring result = string;  // (result = string + ch
    result.push_back(ch);          //  va bene lo stesso   )

    std::wcout << L"nuova stringa " << result;
    return 0;
}
```

Qui si poteva usare anche l'**operatore ```+=```**.

<div style="text-align: center;">

#### ***Concatenare due stringhe***

</div>

Ci sono due modi per concatenare due stringhe: con il metodo **```append```** e con l'**operatore ```+```**:

```cpp
#include <iostream>
#include <string>
int main() {
    setlocale(0, "");

    std::wstring A, B;
    std::wcout << L"inserisci due stringhe\n";
    std::getline(std::wcin, A);
    std::getline(std::wcin, B);

    std::wstring result = A;   // (result = A + B
    result.append(B);          //  va bene lo stesso)

    std::wcout << L"stringhe concatenate: " << result;
    return 0;
}
```

Anche qui si poteva usare l'**operatore ```+=```**.

<div style="text-align: center;">

#### ***Creare una sottostringa***

</div>

Si usa il metodo **```substr```**:

```cpp
    std::wstring part = str.substr(FirstIndex, LastIndex);
```

La stessa cosa si può fare in questo modo con ```erase```:

```cpp
    std::wstring part = str;
    part.erase(LastIndex + 1);
    part.erase(0, FirstIndex);
```

<div style="text-align: center;">

#### ***Altro***

</div>

Esistono sono gli operatori ```=``` per assegnare a una stringa, e ```==``` per eguagliare due stringhe

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Gli stringstream

</div>

In C++ gli **```stringstream```** (necessario includere **```<sstream>```**) sono degli oggetti che ricreano il funzionamento di ```cout``` e ```cin``` ma senza avere accesso alla console, ne esistono molte varianti,

+ **```stringstream```** esegue operazioni di input e output
+ **```ostringstream```** esegue operazioni di output
+ **```istringstream```** esegue operazioni di input
+ **```wstringstream```** esegue operazioni di input wide e output wide
+ **```wostringstream```** esegue operazioni di output wide
+ **```wistringstream```** esegue operazioni di input wide

<div style="text-align: center;">

#### ***Ottenere la stringa di uno stringstream***

</div>

Si usa il metodo **```str```**:

```cpp
#include <iostream>
#include <sstream>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring str;
    std::wcout << L"inserisci una stringa\n";
    std::wcin >> str;

    std::wstringstream stream(str);
    std::wcout << L"la stringa è " << stream.str();
    return 0;
}
```

<div style="text-align: center;">

#### ***Gli stringstream di input***

</div>

Con i **```wistringstream```** si possono eseguire solo operazioni di input dallo stringstream.  
Esempio:

```cpp
#include <iostream>
#include <sstream>
#include <string>

int main()
{
    setlocale(0, "");
    
    std::wstring str = L"123 45.67 read";
    std::wistringstream iss(str);

    int i;
    double d;
    std::wstring s;

    iss >> i >> d >> s; // lettura dati dal wistringstream

    std::wcout << L"intero: "  << i << L'\n'; // output = 123
    std::wcout << L"double: "  << d << L'\n'; // output = 45.67
    std::wcout << L"stringa: " << s << L'\n'; // output = read

    return 0;
}
```

Si può usare **```std::ws```** per forzare il salto degli spazi bianchi (spazi, tabulazioni o nuove righe) durante la lettura, esempio:

```cpp
#include <iostream>
#include <sstream>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring str = L"    123    45.67    read";
    std::wistringstream iss(str);

    int i;
    double d;
    std::wstring s;

    // ignora gli spazi bianchi prima della stringa
    iss >> std::ws >> i;
    
    // gli spazi bianchi in mezzo alla stringa non hanno effetto
    iss >> d;

    // ignora gli spazi bianchi prima della stringa da leggere
    iss >> std::ws >> s;

    std::wcout << L"intero: "  << i << L'\n';
    std::wcout << L"double: "  << d << L'\n';
    std::wcout << L"stringa: " << s << L'\n';

    return 0;
}
```

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Gli stringstream di output***

</div>

Con i **```wostringstream```** si possono eseguire solo operazioni di output dallo stringstream, esempio:

```cpp
#include <iostream>
#include <sstream>
#include <string>

int main()
{
    setlocale(0, "");
    
    std::wostringstream oss;

    int i = 123;
    double d = 45.67;
    std::wstring s = L"read";

    oss << i << L' ' << d << L' ' << s; // scrittura dati sul wostringstream

    std::wcout << "stringstream: " << oss.str(); // output = 123 45.67 read
    return 0;
}
```

<div style="text-align: center;">

#### ***La manipolazione dell'input***

</div>

I ```wostringstream``` sono utili quando bisogna usare le funzioni del file header **```<iomanip>```** (input output manipulator), con dei dati, vediamo i principali:

+ **```std::boolalpha```** e **```std::noboolalpha```**  
Si usa ```boolalpha``` per visualizzare le variabili booleane come il loro valore di verità invece di un numero, ```noboolalpha``` disattiva ```boolalpha```:

```cpp
#include <iomanip>
#include <iostream>
#include <sstream>
int main() {
    setlocale(0, "");

    std::wostringstream stream;
    bool Alpha = true;

    stream << boolalpha   <<  Alpha; // stream.str() = true
    stream << noboolalpha << !Alpha; // stream.str() = true0

    std::wcout << L"lo stringstream è " << stream.str();
    return 0;
}
```

+ **```std::oct```**, **```std::dec```**, **```std::hex```** e **```std::setbase```**  
```oct``` converte i numeri in base 8, ```dec``` in base 10 e ```hex``` in base 16, si può anche utilizzare ```setbase``` al loro posto, ma non con altre basi; ```dec``` è predefinito:

```cpp
#include <iomanip>
#include <iostream>
#include <sstream>

int main()
{
    setlocale(0, "");

    std::wostringstream stream;
    int number = 40;

    stream             << number << L' ';
    stream << std::oct << number << L' '; // 40 in base 8  è 50
    stream << std::hex << number << L' '; // 40 in base 16 è 28
    stream << std::setbase(10);           // reset della base

    // output = 40 50 28
    std::wcout << L"lo stringstream è " << stream.str();
    return 0;
}
```

+ **```std::uppercase```** e **```std::nouppercase```**  
Se un numero convertito in esadecimale ha delle cifre alfabetiche, queste saranno minuscole, per scriverle maiuscole si usa ```uppercase```, per annullare ```uppercase``` si usa ```nouppercase```:

```cpp
#include <iomanip>
#include <iostream>
#include <sstream

int main()
{
    setlocale(0, "");

    std::wostringstream stream;

    stream << std::uppercase;
    stream << std::hex << 59 << L' '; // 59 in base 16 è 3b
    stream << std::nouppercase;

    // output = 3B
    std::wcout << L"lo stringstream è " << stream.str();
    return 0;
}
```

+ **```std::fixed```**, **```std::scientific```** e **```std::defaultfloat```** con **```std::setprecision```**  
```setprecision``` stabilisce quante cifre decimali dopo la virgola ci devono essere, ```fixed``` indica che il numero di cifre decimali è fisso, ```scientific``` forza l'output in notazione scientifica e ```defaultfloat``` annulla ```fixed``` o ```scientific```:

```cpp
#include <iomanip>
#include <iostream>
#include <sstream>

int main()
{
    setlocale(0, "");

    std::wostringstream stream;
    double num = 9876.54321;

    stream << L"   " << std::fixed        << std::setprecision(2) << num;
    stream << L"   " << std::scientific   << std::setprecision(2) << num;
    stream << L"   " << std::defaultfloat << std::setprecision(2) << num;

    // output =   9876.54   9.88e+03   9.9e+03
    std::wcout << L"lo stringstream è" << stream.str();
    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le espressioni regolari

</div>

In C++ le classi **```std::regex```** e **```std::wregex```** (necessario includere **```<regex>```**) sono un modo per controllare se una stringa rispetta una qualche condizione.  
Ecco un esempio di regex

```cpp
#include <regex>
std::wregex rgx(L"[1-3]");
```

<div style="text-align: center;">

#### ***Le funzioni di ricerca***

</div>

Esistono tre funzioni importanti riguardanti la ricerca con le regex:

+ **```regex_match```** controlla se l'intera stringa corrisponde alla regex:

```cpp
#include <iostream>
#include <regex>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring text;
    std::wcout << L"inserisci una stringa\n";
    std::getline(std::wcin, text);

    // controlla se la stringa corrisponde a L"reg"
    if (std::regex_match(text, std::wregex(L"reg")))
        std::wcout << L"hai indovinato la parola\n";

    return 0;
}
```

+ **```regex_search```** controlla se almeno una porzione della stringa corrisponde alla regex:

```cpp
#include <iostream>
#include <regex>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring text;
    std::wcout << L"inserisci una stringa\n";
    std::getline(std::wcin, text);

    // controlla se la stringa contiene L"reg"
    if (std::regex_search(text, std::wregex(L"reg")))
        std::wcout << L"hai inserito una stringa corretta\n";

    return 0;
}
```

E' possibile dichiarare uno **```std::smatch```**, e utilizzare ```regex_search``` per riempirlo con le occorrenze trovate; uno ```std::smatch``` è un array non modificabile, con i metodi ```size``` e ```empty```; per convertire l'occorrenza in stringa si utilizza il metodo **```str```**:

```cpp
#include <iostream>
#include <regex>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring text;
    std::wcout << L"inserisci una stringa\n";
    std::getline(std::wcin, text);

    std::wsmatch matches;

    if (std::regex_search(text, matches, std::wregex(L"reg")))
    {
        std::wcout << L"prima occorrenza:\n" << L"posizione : " ;
        std::wcout << matches.position(0)    << L"\ntesto : ";
        std::wcout << matches[0].str();
    }

    return 0;
}
```

+ ```regex_replace``` sostituisce tutte le occorrenze di una regex con una stringa:  

```cpp
#include <iostream>
#include <regex>
#include <string>

int main()
{
    setlocale(0, "");

    std::wstring text;
    std::wcout << L"inserisci una stringa\n";
    std::getline(std::wcin, text);

    std::wsmatch matches;

    // sostituisce tutte le occorrenze con L"not reg"
    if (std::regex_replace(text, std::wregex(L"reg"), L"not reg"))
        std::wcout << L"la nuova stringa è " << text << L'\n';

    return 0;
}
```

<div style="text-align: center;">

#### ***Le regole delle regex***

</div>

Per indicare la presenza di un carattere bisogna aggiungere un backslash (```\\```) solo se il carattere è tra questi (metacarattere):

+ ```.```: corrisponde a qualsiasi carattere singolo eccetto ```\n```
+ ```^```: inizio stringa
+ ```$```: fine stringa
+ ```*```: 0+ occorrenze del carattere precedente
+ ```+```: 1+ occorrenze del carattere precedente
+ ```?```: 0 o 1 occorrenza del carattere precedente
+ ```[]```: un carattere tra quelli elencati nelle parentesi
+ ```()```: un gruppo
+ ```\\```: backslash
+ parentesi graffe

Esempio:

```cpp
std::wregex(L"^12"); // corrisponde a 12 (il 12 è all'inizio)
std::wregex(L"\\^12"); // corrisponde a ^12,
```

Non è eseguita l'escape del carattere backslash: si sta passando una stringa al costruttore della wregex, la stringa contiene solo un carattere backslash.

Le parentesi graffe vengono utilizzate per stabilire quante occorrenze del carattere precedente:

+ ```{x}``` esattamente ```x``` occorrenze
+ ```{x,y}``` tra ```x``` e ```y``` occorrenze
+ ```{x,}``` almeno ```x``` occorrenze

Esempio:

```cpp
std::wregex(L"n{3}"); // corrisponde a L"nnn"
std::wregex(L"n{3,}"); // corrisponde a L"nnn", L"nnnn", ...
```

<div style="page-break-after: always;"></div>

Esistono delle **escape sequence** per le regex (escape con ```\\```):

+ ```\d```: qualsiasi cifra
+ ```\D```: tutto tranne una cifra
+ ```\w```: un carattere che può comparire nel nome di una variabile
+ ```\W```: un carattere che non può comparire nel nome di una variabile
+ ```\s```: uno spazio bianco
+ ```\S```: qualsiasi carattere tranne uno spazio bianco
+ ```\b```: un bordo di parola (prima o dopo un carattere che fa parte di una parola)
+ ```\B```: una posizione che non è un bordo di parola

Le parentesi quadre si usano con queste regole:

+ ```[...]```: quasiasi carattere tra quelli nelle parentesi quadre (i puntini di sospensione sono indicativi)
+ ```[^...]```: qualsiasi carattere che non si trova nelle parentesi quadre
+ ```[A-z]```: qualsiasi carattere compreso tra 'A' e 'z' nella tabella ASCII

Esempio dell'uso delle parentesi quadre:

```cpp
// corrisponde a una sequenza di 2 lettere maiuscole o minuscole
std::wregex(L"[A-Za-z]{2}");
```

Esempio dell'uso delle parentesi tonde:

```cpp
std::wregex(L"(ab)+"); // corrisponde a L"ab", L"abab", ...
```

E' possibile utilizzare l'**operatore di alternanza ```|```** in questo modo:

```cpp
std::wregex(L"(abc)|(123)"); // corrisponde a L"123" o L"abc"
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### I vettori

</div>

In C++ la classe **```std::vector```** (necessario includere **```<vector>```**) viene utilizzata per creare degli array che possono essere estesi o contratti.

<div style="text-align: center;">

#### ***Inizializzare un vettore***

</div>

+ Inizializzazione con **lista di inizializzazione**, esempio completo:

```cpp
#include <iostream>
#include <vector>

int main()
{
    setlocale(0, "");

    std::vector<int> vect{ 5, 4, 7 };
    for (int i = 0; i < vect.size(); ++i)
    {
        std::wcout << L"elemento " << i + 1 << L" del vettore: ";
        std::wcout << vect[i] << L'\n';
    }

    return 0;
}
```

+ Inizializzazione con un altro vettore:

```cpp
std::vector<int> vect{ 1, 2, 3, 4 };
std::vector<int> NewVect{ vect }; // NewVect = { 1, 2, 3, 4 }
```

+ Inizializzazione con l'intervallo di un altro vettore:

```cpp
std::vector<int> vect{ 1, 2, 3, 4, 5 };
std::vector<int> part{ vect.begin() + 1, vect.end() - 1 };
// part = { 2, 3, 4 }
```

+ Inizializzazione con dimensione fissa:

```cpp
std::vector<int> vect(5); // vect ha 5 elementi non inizializzati
```

<div style="page-break-after: always;"></div>

+ Inizializzazione con dimensione fissa e valore:

```cpp
std::vector<int> vect(5, 0) // vect ha 5 elementi di valore 0
```

<div style="text-align: center;">

#### ***Metodi***

</div>

Tra i metodi in comune con le stringhe ci sono:

+ **```size```**: restituisce la dimensione (anche la funzione ```size``` va bene)
+ **```empty```**: restituisce un valore vero se e solo se il vettore è vuoto
+ **```at```**: restituisce un'elemento data la posizione (va bene anche l'operatore ```[]```)
+ Gli operatori ```=``` (assegnazione) e ```==``` (uguaglianza)
+ **```insert```**: inserisce un elemento nel vettore
+ **```erase```**: solo il metodo che elimina un elemento dal vettore
+ **```push_back```**: aggiunge un elemento alla **fine** del vettore
+ **```pop_back```**: elimina l'ultimo elemento dal vettore
+ **```clear```**: rende il vettore nullo

Esempio completo:

```cpp
#include <iostream>
#include <vector>

int main()
{
    setlocale(0, "");
    std::vector<int> OddNumbers(100);
    for (int i = 0; i < size(OddNumbers); ++i)     // funzione size
        OddNumbers.at(i) = 2 * i + 1;              // metodo at
    
    // elimina il settimo elemento, cioè 13
    OddNumbers.erase(OddNumbers.begin() + 6);      // metodo erase
    // inserisce -1 alla settima posizione
    OddNumbers.insert(OddNumbers.begin() + 6, -1); // metodo insert

    // elimina l'ultimo elemento di OddNumbers
    OddNumbers.pop_back();                         // metodo pop_back
    
    // size restituisce un size_t
    size_t size = OddNumbers.size();               // metodo size

    // estensione di OddNumbers
    for (int i = size; i < 2 * size; ++i)
        OddNumbers.push_back(2 * i + 1);           // metodo push_back
    
    // output
    for (int i = 0; i < OddNumbers.size(); ++i)
    {
        if (i == 6) continue;

        std::wcout << L"numero dispari #" << i + 1;
        std::wcout << L" = " << OddNumbers[i];     // operatore []
        std::wcout << L'\n';
    }

    OddNumbers.clear();                            // metodo clear
    OddNumbers.empty() ?                           // metodo empty
        std::wcout << L"il vettore è stato reso nullo\n" :
        std::wcout << L"qualcosa è andato storto\n";

    // se il vettore è nullo 'return 0' altrimenti 'return 1'
    return !OddNumbers.empty();
}
```

<div style="text-align: center;">

### ```queue``` e ```deque```

</div>

Oltre a ```std::vector``` ci sono altre due classi simili in C++:
**```std::queue```** (includi **```<queue>```**) e **```std::deque```** (includi **```<deque>```**).

<div style="text-align: center;">

#### ***```std::queue```***

</div>

```std::queue``` ha tre metodi nuovi oltre a ```size``` ed ```empty```:

+ **```push```**: aggiunge un elemento alla fine
+ **```pop```**: rimuove l'elemento all'**inizio**
+ **```front```**: accede all'elemento all'inizio (senza modificarlo)

Non ha metodi per accedere a elementi al centro

<div style="text-align: center;">

#### ***```std::vector``` e ```std::deque```***

</div>

```std::deque``` aggiunge questi due metodi a ```std::vector```:

+ **```push_front```**: aggiunge un elemento all'inizio
+ **```pop_front```**: rimuove l'elemento all'inizio

Tuttavia è preferibile usare ```std::vector``` quando possibile perché ```std::deque``` utilizza gli **indici circolari** per rendere efficienti le operazioni all'inizio e alla fine dell'array, ma questo significa utilizzare l'operatore modulo per accedere agli elementi, rallentando l'accesso.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le mappe

</div>

In C++ le classi **```std::map```** e **```std::unordered_map```** servono per creare oggetti che associano a ogni elemento una chiave unica, le chiavi vengono messe in ordine crescente o alfabetico solo in ```std::map```.

<div style="text-align: center;">

#### ***Dichiarazione***

</div>

Esempio di dichiarazione di una mappa:

```cpp
#include <map>

// mappa con una chiave stringa
std::map<std::wstring, int> Map;
```

Esempio di dichiarazione di una mappa non ordinata:

```cpp
#include <unordered_map>
std::unordered_map<std::wstring, int> Map;
```

<div style="text-align: center;">

#### ***Inserimento***

</div>

Si usa il metodo **```insert```** o l'operatore **```=```**

```cpp
#include <map>
#include <string>

int main() {
    // le chiavi vengono ordinate in ordine alfabetico
    std::map<std::wstring, int> ordinals {
        { L"one"  , 1 },
        { L"two"  , 2 },
        { L"three", 3 },
        { L"four" , 4 },
        { L"five" , 5 },
        { L"six"  , 6 },
        { L"seven", 7 },
        { L"eight", 8 },
        { L"nine" , 9 }
    };

    // primo e secondo modo di inserire un elemento
    map.insert({ L"ten", 10 });
    map[L"eleven"] = 11;
    return 0;
}
```

<div style="text-align: center;">

#### ***Eliminazione***

</div>

Si usa il metodo **```erase```**:

```cpp
#include <map>
#include <string>

int main() {
    std::map<std::wstring, int> ordinals
    {
        { L"one"  , 1 },
        { L"two"  , 2 },
        { L"three", 3 },
    };

    map.erase(L"one");
    return 0;
}
```

<div style="text-align: center;">

#### ***Capire se la mappa contiene l'elemento***

</div>

```cpp
#include <iostream>
#include <map>
#include <string>

int main() {
    setlocale(0, "");

    std::map<std::wstring, int> ordinals
    {
        { L"one"  , 1 },
        { L"two"  , 2 },
        { L"three", 3 },
        { L"four" , 4 },
        { L"five" , 5 },
        { L"six"  , 6 },
        { L"seven", 7 },
        { L"eight", 8 },
        { L"nine" , 9 }
    };
    std::wstring ordinal;
    std::wcout << L"Inserisci una stringa\n"
    std::wcin >> ordinal;

    if (ordinals.find(L"ordinal") == ordinals.end())
    {
        std::wcout << L"la stringa non corrisponde a un";
        std::wcout << L" numero da 1 a 9\n";
        return 0;
    }

    std::wcout << L"la stringa corrisponde a " << ordinals[ordinal];
    return 0;
}
```

<div style="text-align: center;">

#### ***Iterare su ogni elemento***

</div>

Ogni elemento di una mappa accede alla chiave con **```first```** e al valore con **```second```**.

```cpp
#include <iostream>
#include <map>
#include <string>

int main() {
    setlocale(0, "");

    std::map<std::wstring, int> ordinals
    {
        { L"one"  , 1 },
        { L"two"  , 2 },
        { L"three", 3 },
        { L"four" , 4 },
        { L"five" , 5 },
        { L"six"  , 6 },
        { L"seven", 7 },
        { L"eight", 8 },
        { L"nine" , 9 }
    };

    std::wcout << L"numeri da 1 a 9 in ordine alfabetico:\n";
    for (const auto& ord : ordinals)
        std::wcout << ord.first << L'(' << ord.second << L")\n";

    return 0;
}
```

<div style="text-align: center;">

#### ***Differenze***

</div>

```std::unordered_map``` differisce da ```std::map``` perché non ordina le chiavi e usa una **tabella hash** per accedere agli elementi (tempo di O(1))

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Misurare il tempo

</div>

<div style="text-align: center;">

#### ***Utilizzo di ```std::chrono```***

</div>

Ci sono tre tipi di clock:

+ ```std::chrono::system_clock```: orologio utilizzato per l'ora corrente, può essere influenzato da cambiamenti manuali dell'ora
+ ```std::chrono::steady_clock```: orologio utilizzato per misurare intervalli di tempo
+ ```std::chrono::high_resolution_clock```: è l'orologio più preciso tra i tre

Esempio d'uso:

```cpp
#include <iostream>
#include <chrono>

int main()
{
    setlocale(0, "");

    auto start = std::chrono::high_resolution_clock::now();

    // codice...
    // ...

    auto end = std::chrono::high_resolution_clock::now();
    std::wcout << L"tempo trascorso: ";

    std::wcout << std::chrono::duration_cast
        <std::chrono::nanoseconds>(end - start).count();

    std::wcout << L" microsecondi\n";

    return 0;
}
```

<div style="text-align: center;">

#### ***Utilizzo delle API di Windows***

</div>

```cpp
#include <iostream>
#include <Windows.h>

int main()
{
    setlocale(0, "");

    LARGE_INTEGER frequency, start, end;
    QueryPerformanceFrequency(&frequency);
    QueryPerformanceCounter(&start);

    // codice...
    // ...

    QueryPerformanceCounter(&end);
    double duration =
        double(end.QuadPart - start.QuadPart) / frequency.QuadPart;
    std::wcout << L"tempo trascorso: " << duration << L" secondi\n";

    return 0;
}
```

<div style="text-align: center;">

#### ***Utilizzo di ```GetTickCount```***

</div>

Queste funzioni contano i millisecondi dall'accensione del sistema, tuttavia la precisione è limitata.

```cpp
#include <iostream>
#include <Windows.h>

int main()
{
    setlocale(0, "");

    DWORD start = GetTickCount64();

    // codice...
    // ...

    DWORD end = GetTickCount64();
    std::wcout << L"tempo trascorso: " << (end - start);
    std::wcout << L" millisecondi\n";

    return 0;
}
```

Viene utilizzato ```GetTickCount64``` al posto di ```GetTickCount``` perché ```GetTickCount``` va in overflow dopo circa 50 giorni.

<div style="text-align: center;">

#### ***Utilizzo di ```clock```***

</div>

Questa è una funzione definita nell'header **```<ctime>```**, che su Windows ha una precisione pressoché uguale a ```GetTickCount```, definita dalla macro ```CLOCKS_PER_SEC```. Non è un approccio adatto alla misurazione del tempo reale, perché misura il numero di clock ticks della CPU del computer.

<div style="page-break-after: always;"></div>

Esempio:

```cpp
#include <ctime>
#include <iostream>

int main()
{
    setlocale(0, "");

    clock_t start = clock();

    // codice...
    // ...

    clock_t end   = clock();

    std::wcout << L"tempo trascorso: ";
    std::wcout << double(end - start) / CLOCKS_PER_SEC;
    std::wcout << L" secondi\n";

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Generare dei numeri casuali

</div>

<div style="text-align: center;">

#### ***Con la funzione ```rand```***

</div>

L'utilizzo di ```rand``` è limitato perché il massimo è di solito impostato a 32767.

```cpp
#include <iostream>
#include <ctime>

int main()
{
    setlocale(0, "");

    std::srand(std::time(NULL)); // impostazione del seme
    std::wcout << std::rand();

    return 0;
}
```

<div style="text-align: center;">

#### ***Con i ```random_device```***

</div>

Questo è un metodo che genera numeri casuali di alta qualità, tuttavia è lento, esempio:

```cpp
#include <iostream>
#include <random>

int main()
{
    setlocale(0, "");

    std::random_device rnd;
    std::wcout <<      rnd();

    return 0;
}
```

<div style="text-align: center;">

#### ***Con il mersenne twister***

</div>

Questo metodo è più veloce rispetto ai ```random_device``` perché il numero casuale viene calcolato una sola volta per impostare il seme, e a partire da esso si usa un generatore pseudo-casuale per generare degli altri numeri casuali.

<div style="page-break-after: always;"></div>

Esempio:

```cpp
#include <iostream>
#include <random>

int main()
{
    setlocale(0, "");

    std::random_device rnd;
    std::mt19937 generator(rnd());
    std::uniform_int_distribution<> distr(1, 100);

    std::wcout << distr(generator);

    return 0;
}
```

Se l'intervallo è molto grande è sufficiente cambiare il template di ```uniform_int_distribution```:

```cpp
#include <iostream>
#include <random>

int main()
{
    setlocale(0, "");

    std::random_device rnd;
    std::mt19937 generator(rnd());
    std::uniform_int_distribution<long long> distr(0, 1e14);

    std::wcout << distr(generator);

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

---

<h2 style="text-align: center;"><b>Livello Advanced</b></h2>

---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Le classi

</div>

In C++ una classe è una struttura che può contenere dei **metodi**, cioè delle funzioni, oltre alle variabili.

In una classe, si possono definire dei **costruttori** cioè delle funzioni che servono a inizializzare la classe, è anche possibile definire il **distruttore**, una funzione che viene chiamata quando la classe deve essere distrutta.

Variabili (**campi**), metodi, costruttori e distruttore si dicono **membri** della classe, un membro è **pubblico**, se ovunque nel codice si può accedere a esso, o **privato** se ci si può accedere solo dalla classe.

In realtà anche una struttura può contenere dei metodi, la differenza tra una struttura e una classe è il fatto che in una struttura i membri sono pubblici per impostazione predefinita, ed esistono anche dei **costruttori** predefiniti, mentre in una classe i membri sono privati per opzione predefinita.

Per dichiarare una classe si fa così:

```cpp
class Class1
{
    // membri
};
```

Esempio completo di una classe:

```cpp
#include <iostream>
#include <numbers>

class Circle
{
public:
    int radius;

    int Diameter()
    {
        return 2 * radius;
    }
    double Circumference()
    {
        return std::numbers::pi * radius;
    }
    long double Area()
    {
        return std::numbers::pi * radius * radius;
    }
};

int main()
{
    setlocale(0, "");

    Circle c1;
    std::wcout << L"inserisci il raggio del cerchio: ";
    std::wcin >> c1.radius;

    std::wcout << L"il diametro è: "        << c1.Diameter();
    std::wcout << L"\nla circonferenza è: " << c1.Circumference();
    std::wcout << L"\nl'area è: "           << c1.Area();

    return 0;
}
```

In questo caso, la classe ```Circle``` è usata per creare un **oggetto** ```c1```.

La parola chiave **public** denota quali membri sono pubblici, per rendere dei membri privati si usa la parola chiave **private**.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### I costruttori e il distruttore

</div>

In una classe in C++ un **costruttore** si distingue da un metodo perché ha lo stesso nome della classe, possono esistere più costruttori, ma devono avere firme diverse, anche il **distruttore** ha lo stesso nome della classe, ma deve essere preceduto da un carattere ```~``` (premere ALT + 126 dal tastierino numerico, num lock deve essere disattivato).

<div style="text-align: center;">

#### ***Sintassi dei costruttori***

</div>

Esempio:

```cpp
    Circle(int R)
    {
        radius = std::abs(R);
    }
```

Che si può riscrivere così:

```cpp
    Circle(int R) : radius(std::abs(R)) {}
```

Gli oggetti di una determinata classe devono sempre essere inizializzati con i paramteri di un costruttore, quindi di solito si aggiunge un costruttore di default:

```cpp
    Circle()      : radius(0)           {}
    Circle(int R) : radius(std::abs(R)) {}
```

Grazie a questi costruttori un oggetto può essere inizializzato in questi modi:

```cpp
int main()
{
    Circle c1, c2(1), c3{ 5 };

    // il resto del codice

    return 0;
}
```

<div style="text-align: center;">

#### ***Sintassi del distruttore***

</div>

Ecco un esempio di come si può implementare il distruttore con la classe ```Circle```:

<div style="page-break-after: always;"></div>

```cpp
#include <iostream>
#include <numbers>

class Circle
{
public:
    int radius;

    // costruttore di default
    Circle()      : radius(0)           {}

    // costruttore con parametro
    Circle(int R) : radius(std::abs(R)) {}

    // distruttore
    ~Circle()
    {
        setlocale(0, "");
        std::wcout << L"\nl'oggetto è stato distrutto\n";
    }

    int Diameter()
    {
        return 2 * radius;
    }
    double Circumference()
    {
        return std::numbers::pi * radius;
    }
    long double Area()
    {
        return std::numbers::pi * radius * radius;
    }
};

int main()
{
    setlocale(0, "");

    Circle c1;
    std::wcout << L"inserisci il raggio del cerchio: ";
    std::wcin >> c1.radius;

    std::wcout << L"il diametro è: " << c1.Diameter();
    std::wcout << L"\nla circonferenza è: " << c1.Circumference();
    std::wcout << L"\nl'area è: " << c1.Area();

    return 0; // qui viene chiamato il distruttore
}
```

<div style="text-align: center;">

#### ***Il costruttore di copia***

</div>

Quando un oggetto viene passato a una funzione per valore, una funzione ritorna un oggetto, o un oggetto viene inizializzato con un altro oggetto della stessa classe, viene chiamato il **costruttore di copia**:

```cpp
class Circle
{
    using std::numbers::pi;
public:
    int radius;

    // costruttore di default
    Circle()              : radius(0)            {}

    // costruttore con parametro
    Circle(int R)         : radius(std::abs(R))  {}

    // costruttore di copia
    Circle(Circle& other) : radius(other.radius) {}

    // distruttore
    ~Circle()
    {
        setlocale(0, "");
        std::wcout << L"\nl'oggetto è stato distrutto\n";
    }

    int         Diameter()      { return 2  * radius;          }
    double      Circumference() { return pi * radius;          }
    long double Area()          { return pi * radius * radius; }
};
```

Esempio in cui viene chiamato il costruttore di copia:

```cpp
int main()
{
    Circle first = 10;

    // chiamata al costruttore di spostamento
    // c1 è inizializzato come una copia di first
    Circle c1 = first;

    return 0;
}
```

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Il costruttore di spostamento***

</div>

Quando un oggetto viene spostato (con **```std::move```**) si chiama il **costruttore di spostamento**:

```cpp
class Circle
{
    using std::numbers::pi;
public:
    int radius;

    // costruttore di default
    Circle()                        : radius(0)            {}

    // costruttore con parametro
    Circle(int R)                   : radius(std::abs(R))  {}

    // costruttore di copia
    Circle(Circle& other)           : radius(other.radius) {}

    // costruttore di spostamento
    Circle(Circle&& other) noexcept : radius(other.radius) {}

    // distruttore
    ~Circle()
    {
        setlocale(0, "");
        std::wcout << L"\nl'oggetto è stato distrutto\n";
    }

    int         Diameter()      { return 2  * radius;          }
    double      Circumference() { return pi * radius;          }
    long double Area()          { return pi * radius * radius; }
};
```

In un costruttore di spostamento di utilizza **```noexcept```** per non solleverà mai un'eccezione.

Esempio in viene chiamato il costruttore di spostamento:

```cpp
int main()
{
    Circle first = 10;

    // chiamata al costruttore di spostamento
    // c1 è inizializzato a first e first è distrutto 
    Circle c1 = std::move(first);

    return 0;
}
```

<div style="text-align: center;">

#### ***Costruttore con ```std::initializer_list```***

</div>

**```std::initializer_list```** è una classe utilizzata nei costruttori di classi più complesse (come ```std::vector```), ha il metodo ```size```.

Vediamo una classe con un costruttore che accetta una lista di inizializzazione come argomento e inizializza delle variabili con somma e prodotto:

```cpp
#include <initializer_list>
#include <iostream>

class DataProcesser
{
public:
    int sum;
    int prod;

    DataProcesser()                                : sum(0), prod(1) {}
    DataProcesser(std::initializer_list<int> data) : sum(0), prod(1)
    {
        for (const auto& n : data) {
            sum  += n;
            prod *= n;
        }
    }

    void print() const
    {
        setlocale(0, "");

        std::wcout << L"somma:    " << sum  << L'\n';
        std::wcout << L"prodotto: " << prod << L'\n';
    }
};

int main()
{
    setlocale(0, "");

    DataProcesser Data{ 2, -3, -1, 9, 4 };
    Data.print();

    return 0;
}
```

Qui si utilizza ```const``` dopo ```print()``` per indicare che il metodo non può modificare i campi della classe, se invece si mette ```const``` prima del nome di un parametro, si indica che è il parametro a non poter essere modificato.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### L'ereditarietà

</div>

In C++ una classe può **ereditare** da un'altra classe, questo significa che avrà tutti i membri protetti e pubblici della classe base.

<div style="text-align: center;">

#### ***Derivare una classe***

</div>

Un membro si dice **protetto** (parola chiave **```protected```**) se è accessibile solo alla classe base e a eventuali classi **derivate** (cioè classi che ereditano dalla classe base).

Ecco un esempio di classe derivata da ```std::vector```:

```cpp
#include <initializer_list>
#include <iostream>
#include <string>
#include <vector>

class vector_t : std::vector<int>
{
public:

    // costruttori
    vector_t() {}
    vector_t(std::initializer_list<int> list)
    {
        for (const auto& n : list) push_back(n);
    }

    std::wstring string()
    {
        std::wstring output = L"{";
        for (int i = 0; i < size() - 1; ++i)
            output += L' ' + at(i);

        output += at(size() - 1);
        return output;
    }

    void print()
    {
        std::wcout << string();
    }

    void println()
    {
        std::wcout << string() << L'\n';
    }
};
```

<div style="page-break-after: always;"></div>

Questa classe aggiunge dei metodi a ```std::vector```, ma adesso il codice esterno non riesce ad accedere ai membri di ```std::vector``` da ```vector_t```, questo perché quando una classe eredita da un'altra, tutti i membri ereditati sono **privati**, per risolvere questo problema bisogna aggiungere ```public``` prima del nome della classe base:

```cpp
#include <initializer_list>
#include <iostream>
#include <string>
#include <vector>

class vector_t : public std::vector<int>
{
    // il resto della classe
};
```

<div style="text-align: center;">

#### ***Ereditare i costruttori***

</div>

Quando si deriva una classe, essa non eredita i costruttori, tuttavia ciò si risolve facilmente con ```using```, esempio:

```cpp
#include <initializer_list>
#include <iostream>
#include <string>
#include <vector>
class vector_t : public std::vector<int>
{
    using std::vector<int>::vector;

    // il resto della classe
};
```

<div style="text-align: center;">

#### ***Sovrascrivere un metodo***

</div>

Una classe derivata può **sovrascrivere** un metodo della classe base con la parola chiave **```override```** solo se la classe base ha dichiarato il metodo come **```virtual```**, in questo modo la classe derivata eseguirà sempre la sua versione sovrascritta del metodo invece di quella originaria:

```cpp
#include <iostream>

class Base
{
public:

    virtual void show() const
    {
        setlocale(0, "");
        std::wcout << L"questa è la classe base\n";
    }
};

class Derived : public Base
{
    void show() const override
    {
        setlocale(0, "");
        std::wcout << L"questa è la classe derivata\n";
    }
};
```

<div style="text-align: center;">

#### ***Il puntatore ```this```***

</div>

Quando un paramtero in una classe ha lo stesso nome di un campo, è possibile usare il **puntatore ```this```** per accedere al campo, esso è un puntatore che viene passato implicitamente a tutti i metodi non statici di una classe, si può dereferenziare ```this``` per ottenere l'oggetto su cui è stato chiamato il metodo.

Esempio d'uso:

```cpp
#include <iostream>
#include <string>

class MyClass
{
    // campi privati
    int x;
    int y;

    // metodi pubblici
public:

    MyClass(int x, int y)
    {
        setlocale(0, "");

        this->x = x;
        this->y = y;

        // stessa cosa usare this->str()
        std::wcout << L"oggetto corrente: " << (*this).str() << L'\n';
    }

    std::wstring str()
    {
        return L'{' + std::to_wstring(x) + L", " + std::to_wstring(y) + L'}';
    }
};
```

<div style="text-align: center;">

#### ***Costruttori e distruttori***

</div>

Il costruttore della classe base viene chiamato prima di quello della classe derivata, mentre il distruttore della classe derivata viene chiamato prima di quello della classe base.

E' possibile chiamare il costruttore della classe base nel costruttore della classe derivata:

```cpp
#include <iostream>

class Base
{
public:
    Base() {}
    Base(const Base&)
    {
        setlocale(0, "");
        std::wcout << L"costruttore di copia della classe base\n";
    }
};

class Derived : public Base
{
public:
    Derived() {}
    Derived(const Derived&) : Base(*this)
    {
        setlocale(0, "");
        std::wcout << L"costruttore di copia della classe derivata\n";
    }
};
```

In questo caso non è stato scritto il nome del parametro del costruttore perché esso non è utilizzato.  
Se i costruttori presentano dei parametri si può fare così:

```cpp
#include <iostream>

class Base
{
public:
    Base() {}
    Base(int x)
    {
        setlocale(0, "");
        std::wcout << L"costruttore Base con parametro ";
        std::wcout << x << L'\n';
    }
};



class Derived : public Base
{
public:
    Derived() {}
    Derived(int x, int y) : Base(x)
    {
        setlocale(0, "");
        std::wcout << L"costruttore Derived con parametro ";
        std::wcout << y << L'\n';
    }
};
```

<div style="text-align: center;">

#### ***Distruttore virtuale***

</div>

Quando si distrugge con ```delete``` un oggetto di una classe derivata tramite un puntatore alla classe base, se il distruttore non è virtuale verrà chiamato solo quello della classe base, causando potenziali perdite di memoria:

```cpp
#include <iostream>

class Base
{
public:
    Base ()    { std::wcout << L"costruttore Base\n"; }
    ~Base()    { std::wcout << L"distruttore Base\n"; }
};

class Derived : public Base
{
public:
    Derived () { std::wcout << L"costruttore Derived\n"; }
    ~Derived() { std::wcout << L"distruttore Derived\n"; }
};

int main()
{
    Base* obj = new Derived();
    delete obj; // il distruttore Derived non verrà chiamato
    return 0;
}
```

<div style="page-break-after: always;"></div>

In questi casi si rende il distruttore virtuale:

```cpp
#include <iostream>

class Base
{
public:
            Base () { std::wcout << L"costruttore Base\n"; }
    virtual ~Base() { std::wcout << L"distruttore Base\n"; }
};

class Derived : public Base
{
public:
    Derived ()      { std::wcout << L"costruttore Derived\n"; }
    ~Derived()      { std::wcout << L"distruttore Derived\n"; }
};
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Il sovraccarico degli operatori

</div>

In una classe in C++ si possono definire degli operatori con il **sovraccarico**, si scrive una funzione il cui nome è ```operator``` seguito dall'operatore, qui ne vedremo alcuni.

<div style="text-align: center;">

#### ***Sovraccarico dell'operatore ```=```***

</div>

Vediamo come si può sovraccaricare l'operatore di assegnazione di questa classe ```coord```:

```cpp
#include <iostream>
#include <string>

class coord
{
public:
    int X;
    int Y;

    coord()                             : X(0)      , Y(0)       {}
    coord(int x, int y)                 : X(x)      , Y(y)       {}
    coord(const coord& other)           : X(other.X), Y(other.Y) {}
    coord(const coord&& other) noexcept : X(other.X), Y(other.Y) {}

    coord& operator=(const coord other)
    {
        X = other.X;
        Y = other.Y;
        return *this;
    }

    std::wstring str() const
    {
        return L'{' + std::to_wstring(X) + L", " + std::to_wstring(Y) + L'}';
    }
};
```

Con questo operatore ```=``` si può assegnare un ```coord``` a un altro ```coord```, la funzione restituisce un ```coord&```, dove l'operatore di indirizzo indica che viene restituito un riferimento al risultato, questo serve per poter fare delle assegnazioni multiple con una istruzione:

```cpp
int main()
{
    setlocale(0, "");

    coord c_one{ 1, 2 }, c_two, c_three, c_four, c_five;
    cfive = cfour = cthree = ctwo = cone;



    std::wcout << c_one.str()   << L'\n';
    std::wcout << c_two.str()   << L'\n';
    std::wcout << c_three.str() << L'\n';
    std::wcout << c_four.str()  << L'\n';
    std::wcout << c_five.str()  << L'\n';


    return 0;
}
```

Spiegazione: quando si esegue ```c_two = c_one```, a ```c_two``` viene assegnato il valore di ```c_one```, ma l'operatore restituisce ```*this``` cioè il risultato, di conseguenza a ```c_three``` viene assegnato il valore del risultato, e così via.

<div style="text-align: center;">

#### ***Sovraccarico degli operatori logici e di confronto***

</div>

Esempi:

+ Operatori ```&&``` e ```||```

```cpp
bool operator&&(const coord other) const
{
    return (X != 0 && Y != 0) && (other.X != 0 and other.Y != 0);
}
bool operator||(const coord other) const
{
    return (X != 0 && Y != 0) || (other.X != 0 and other.Y != 0);
}
```

Questi due operatori consentono di comparare i valori booleani delle due coordinate, in questo caso, una coordinata è falsa se e solo se è nulla.

+ Operatori ```<```, ```>```, ```<=```, ```>=```, ```==``` e ```!=```

```cpp
bool operator==(const coord other) const
{
    return X == other.X && Y == other.Y;
}
bool operator!=(const coord other) const
{
    return X != other.X || Y != other.Y;
}
bool operator<(const coord other) const
{
    return std::hypot(X, Y) <  std::hypot(other.X, other.Y);
}
bool operator>(const coord other) const
{
    return std::hypot(X, Y) >  std::hypot(other.X, other.Y);
}
bool operator<=(const coord other) const
{
    return std::hypot(X, Y) <= std::hypot(other.X, other.Y);
}
bool operator>=(const coord other) const
{
    return std::hypot(X, Y) >= std::hypot(other.X, other.Y);
}
```

In questo caso confrontiamo i moduli delle due coordinate (le distanze da {0, 0}), che si calcolano con il teorema di pitagora (```std::hypot```).

<div style="text-align: center;">

#### ***Sovraccarico degli operatori aritmetici***

</div>

```cpp
coord operator+(const coord other) const
{
    coord result = *this;
    result.X += other.X;
    result.Y += other.Y;
    return result;
}
coord& operator+=(const coord other)
{
    *this = *this + other;
    return  *this;
}
coord& operator++()    // ++ pre-fisso  (++a)
{
    *this = *this + coord{ 1, 0 };
    return  *this;
}
coord& operator++(int) // ++ post-fisso (a++)
{
    *this = *this + coord{ 0, 1 };
    return  *this;
}
```

Il riferimento (```&```) si trova solo sul tipo restituito dagli operatori ```+=``` e ```++``` perché quel risultato viene assegnato solo in caso di una seconda operazione (```c = a += b```) invece di una sola operazione come con l'operatore ```+``` (```c = a + b```).

L'operatore ```++``` post-fisso si distingue da quello pre-fisso perché accetta un parametro di tipo ```int```, ma esso non viene mai usato.

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Sovraccarico degli operatori speciali***

</div>

+ Operatore ```->```  

```cpp
coord* operator->()
{
    return this;
}
```

Si esegue ```return this``` invece di ```return *this``` perché si sta restituendo un puntatore.

+ Operatore ```()```

E' possibile utilizzare l'operatore ```()``` per eseguire una chiamata di funzione con un oggetto (**funtore**):

```cpp
coord operator()(int scalar) const
{
    coord result = *this;
    result.X *= scalar;
    result.Y *= scalar;
    return result;
}
```

In questo caso viene utilizzato l'operatore ```()``` per eseguire il prodotto per uno scalare, adesso questo operatore si può utilizzare così:

```cpp
int main()
{
    setlocale(0, "");
    coord Coord{ 2, -1 };

    // output = {6, -3}
    std::wcout << L"triplo della coordinata: " << Coord(3).str();
    std::wcout << L'\n';

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### I template

</div>

In C++ i **template** permettono di creare codice generico, utilizzabile con diversi datatype allo stesso modo.

<div style="text-align: center;">

#### ***Funzioni template***

</div>

Vediamo alcuni esempi di funzioni template:

```cpp
template<typename T> static void swap(T& A, T& B)
{
    auto temp = B;
    A = temp;
    B = A;
}
template<class T> T add(T A, T B)      { return A + B; }
template<class T> T subtract(T A, T B) { return A - B; }
```

In questo modo si evita di scrivere funzioni diverse per datatype diversi, evitando la duplicazione del codice.

L'utilizzo di ```class``` al posto di ```typename``` non cambia nulla, sono solo due diversi modi di scrivere un template, ```T``` è il nome di un datatype che vale solo all'interno della funzione, il suo reale datatype viene determinato dai parametri nella chiamata di funzione:

```cpp
int main()
{
    setlocale(0, "");

    std::wcout << L"1 + 2 è "     << add(1, 2)          << L'\n';
    std::wcout << L"1.5 - 2.3 è " << subtract(1.5, 2.3) << L'\n';

    return 0;
}
```

<div style="text-align: center;">

#### ***Template doppi***

</div>

E' possibile scrivere una funzione con più di un template come in questo esempio:

```cpp
template<class T, class U> T add(T A, U B)      { return A + B; }
template<class T, class U> T subtract(T A, U B) { return A - B; }
```

Per usare funzioni di questo genere è buona pratica specificare i template nella chiamata di funzione (per prevenire errori di compilazione):

<div style="page-break-after: always;"></div>

```cpp
int main()
{
    setlocale(0, "");

    std::wcout << L"1 + 2.21 è ";
    std::wcout << add<int, double>(1, 2.21)     << L'\n';
    
    std::wcout << L"1.5 - 2 è ";
    std::wcout << subtract<double, int>(1.5, 2) << L'\n';

    return 0;
}
```

<div style="text-align: center;">

#### ***Classi template***

</div>

Anche le strutture possono essere template, ma il ragionamento è analogo; le classi template si distinguono dalle funzioni template perché bisogna sempre specificare il template (anche se è uno solo).

Esempio:

```cpp
template<class Ty> class MyClass
{
public:
    Ty data;
    MyClass(Ty val) : data(val) {}
};

// oggetto di tipo int
MyClass<int>    intObj(4);

// oggetto di tipo double
MyClass<double> doubleObj(7.5);
```

La sintassi infatti è molto simile a classi come ```std::vector``` o ```std::queue```, questo perché sono **classi template** anche loro, le mappe invece hanno un **template doppio**.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Tecniche avanzate dei template

</div>

In C++ i template hanno un sacco di utilizzi, qui vedremo quelli avanzati.

<div style="text-align: center;">

#### ***Template facoltativi e alias***

</div>

Per definire un alias di una classe template la sintassi cambia leggermente rispetto a un alias normale.

Esempio di alias normale:

```cpp
using vector_int = vector<int>;
```

Esempio di alias di template:

```cpp
template<typename T> using vec = vector<T>;
```

Nel primo esempio ```vector_int``` è un vettore di interi, mentre nel secondo esempio ```vec``` è un vettore di qualsiasi template.  
Si può impostare un valore predefinito al template, per esempio int:

```cpp
#include <vector>
template<typename T = int> using vec = std::vector<T>;

int main()
{
    vec<>       intvect{ 1, 2, 3 };
    vec<double> dblvect{ 1.0, 2.0, 3.0 };
    return 0;
}
```

<div style="text-align: center;">

#### ***Template con valori costanti***

</div>

I template possono accettare parametri che non sono tipi (ma devono essere integrali, puntatori o riferimenti), esempio:

```cpp
template<typename T, int size> static void BubbleSort(T arr[])
{
    for (int i = 0; i < size - 1; ++i)
        for (int j = 0; j < size - i - 1; ++j)
            if (arr[j] > arr[j + 1])
                std::swap(arr[j], arr[j + 1]);
}
```

Viene passato un parametro integrale ```size``` al template, non alla funzione (ma cambia solo la sintassi della chiamata di funzione, per il resto la logica è la stessa).

<div style="text-align: center;">

#### ***La specializzazione di un template***

</div>

Si utilizza questa tecnica quando si vuole creare un'altra versione di un blocco di codice solo per un template particolare.

```cpp
#include <iostream>

template<typename T> class MyClass
{
public:
    void show()
    {
        std::wcout << L"versione generica\n";
    }
};

template<> class MyClass<bool>
{
public:
    void show()
    {
        std::wcout << L"versione specializzata con template bool\n";
    }
};

int main()
{
    MyClass<int>  obj1;
    obj1.show();  // output = versione generica

    MyClass<bool> obj2;
    // output = versione specializzata con template bool
    obj2.show();

    return 0;
}
```

Questa era una **specializzazione totale**, si parla di **specializzazione parziale** quando la versione specializzata ha un template che dipende da quello della versione base, esempio:

<div style="page-break-after: always;"></div>

```cpp
#include <iostream>

template<typename T> class MyClass
{
public:
    void show()
    {
        std::wcout << L"template valore\n";
    }
};

template<typename T> class MyClass<T*>
{
public:
    void show()
    {
        std::wcout << L"template puntatore\n";
    }
};

int main()
{
    MyClass<int>  obj1;
    obj1.show();  // output = template valore

    MyClass<int*> obj2;
    obj2.show();  // output = template puntatore

    return 0;
}
```

<div style="text-align: center;">

#### ***Template variadici***

</div>

I template variadici consentono di accettare un numero variabile di parametri di tipo:

```cpp
#include <iostream>

template<typename... Args> static void write(Args... args)
{
    setlocale(0, "");
    (std::wcout << ... << args) << L'\n';
}

int main()
{
    write(23, L' ', 1.05, L"written"); // output = 23 1.05written
    return 0;
}
```

I puntini di sospensione vengono espansi dal compilatore in questo modo: ```std::wcout << 23 << L' ' << 1.05 << L"written"```.

La stessa cosa si può fare anche in questo modo:

```cpp
#include <iostream>

template<typename T>       static void print_single(T value)
{
    std::wcout << value << L'\n';
}

template<typename... Args> static void print(Args... args)
{
    (print_single(args), ...);
}

int main()
{
    write(23, L' ', 1.05, L"written");
    return 0;
}
```

<div style="text-align: center;">

#### ***```<type_traits>```***

</div>

Il file header ```<type_traits>``` contiene alcune classi importanti per controllare di quale datatype è un template, vediamo i principali:

+ **```std::is_same```**:

```cpp
if constexpr (std::is_same<T, int>::value)
{
    // codice da eseguire se T è un intero
}
```

E' molto importante l'utilizzo di ```constexpr```, perché ```std::is_same``` agisce a tempo di compilazione, lo stesso codice si può riscrivere così:

```cpp
if constexpr (std::is_same_v<T, int>)
{
    // codice da eseguire se T è un intero
}
```

<div style="page-break-after: always;"></div>

+ **```std::is_integral```**:

```cpp
if constexpr (std::is_integral<T, int>::value)
{
    // codice da eseguire se T è integrale
}
```

Il codice si può riscrivere così:

```cpp
if constexpr (std::is_integral_v<T, int>)
{
    // codice da eseguire se T è integrale
}
```

Tra le altre classi ci sono:

+ **```is_void```**
+ **```is_null_pointer```**
+ **```is_floating_point```** (controlla se un numero è decimale)
+ **```is_array```**
+ **```is_enum```**
+ **```is_class```** (controlla se è di tipo classe o struttura)
+ **```is_function```**
+ **```is_pointer```**

Con i template, **```std::enable_if```** permette di abilitare una porzione di codice se e solo se una condizione è vera, in questo caso, se T è integrale.

```cpp
template<typename T>
typename std::enable_if<std::is_integral<T>::value, T>::type
add(T A, T B) { return A + B; }
```

Questo codice può essere riscritto in questo modo con i **concetti**:

```cpp
template<typename T> concept Integral = std::is_integral_v<T>;

template<Integral T> T add(T a, T b)  { return a + b;        }
```

La differenza è che nel secondo codice avviene un errore di compilazione se la condizione non è rispettata invece di disattivare il codice.

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Metaprogrammazione***

</div>

La **metaprogrammazione** consiste nel fare calcoli a tempo di compilazione, e ciò si può fare con i template, come in questo esempio:

```cpp
template<int N> struct Factorial {
    static const int value = N * Factorial<N - 1>::value;
};
template<> struct Factorial<1> {
    static const int value = 1;
};
template<> struct Factorial<0> {
    static const int value = 1;
};

int main()
{
    setlocale(0, "");

    // output = 720
    std::wcout << L"il fattoriale di 6 è " << Factorial<6>::value << L'\n';

    return 0;
}
```

Poiché la variabile ```value``` è statica, essa matiene il suo valore tra le diverse chiamate, il compilatore calcola ```value``` con la prima versione della struttura, fino a quando ```N``` non arriva a 0 o 1, in quei casi si utilizza la versione specializzata, che imposta ```value``` a 1.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### La parola chiave ```friend```

</div>

In C++ si dice che una funzione o una classe è amica di un'altra classe se ha accesso alle sue variabili private e protette pur trovandosi all'esterno di quest'ultima.

Esempio:

```cpp
#include <iostream>

class MyClass
{
private: int SecretValue;
public:
    MyClass(int value) : SecretValue(value) {}

    friend void  ShowSecret(const MyClass& obj);
    friend class FriendClass;
};

class FriendClass
{
public:
    void IncrSecret(MyClass& obj) const { obj.SecretValue++; }
    void DecrSecret(MyClass& obj) const { obj.SecretValue--; }
};

void ShowSecret(const MyClass& obj)
{
    setlocale(0, "");
    std::wcout << L"valore segreto: " << obj.SecretValue << L'\n';
}

int main()
{
    MyClass Object(40);
    FriendClass Friend;

    ShowSecret(Object);
    Friend.IncrSecret(Object);
    ShowSecret(Object);

    return 0;
}
```

In questo esempio la classe ```FriendClass``` e la funzione ```ShowSecret``` riescono ad accedere alla variabile privata ```SecretValue``` di ```MyClass``` perché vengono dichiarate **```friend```** nella classe ```MyClass```.

Si può usare la parola chiave ```friend``` per sovraccaricare il comportamento degli operatori di classi esterne con una classe.

Esempio: sovraccaricare l'operatore ```<<``` di ```wcout``` perché possa funzionare con una classe derivata da ```std::vector```.

```cpp
template<class Ty = int>class new_vector : public std::vector<Ty>
{
public: using std::vector<Ty>::vector;

    friend std::wostream& operator<<(
        std::wostream& os,
        const new_vector& vect
        )
    {
        os << L"{";
        for (size_t i = 0; i < vect.size(); ++i)
        {
            os << vect[i];
            if (i < vect.size() - 1) os << L", ";
        }
        os << L"}";
        return os;
    }
};

int main()
{
    setlocale(0, "");
    new_vector<>  vec{ 1, 2, 3 };
    std::wcout << vec << L'\n';  // output: {1, 2, 3}
    return 0;
}
```

Ecco un altro esempio: sovraccaricare l'operatore ```+=``` di ```std::wstring``` perché funzioni con interi.

```cpp
#include <iostream>
#include <string>

class new_wstring : public std::wstring
{
public: using std::wstring::wstring;

    friend std::wstring& operator+=(
        std::wstring& str,
        const int&  param 
        )
    {
        str += std::to_wstring(param);
        return str;
    }
};

int main()
{
    setlocale(0, "");
    new_wstring str = L"123";
    str += 4;
    std::wcout << str << L'\n';  // Output: 1234
    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### I thread

</div>

In C++ un **thread** è un processo, si possono quindi creare più processi per eseguire diversi compiti allo stesso momento.

Si può utilizzare **```std::this_thread::sleep_for```** per fermare l'esecuzione di un thread per una certa durata di tempo, ad esempio:

```cpp
#include <chrono>
#include <thread>

int main()
{
    // aspetta 2 secondi
    std::this_thread::sleep_for(std::chrono::seconds(2));
    return 0;
}
```

<div style="text-align: center;">

#### ***Thread con una funzione***

</div>

Per utilizzare un thread bisogna assegnargli una funzione:

```cpp
#include <iostream>
#include <thread>

void Function()
{
    // il codice della funzione
}

int main()
{
    std::thread Process(Function);          // attiva il thread
    if (Process.joinable()) Process.join(); // aspetta il termine del thread
    return 0;
}
```

Il thread chiamante (quello che esegue l'intero programma) attiva il thread secondario dichiarato con **```std::thread```**, quindi aspetta il suo termine con ```join``` (importante l'utilizzo di ```joinable``` perché altrimenti il programma potrebbe andare in crash), prima di continuare la sua esecuzione.

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***Thread con una lambda***

</div>

Un thread può anche essere attivato senza una funzione, per fare ciò si utilizza una **funzione lambda**:

```cpp
#include <iostream>
#include <thread>

int main()
{
    std::thread Process([]() {
        
        // codice della funzione lambda

        }
    );
    if (Process.joinable()) Process.join();

    return 0;
}
```

<div style="text-align: center;">

#### ***Passare parametri a un thread di una lambda***

</div>

Le lambda possono catturare delle variabili dall'ambiente, se per valore o per riferimento si descrive fra le parentesi quadre:

```cpp
#include <iostream>
#include <thread>

int main()
{
    std::thread Process1([=]() {
        
        // tutte le variabili sono catturate per valore

        }
    );
    if (Process1.joinable()) Process1.join();

    std::thread Process1([&]() {
        
        // tutte le variabili sono catturate per riferimento

        }
    );
    if (Process2.joinable()) Process2.join();

    return 0;
}
```

```cpp
#include <iostream>
#include <thread>

int main()
{
    setlocale(0, "");
    int param1 = 3, param2 = 5;

    std::wcout << L"l'indirizzo del primo parametro è ";
    std::wcout << &param1 << L'\n';
    
    std::wcout << L"l'indirizzo del secondo parametro è ";
    std::wcout << &param2 << L'\n';

    std::thread Process([param1, &param2]() {
        
        std::wcout << L"parametro 1: "           << param1 << L'\n';
        std::wcout << L"parametro 2: "           << param2 << L'\n';

        std::wcout << L"indirizzo parametro 1: " << &param1 << L'\n';
        std::wcout << L"indirizzo parametro 2: " << &param2 << L'\n';

        // l'indirizzo del primo parametro cambia:
        // ne viene eseguita una copia
        // l'indirizzo del secondo parametro rimane lo stesso

        }
    );
    if (Process.joinable()) Process.join();

    return 0;
}
```

<div style="text-align: center;">

#### ***Thread di funzione membro***

</div>

Per eseguire un thread di una funzione membro di una classe bisogna passare anche il puntatore a ```this```, in questo modo:

```cpp
#include <iostream>
#include <thread>

class MyClass
{
public:
    void show() { std::wcout << L"thread in esecuzione\n"; }
    void operator->() { show(); }
};

int main()
{
    setlocale(0, "");
    MyClass obj;

    // passaggio di operatore e puntatore all'oggetto
    std::thread Process1(&MyClass::operator->, &obj);
    if (Process1.joinable()) Process1.join();

    // passaggio di operatore e puntatore all'oggetto
    std::thread Process2(&MyClass::show, &obj);
    if (Process2.joinable()) Process2.join();

    return 0;
}
```

<div style="text-align: center;">

#### ***Passare parametri a un thread di una funzione***

</div>

Se la funzione di un thread ha degli argomenti, è possibile passare questi argomenti direttamente al thread:

```cpp
#include <iostream>
#include <thread>

void funct(int param1, int& param2) {
    std::wcout << L"parametro 1: " << param1 << L'\n';
    std::wcout << L"parametro 2: " << param2 << L'\n';

    std::wcout << L"indirizzo parametro 1: " << &param1 << L'\n';
    std::wcout << L"indirizzo parametro 2: " << &param2 << L'\n';
}

int main()
{
    setlocale(0, "");
    int var1 = 3, var2 = 5;

    std::wcout << L"l'indirizzo del primo parametro è ";
    std::wcout << &var1 << L'\n';

    std::wcout << L"l'indirizzo del secondo parametro è ";
    std::wcout << &var2 << L'\n';

    std::thread Process(funct, var1, std::ref(var2));
    if (Process.joinable()) Process.join();

    return 0;
}
```

Si utilizza **```std::ref```** quando bisogna passare un parametro per riferimento a un thread.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### Classi importanti con i thread

</div>

<div style="text-align: center;">

#### ***```std::mutex```***

</div>

Un **mutex** è una classe utilizzata per prevenire situazioni di **race-condition** tra i thread, dove più di un thread accede a risorse condivise provocando il crash del programma, per gestire un mutex si utilizzano **```std::lock_guard```** e **```std::unique_lock```**.

```cpp
#include <iostream>
#include <mutex>
#include <string>
#include <thread>

std::mutex mtx;

void output(std::wstring& message)
{
    std::lock_guard<std::mutex> lock(mtx);
    std::wcout << message << L'\n';
}

int main()
{
    setlocale(0, "");
    std::thread t1(output, "Thread 1");
    std::thread t2(output, "Thread 2");

    if (t1.joinable()) t1.join();
    if (t2.joinable()) t2.join();
    return 0;
}
```

Utilizzando ```lock_guard``` si crea un mutex e questo viene attivato, questo mette in pausa tutti gli altri thread impendendo loro di accedere a risorse condivise (```wcout```), quando lock_guard viene distrutto, il mutex è rilasciato e gli altri thread continuano la loro esecuzione.

Si può anche untilizzare ```unique_lock```, in questo caso esiste un metodo **```unlock```** per sbloccare il mutex manualmente:

```cpp
    std::mutex mtx;
    std::unique_lock<std::mutex> lock(mtx);
    lock.unlock();
```

I template di ```lock_guard``` e ```unique_lock``` esistono per via di un altro tipo di mutex detto ```shared_mutex```, che consente a più thread di accedere a una risorsa in lettura ma non in scrittura.

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

#### ***```std::condition_variable```***

</div>

Una variabile condizionale è molto utile quando diversi thread devono interagire, vediamo un esempio dove un thread sta aspettando che un altro thread finisca il calcolo prima di procedere:

```cpp
#include <condition_variable>
#include <iostream>
#include <mutex>
#include <thread>

std::mutex mtx;
std::condition_variable cv;
bool ready = false;

// funzione del thread che aspetta
void waiter()
{
    std::unique_lock<std::mutex> lock(mtx);
    cv.wait(lock, []{ return ready; });
    std::wcout << L"Il thread è stato sbloccato\n";
}

// funzione del thread che esegue il calcolo
void worker()
{
    // il calcolo
    std::this_thread::sleep_for(std::chrono::seconds(1));

    {
        std::lock_guard<std::mutex> lock(mtx);
        ready = true;
    }

    // notifica l'altro thread
    cv.notify_one();
}

int main()
{
    setlocale(0, "");
    std::thread t1(waiter);
    std::thread t2(worker);

    if (t1.joinable()) t1.join();
    if (t2.joinable()) t2.join();
    return 0;
}
```

<div style="page-break-after: always;"></div>

In questo codice vengono avviati due thread, il primo viene fermato dalla variabile condizionale, importante l'utilizzo del mutex, il secondo thread esegue un calcolo, poi utilizza un mutex per modificare la variabile globale ```ready```, importante l'uso delle parentesi graffe per rilasciare il mutex, si esegue la notifica, il thread in attesa si sblocca perché ```ready == true```.

Vediamo più nel dettaglio alcuni metodi di ```std::condition_variable```:

+ ```wait```

```cpp
cv.wait(lock);
```

```cpp
cv.wait(lock, [] { return ready; });
```

Il primo metodo aspetta fino a quando non riceve una notifica, mentre il secondo metodo sveglia il thread solo se dopo una notifica ```ready == true```.

+ ```wait_for```  
  aspetta per una durata specifica

```cpp
cv.wait_for(lock, std::chrono::seconds(1), [] { return ready; });
```

+ ```wait_until```  
  attende fino a un punto temporale specifico

```cpp
cv.wait_until(
    lock,
    std::chrono::steady_clock::now() + std::chrono::seconds(1),
    [] { return ready; }
);
```

+ ```notify_one```  
  risveglia un singolo thread in attesa.

```cpp
cv.notify_one();
```

+ ```notify_all```  
  risveglia tutti i thread in attesa.

```cpp
cv.notify_all();
```

<div style="text-align: center;">

#### ***```std::future``` e ```std::promise```***

</div>

```std::promise``` viene utilizzato per impostare un risultato che verrà poi recuperato da ```std::future```, il tutto in un thread separato

```cpp
#include <future>
#include <iostream>
#include <thread>

void setter(std::promise<int> P) { P.set_value(40); }

int main()
{
    setlocale(0, "");

    std::promise<int> P;
    std::future <int> F = P.get_future();

    std::thread thr(setter, std::move(P));
    std::wcout << L"risultato: " << F.get() << L'\n';

    thr.join();
    return 0;
}
```

```std::async``` può essere utilizzato con ```std::future``` per semplificare l'utilizzo:

```cpp
#include <iostream>
#include <future>

int setter() { return 40; }

int main()
{
    setlocale(0, "");
    std::future<int> result = std::async(calculate);
    std::wcout << L"risultato: " << result.get() << L'\n';
    return 0;
}
```

<div style="text-align: center;">

#### ***```std::atomic```***

</div>

Con l'espressione **variabile atomica** si intende una variabile in grado di effettuare **operazioni atomiche**, cioè operazioni sicure anche se la variabile è condivisa (un'alternativa ai mutex).

Questo funziona solo se il datatype è primitivo oppure un typedef\alias di un tipo primitivo.

<div style="page-break-after: always;"></div>

I metodi di ```std::atomic``` includono:

+ ```load```: legge il valore della variabile
+ ```store```: scrive un valore nella variabile
+ ```fetch_add```: incrementa il valore
+ ```fetch_sub```: decrementa il valore

Esempio:

```cpp
#include <atomic>
#include <iostream>

std::atomic_int atomic_num;

int main()
{
    setlocale(0, "");

    atomic_num.store(17);
    atomic_num.fetch_sub(1);
    atomic_num.fetch_add(4);

    std::wcout << atomic_num.load() << L'\n'; // output = 20
    return 0;
}
```

In questo caso viene usato ```std::atomic_int``` al posto di ```std::atomic<int>``` ma è la stessa cosa, questo si può fare anche con ```bool```, ```char```, ```size_t``` e altri tipi primitivi.

---
---

<div style="page-break-after: always;"></div>

<div style="text-align: center;">

### La parallelizzazione del codice

</div>

<div style="text-align: center;">

#### ***Con ```<execution>```***

</div>

In C++ è possibile dividere il lavoro di una porzione di codice fra più thread con le funzioni dell'header **```execution```**, ecco un esempio:

```cpp
#include <algorithm>
#include <execution>
#include <iostream>
#include <vector>

int main()
{
    setlocale(0, "");
    std::vector<int> vect{ 5, 2, 9, 1, 5, 6, 7 };

    std::wcout << L"questo è il vettore: ";
    for (const auto& v : vect) std::wcout << v << L' ';
    std::wcout << L'\n';

    // foreach
    std::for_each(
        std::execution::par_unseq,
        vect.begin(), vect.end() ,
        [](int& n) {
            n *= 2;
        }
    );

    std::wcout << L"vettore modificato: ";
    for (const auto& v : vect) std::wcout << v << L' ';
    std::wcout << L'\n';

    // ordinamento
    std::sort(std::execution::par, vect.begin(), vect.end());

    std::wcout << L"vettore ordinato: ";
    for (const auto& v : vect) std::wcout << v << L' ';
    std::wcout << L'\n';

    return 0;
}
```

La funzione **```std::for_each```** esegue il codice contenuto nella lambda in parallelo, dove ```n``` è un elemento del vettore (questo il motivo del riferimento ```&```), mentre la funzione **```std::sort```** ordina il vettore con un calcolo in parallelo.

<div style="page-break-after: always;"></div>

+ ```std::execution::seq``` esegue il codice in sequenza
+ ```std::execution::par``` esegue il codice in parallelo mantenendo comunque un certo ordine
+ ```std::execution::par_unseq``` esegue il codice in parallelo senza alcun ordine

<div style="text-align: center;">

#### ***Con ```Concurrency```***

</div>

Se invece si intende parallelizzare un semplice ciclo for invece di un foreach si può utilizzare **```Concurrency::parallel_for```**:

```cpp
#include <iostream>
#include <ppl.h>
#include <vector>

int main()
{
    setlocale(0, "");
    std::vector<int> vect(1'000'000);

    Concurrency::parallel_for(
        0, 1'000'000,
        [&](int i) {
            vect[i] = i * 2;
        }
    );

    std::wcout << L"ecco il vettore: ";
    for (const auto& v : vect) std::wcout << v << L' ';
    std::wcout << L'\n';

    return 0;
}
```

---
---

<div style="page-break-after: always;"></div>

<h1 style="text-align: center;"><b>FINE</b></h1>
