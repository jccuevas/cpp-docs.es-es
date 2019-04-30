---
title: Sobrecarga de funciones
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: 6cc432e404a7a66de63cf87f0fe87f0ccdcb5d70
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154287"
---
# <a name="function-overloading"></a>Sobrecarga de funciones

C++ permite especificar más de una función del mismo nombre en el mismo ámbito. Estas funciones se denominan *sobrecargado* funciones. Las funciones sobrecargadas permiten proporcionar una semántica diferente para una función, dependiendo de los tipos y el número de argumentos.

Por ejemplo, un `print` función que toma un `std::string` argumento podría realizar tareas muy diferentes que una que toma un argumento de tipo **doble**. Sobrecarga evita tener que usar nombres como `print_string` o `print_double`. En tiempo de compilación, el compilador elige la sobrecarga que usar según el tipo de argumentos pasados por el llamador.  Si se llama a `print(42.0)`, el `void print(double d)` se invocará la función. Si se llama a `print("hello world")`, el `void print(std::string)` sobrecarga que se va a invocar.

Puede sobrecargar funciones miembro y funciones no miembro. En la tabla siguiente se muestran las partes de una declaración de función que usa C++ para distinguir entre grupos de funciones con el mismo nombre en el mismo ámbito.

### <a name="overloading-considerations"></a>Consideraciones sobre la sobrecarga

|Elemento de declaración de función|¿Se usa para la sobrecarga?|
|----------------------------------|---------------------------|
|Tipo de valor devuelto de la función|No|
|Número de argumentos|Sí|
|Tipo de argumentos|Sí|
|Presencia o ausencia de puntos suspensivos|Sí|
|El uso de **typedef** nombres|No|
|Límites de matriz sin especificar|No|
|**Const** o **volátil**|Sí, cuando se aplica a la función completa|
|[Calificadores de referencia](#ref-qualifiers)|Sí|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo se puede usar la sobrecarga.

```cpp
// function_overloading.cpp
// compile with: /EHsc
#include <iostream>
#include <math.h>
#include <string>

// Prototype three print functions.
int print(std::string s);             // Print a string.
int print(double dvalue);            // Print a double.
int print(double dvalue, int prec);  // Print a double with a
                                     //  given precision.
using namespace std;
int main(int argc, char *argv[])
{
    const double d = 893094.2987;
    if (argc < 2)
    {
        // These calls to print invoke print( char *s ).
        print("This program requires one argument.");
        print("The argument specifies the number of");
        print("digits precision for the second number");
        print("printed.");
        exit(0);
    }

    // Invoke print( double dvalue ).
    print(d);

    // Invoke print( double dvalue, int prec ).
    print(d, atoi(argv[1]));
}

// Print a string.
int print(string s)
{
    cout << s << endl;
    return cout.good();
}

// Print a double in default precision.
int print(double dvalue)
{
    cout << dvalue << endl;
    return cout.good();
}

//  Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.
int print(double dvalue, int prec)
{
    // Use table-lookup for rounding/truncation.
    static const double rgPow10[] = {
        10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1,
        10E0, 10E1,  10E2,  10E3,  10E4, 10E5,  10E6 };
    const int iPowZero = 6;

    // If precision out of range, just print the number.
    if (prec < -6 || prec > 7)
    {
        return print(dvalue);
    }
    // Scale, truncate, then rescale.
    dvalue = floor(dvalue / rgPow10[iPowZero - prec]) *
        rgPow10[iPowZero - prec];
    cout << dvalue << endl;
    return cout.good();
}
```

El código anterior muestra la sobrecarga de la función `print` en el ámbito del archivo.

El argumento predeterminado no se considera parte del tipo de función. Por lo tanto, no se utiliza en la selección de funciones sobrecargadas. Dos funciones que solo difieren en sus argumentos predeterminados se consideran varias definiciones en lugar de funciones sobrecargadas.

No se pueden proporcionar argumentos predeterminados para los operadores sobrecargados.

## <a name="argument-matching"></a>Coincidencia de argumentos

Las funciones sobrecargadas se seleccionan para obtener la mejor coincidencia entre las declaraciones de función del ámbito y los argumentos proporcionados en la llamada de función. Si se encuentra una función adecuada, se llama a esa función. "Adecuada" en este contexto, bien:

- Se encontró una coincidencia exacta.

- Se realizó una conversión trivial.

- Se realizó una promoción de entero.

- Existe una conversión estándar al tipo de argumento deseado.

- Existe una conversión definida por el usuario (un constructor o un operador de conversión) al tipo de argumento deseado.

- Se encontraron argumentos representados por puntos suspensivos.

El compilador crea un conjunto de funciones de candidato para cada argumento. Las funciones de candidato son funciones en las que el argumento real de esa posición se puede convertir al tipo de argumento formal.

Compila un conjunto de “funciones de coincidencia óptima” para cada argumento y la función seleccionada es la intersección de todos los conjuntos. Si la intersección contiene más de una función, la sobrecarga es ambigua y genera un error. La función seleccionada finalmente siempre es una coincidencia mejor que cada una de las demás funciones del grupo para al menos un argumento. Si no hay ningún ganador claro, la llamada de función genera un error.

Considere las siguientes declaraciones (las funciones se marcan como `Variant 1`, `Variant 2` y `Variant 3` para su identificación en la siguiente discusión):

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

Considere la instrucción siguiente:

```cpp
F1 = Add( F2, 23 );
```

La instrucción anterior compila dos conjuntos:

|Conjunto 1: Funciones de candidato cuyo primer argumento de tipo fracción|Conjunto 2: Candidato funciones cuyo segundo argumento se puede convertir al tipo **int**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|Variante 1|Variante 1 (**int** puede convertirse en **largo** mediante una conversión estándar)|
|Variante 3||

Las funciones del conjunto 2 son funciones para el que hay conversiones implícitas de tipo de parámetro real al tipo de parámetro formal, y entre esas funciones, hay una función para el que el "costo" de la conversión del tipo de parámetro real al tipo de parámetro formal es el más pequeño.

La intersección de estos dos conjuntos es Variante 1. Un ejemplo de una llamada de función ambigua es:

```cpp
F1 = Add( 3, 6 );
```

La llamada de función anterior compila los conjuntos siguientes:

|Conjunto 1: Candidato funciones cuyo primer argumento de tipo **int**|Conjunto 2: Funciones de candidato que tienen segundo argumento de tipo **int**|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|Variante 2 (**int** puede convertirse en **largo** mediante una conversión estándar)|Variante 1 (**int** puede convertirse en **largo** mediante una conversión estándar)|

Dado que la intersección de estos dos conjuntos está vacía, el compilador genera un mensaje de error.

Para la coincidencia de argumentos, una función con *n* argumentos predeterminados se trata como *n*funciones de + 1 separadas, cada uno con un número diferente de argumentos.

Los puntos suspensivos (...) actúan como comodín; coinciden con cualquier argumento real. Se puede producir muchos conjuntos ambiguos, si no diseña los conjuntos de funciones sobrecargadas con extremo cuidado.

> [!NOTE]
>  Ambigüedad de funciones sobrecargadas no se puede determinar hasta que se encuentra una llamada de función. En ese momento, se compilan los conjuntos para cada argumento de la llamada de función y se puede determinar si existe una sobrecarga inequívoca. Esto significa que las ambigüedades pueden permanecer en el código hasta que las evoque una llamada de función determinada.

## <a name="argument-type-differences"></a>Diferencias de tipo de argumento

Las funciones sobrecargadas distinguen entre los tipos de los argumentos que toman diferentes inicializadores. Por consiguiente, un argumento de un tipo especificado y una referencia a ese tipo se consideran iguales con el propósito de sobrecarga. Se consideran iguales porque toman los mismos inicializadores. Por ejemplo, `max( double, double )` se considera igual que `max( double &, double & )`. Declarar dos funciones de este tipo produce un error.

Para la misma razón, argumentos de función de un tipo modificado por **const** o **volátil** no reciben un tratamiento diferente que el tipo base para los fines de sobrecarga.

Sin embargo, el mecanismo de sobrecarga de función puede distinguir entre las referencias que están calificadas por **const** y **volátil** y las referencias al tipo base. Hace que el código como el siguiente:

```cpp
// argument_type_differences.cpp
// compile with: /EHsc /W3
// C4521 expected
#include <iostream>

using namespace std;
class Over {
public:
   Over() { cout << "Over default constructor\n"; }
   Over( Over &o ) { cout << "Over&\n"; }
   Over( const Over &co ) { cout << "const Over&\n"; }
   Over( volatile Over &vo ) { cout << "volatile Over&\n"; }
};

int main() {
   Over o1;            // Calls default constructor.
   Over o2( o1 );      // Calls Over( Over& ).
   const Over o3;      // Calls default constructor.
   Over o4( o3 );      // Calls Over( const Over& ).
   volatile Over o5;   // Calls default constructor.
   Over o6( o5 );      // Calls Over( volatile Over& ).
}
```

### <a name="output"></a>Salida

```Output
Over default constructor
Over&
Over default constructor
const Over&
Over default constructor
volatile Over&
```

Punteros a **const** y **volátil** objetos también se consideran diferentes de los punteros al tipo base para los fines de sobrecarga.

## <a name="argument-matching-and-conversions"></a>Coincidencia y conversión de argumentos

Cuando el compilador intenta buscar coincidencias entre argumentos reales y los argumentos de las declaraciones de función, puede proporcionar conversiones estándar o definidas por el usuario para obtener el tipo correcto si no se encuentra ninguna coincidencia exacta. La aplicación de conversiones está sujeta a estas reglas:

- No se tienen en cuenta las secuencias de conversiones que contienen más de una conversión definida por el usuario.

- No se tienen en cuenta las secuencias de conversiones que pueden acortarse quitando las conversiones intermedias.

La secuencia resultante de las conversiones, si existe, se denomina la mejor coincidencia de secuencia. Hay varias maneras de convertir un objeto de tipo **int** escriba **unsigned long** mediante conversiones estándar (se describe en [conversiones estándar](../cpp/standard-conversions.md)):

- Convertir de **int** a **largo** y, a continuación **largo** a **unsigned long**.

- Convertir de **int** a **unsigned long**.

La primera secuencia, aunque logra el objetivo deseado, no es la mejor coincidencia de secuencia, existe una secuencia más corta.

En la tabla siguiente se muestra un grupo de conversiones, denominadas conversiones triviales, que tienen un efecto limitado en la determinación de la secuencia que se considera la mejor coincidencia. Los casos en los que las conversiones triviales influyen en la elección de la secuencia se analizan en la lista que sigue a la tabla.

### <a name="trivial-conversions"></a>Conversiones triviales

|Conversión del tipo|Conversión al tipo|
|-----------------------|---------------------|
|*type-name*|*type-name* **&**|
|*type-name* **&**|*type-name*|
|*type-name* **[ ]**|*type-name* __\*__|
|*type-name* **(** *argument-list* **)**|**(** __\*__ *type-name* **) (** *argument-list* **)**|
|*type-name*|**const** *type-name*|
|*type-name*|**volatile** *type-name*|
|*type-name* __\*__|**const** *type-name* __\*__|
|*type-name* __\*__|**volatile** *type-name* __\*__|

Las conversiones se intentan en la siguiente secuencia:

1. Coincidencia exacta. Una coincidencia exacta entre los tipos con los que se llama a la función y los tipos declarados en el prototipo de función siempre es la mejor coincidencia. Las secuencias de conversiones triviales se clasifican como coincidencias exactas. Sin embargo, las secuencias que no tienen ninguna de estas conversiones se consideran mejores que las secuencias que convierten:

   - De puntero a puntero a **const** (`type` <strong>\*</strong> a **const** `type` <strong>\*</strong> ).

   - De puntero a puntero a **volátil** (`type` <strong>\*</strong> a **volátil** `type` <strong>\*</strong>).

   - De referencia, en referencia a **const** (`type` **&** a **const** `type` **&**).

   - De referencia, en referencia a **volátil** (`type` **&** a **volátil** `type` **&**).

1. Coincidencia mediante promociones. Cualquier secuencia no clasificada como coincidencia exacta que contiene solo las promociones de enteros, conversiones de **float** a **doble**, y conversiones triviales se clasifica como coincidencia mediante promociones. Aunque no es una coincidencia tan buena como cualquier coincidencia exacta, una coincidencia mediante promociones es mejor que una coincidencia mediante conversiones estándar.

1. Coincidencia mediante conversiones estándar. Cualquier secuencia no clasificada como coincidencia exacta o una coincidencia mediante promociones que contenga solo conversiones estándar y conversiones triviales se clasifica como coincidencia mediante conversiones estándar. Dentro de esta categoría, se aplican las reglas siguientes:

   - Conversión de un puntero a una clase derivada, en un puntero a una clase base directa o indirecta es preferible convertir a `void *` o `const void *`.

   - La conversión de un puntero a una clase derivada, a un puntero a una clase base, genera una coincidencia mejor cuanto más cerca esté la clase base de una clase base directa. Supongamos que la jerarquía de clases es tal y como se muestra en la ilustración siguiente.

![Gráfico de las conversiones preferidas](../cpp/media/vc391t1.gif "gráfico de las conversiones preferidas") <br/>
Gráfico que muestra conversiones preferidas

La conversión del tipo `D*` al tipo `C*` es preferible a la conversión del tipo `D*` al tipo `B*`. De forma similar, la conversión del tipo `D*` al tipo `B*` es preferible a la conversión del tipo `D*` al tipo `A*`.

Esta regla se aplica también a las conversiones de referencia. La conversión del tipo `D&` al tipo `C&` es preferible a la conversión del tipo `D&` al tipo `B&`, y así sucesivamente.

Esta regla se aplica también a las conversiones de puntero a miembro. La conversión del tipo `T D::*` al tipo `T C::*` es preferible a la conversión del tipo `T D::*` al tipo `T B::*`, y así sucesivamente, donde `T` es el tipo del miembro.

La regla anterior solo se aplica a lo largo de una ruta de derivación determinada. Considere el gráfico que se muestra en la ilustración siguiente.

![Varios&#45;herencia que muestra conversiones preferidas](../cpp/media/vc391t2.gif "varios&#45;herencia que muestra conversiones preferidas") <br/>
Gráfico de herencia múltiple que muestra conversiones preferidas

La conversión del tipo `C*` al tipo `B*` es preferible a la conversión del tipo `C*` al tipo `A*`. La razón es que están en la misma ruta y `B*` está más cerca. Sin embargo, la conversión de tipo `C*` escriba `D*` no es preferible a la conversión al tipo `A*`; no hay ninguna preferencia porque las conversiones siguen diferentes rutas de acceso.

1. Coincidencia con conversiones definidas por el usuario. Esta secuencia no se puede clasificar como una coincidencia exacta, coincidencia mediante promociones o coincidencia mediante conversiones estándares. La secuencia debe contener solo conversiones definidas por el usuario, conversiones estándar o conversiones triviales para clasificarse como coincidencia con conversiones definidas por el usuario. Una coincidencia con conversiones definidas por el usuario se considera una coincidencia mejor que una coincidencia con puntos suspensivos, pero no tan buena como una coincidencia con conversiones estándar.

1. Coincidencia con puntos suspensivos. La secuencia que coincida con puntos suspensivos en la declaración se clasifica como coincidencia con puntos suspensivos. Se considera a la coincidencia más débil.

Se aplican las conversiones definidas por el usuario si no existe ninguna promoción o conversión integrada. Estas conversiones se seleccionan en función del tipo de argumento que se coteja. Observe el código siguiente:

```cpp
// argument_matching1.cpp
class UDC
{
public:
   operator int()
   {
      return 0;
   }
   operator long();
};

void Print( int i )
{
};

UDC udc;

int main()
{
   Print( udc );
}
```

Las conversiones definidas por el usuario disponibles para la clase `UDC` son de tipo **int** y tipo **largo**. Por consiguiente, el compilador considera las conversiones para el tipo de objeto que se coteja: `UDC`. Una conversión a **int** existe, que está seleccionada.

Durante el proceso de coincidencia de argumentos, las conversiones estándar se pueden aplicar tanto al argumento como al resultado de una conversión definida por el usuario. Por consiguiente, el código siguiente funciona:

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

En el ejemplo anterior, la conversión definida por el usuario, **operador long**, se llama para convertir `udc` escriba **largo**. Si ninguna conversión definida por el usuario escriba **largo** se hubiera definido, la conversión se habría realizado como sigue: Tipo `UDC` habría convertido al tipo **int** mediante la conversión definida por el usuario. A continuación, la conversión estándar del tipo **int** escriba **largo** habría aplicado para que coincida con el argumento en la declaración.

Si las conversiones definidas por el usuario deben coincidir con un argumento, no se usan las conversiones estándar al evaluar a la mejor coincidencia. Incluso si más de una función de candidatos requiere una conversión definida por el usuario, las funciones se consideran iguales. Por ejemplo:

```cpp
// argument_matching2.cpp
// C2668 expected
class UDC1
{
public:
   UDC1( int );  // User-defined conversion from int.
};

class UDC2
{
public:
   UDC2( long ); // User-defined conversion from long.
};

void Func( UDC1 );
void Func( UDC2 );

int main()
{
   Func( 1 );
}
```

Ambas versiones de `Func` requieren una conversión definida por el usuario debe convertir el tipo **int** para el argumento de tipo de clase. Las conversiones posibles son:

- Conversión de tipo **int** escriba `UDC1` (conversión definida por el usuario).

- Conversión de tipo **int** escriba **largo**; a continuación, convertir al tipo `UDC2` (conversión en dos pasos).

Aunque la segunda requiere una conversión estándar y la conversión definida por el usuario, las dos conversiones todavía se consideran iguales.

> [!NOTE]
>  Las conversiones definidas por el usuario se consideran conversión por construcción o conversión por inicialización (función de conversión). Ambos métodos se consideran iguales al considerar la mejor coincidencia.

## <a name="argument-matching-and-the-this-pointer"></a>Coincidencia de argumentos y el puntero this

Funciones miembro de clase se tratan de forma diferente, dependiendo de si se declaran como **estático**. Dado que las funciones no estáticas tienen un argumento implícito que proporciona el **esto** puntero, se consideran las funciones no estáticas tienen un argumento más que las funciones estáticas; en caso contrario, se declaran de forma idéntica.

Estas funciones miembro no estáticas requieren que el implícito **esto** puntero coincide con el tipo de objeto a través del cual la función se llama o, para operadores sobrecargados, requieren que el primer argumento coincide con el objeto en el que el se está aplicando el operador. (Para obtener más información acerca de los operadores sobrecargados, vea [operadores sobrecargados](../cpp/operator-overloading.md).)

A diferencia de otros argumentos en funciones sobrecargadas, no se introducen ningún objeto temporal y se realiza ninguna conversión cuando intenta hacer coincidir la **esto** argumento de puntero.

Cuando el `->` operador de selección de miembro se usa para tener acceso a una función miembro de clase `class_name`, **esto** argumento de puntero tiene un tipo de `class_name * const`. Si los miembros se declaran como **const** o **volátil**, los tipos son `const class_name * const` y `volatile class_name * const`, respectivamente.

El operador de selección de miembro `.` funciona exactamente de la misma manera, salvo que se antepone como prefijo un operador `&` (address-of) implícito al nombre de objeto. En el ejemplo siguiente se muestra cómo funciona:

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

El operando izquierdo de los operadores `->*` y `.*` (puntero a miembro) se trata del mismo modo que los operadores `.` y `->` (selección de miembro) en cuanto a la coincidencia de argumentos.

## <a name="ref-qualifiers"></a> Calificadores de referencia en funciones miembro

Calificadores de referencia hacen posible sobrecargar una función miembro basándose en el objeto señalado por **esto** es un valor r o un valor l.  Esta característica puede usarse para evitar las operaciones de copia innecesarias en escenarios donde se elija no proporcionar acceso de puntero a los datos. Por ejemplo, supongamos la clase `C` inicializa algunos datos en su constructor y devuelve una copia de los datos en función de miembro `get_data()`. Si un objeto de tipo `C` es un valor r que está a punto de destruirse, a continuación, el compilador elige la `get_data() &&` sobrecarga, que mueve los datos en lugar de copiarlo.

```cpp
#include <iostream>
#include <vector>

using namespace std;

class C
{

public:
    C() {/*expensive initialization*/}
    vector<unsigned> get_data() &
    {
        cout << "lvalue\n";
        return _data;
    }
    vector<unsigned> get_data() &&
    {
        cout << "rvalue\n";
        return std::move(_data);
    }

private:
    vector<unsigned> _data;
};

int main()
{
    C c;
    auto v = c.get_data(); // get a copy. prints "lvalue".
    auto v2 = C().get_data(); // get the original. prints "rvalue"
    return 0;
}
```

## <a name="restrictions-on-overloading"></a>Restricciones de la sobrecarga

Varias restricciones rigen un conjunto aceptable de funciones sobrecargadas:

- Dos funciones cualesquiera de un conjunto de funciones sobrecargadas deben tener distintas listas de argumentos.

- Sobrecargar funciones con listas de argumentos de los mismos tipos, sobre la base exclusiva del tipo de valor devuelto, es un error.

     **Específicos de Microsoft**

Se puede sobrecargar **new (operador)** únicamente en la base del tipo de valor devuelto; específicamente, en función del modificador de modelo de memoria especificado.

**FIN de Específicos de Microsoft**

- Las funciones miembro no se puede sobrecargar basándose solo en una sea estática y la otra no estática.

- **TypeDef** declaraciones no definen nuevos tipos; presentan los sinónimos de tipos existentes. No afectan al mecanismo de sobrecarga. Observe el código siguiente:

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   Las dos funciones anteriores tienen listas de argumentos idénticas. `PSTR` es un sinónimo de tipo `char *`. En el ámbito del miembro, este código genera un error.

- Los tipos enumerados son tipos distintos y se pueden utilizar para diferenciar funciones sobrecargadas.

- Los tipos "matriz de" y "puntero a" se consideran idénticos para los fines de distinguir entre funciones sobrecargadas, pero solo para las matrices dimensión individualmente. Por eso estos funciones sobrecargadas entran en conflicto y generar un mensaje de error:

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   Para matrices con varias dimensiones, la segunda y todas las dimensiones sucesivas se consideran parte del tipo. Por consiguiente, se utilizan en la distinción entre funciones sobrecargadas:

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>La sobrecarga, reemplazar y ocultar

Dos declaraciones de función cualquiera con el mismo nombre en el mismo ámbito pueden hacer referencia a la misma función o a dos funciones discretas sobrecargadas. Si las listas de argumentos de las declaraciones contienen argumentos de tipos equivalentes (como se describe en la sección anterior), las declaraciones de función hacen referencia a la misma función. Si no, hacen referencia a dos funciones diferentes que se seleccionan mediante la sobrecarga.

Ámbito de clase se respeta estrictamente; por lo tanto, una función declarada en una clase base no se encuentra en el mismo ámbito que una función declarada en una clase derivada. Si una función en una clase derivada se declara con el mismo nombre que una función virtual en la clase base, la función de la clase derivada *invalida* la función de la clase base. Para obtener más información, consulte [funciones virtuales](../cpp/virtual-functions.md).

Si la función de la clase base no está declarada como 'virtual', a continuación, se dice que la función de la clase derivada *ocultar* lo. Tanto reemplazar y ocultar son distintas de sobrecarga.

Ámbito de bloque se respeta estrictamente; por lo tanto, no es una función declarada en el ámbito de archivo en el mismo ámbito que una función declarado localmente. Si una función declarada localmente tiene el mismo nombre que una función declarada en el ámbito del archivo, la función declarada localmente oculta la función del ámbito del archivo, en lugar de producir una sobrecarga. Por ejemplo:

```cpp
// declaration_matching1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void func( int i )
{
    cout << "Called file-scoped func : " << i << endl;
}

void func( char *sz )
{
   cout << "Called locally declared func : " << sz << endl;
}

int main()
{
   // Declare func local to main.
   extern void func( char *sz );

   func( 3 );   // C2664 Error. func( int ) is hidden.
   func( "s" );
}
```

En el código anterior se muestran dos definiciones de la función `func`. La definición que acepta un argumento de tipo `char *` es local para `main` debido la **extern** instrucción. Por lo tanto, la definición que acepta un argumento de tipo **int** está oculto y la primera llamada a `func` es un error.

Para funciones miembro sobrecargadas, diferentes versiones de la función pueden recibir diferentes privilegios de acceso. Continúan considerándose en el ámbito de la clase envolvente y, por lo tanto, son funciones sobrecargadas. Considere el código siguiente, en el que se sobrecarga la función miembro `Deposit`; una versión es pública y la otra privada.

El propósito de este ejemplo es proporcionar una clase `Account` que requiera una contraseña correcta para realizar depósitos. Se hace mediante el uso de la sobrecarga.

La llamada a `Deposit` en `Account::Deposit` llama a la función de miembro privado. Esta llamada es correcta porque `Account::Deposit` es una función miembro, y tiene acceso a los miembros privados de la clase.

```cpp
// declaration_matching2.cpp
class Account
{
public:
   Account()
   {
   }
   double Deposit( double dAmount, char *szPassword );

private:
   double Deposit( double dAmount )
   {
      return 0.0;
   }
   int Validate( char *szPassword )
   {
      return 0;
   }

};

int main()
{
    // Allocate a new object of type Account.
    Account *pAcct = new Account;

    // Deposit $57.22. Error: calls a private function.
    // pAcct->Deposit( 57.22 );

    // Deposit $57.22 and supply a password. OK: calls a
    //  public function.
    pAcct->Deposit( 52.77, "pswd" );
}

double Account::Deposit( double dAmount, char *szPassword )
{
   if ( Validate( szPassword ) )
      return Deposit( dAmount );
   else
      return 0.0;
}
```

## <a name="see-also"></a>Vea también

[Funciones (C++)](../cpp/functions-cpp.md)