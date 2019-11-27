---
title: Sistema de tipos de C++
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
ms.openlocfilehash: 1f12f7505438dc995aaf8a045fd903488e9ff092
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246598"
---
# <a name="c-type-system"></a>Sistema de tipos de C++

El concepto de *tipo* es muy importante en C++. Cada variable, argumento de función y valor devuelto por una función debe tener un tipo para compilarse. Asimismo, antes de evaluar cada una de las expresiones (incluidos los valores literales), el compilador da implícitamente un tipo a estas expresiones. Algunos ejemplos de tipos son **int** para almacenar valores enteros, **Double** para almacenar valores de punto flotante (también conocidos como tipos de datos *escalares* ) o la clase [STD:: basic_string](../standard-library/basic-string-class.md) de la biblioteca estándar para almacenar texto. Puede crear su propio tipo definiendo una **clase** o un **struct**. El tipo especifica la cantidad de memoria que se asignará para la variable (o el resultado de la expresión), las clases de valores que se pueden almacenar en esa variable, cómo se interpretan estos valores (como patrones de bits) y las operaciones que se pueden realizar en ella. Este artículo contiene información general sobre las principales características del sistema de tipos de C++.

## <a name="terminology"></a>Terminología

**Variable**: el nombre simbólico de una cantidad de datos para que el nombre se pueda usar para tener acceso a los datos a los que hace referencia a lo largo del ámbito del código en el que se define. En C++, la *variable* se utiliza normalmente para hacer referencia a instancias de tipos de datos escalares, mientras que las instancias de otros tipos normalmente se denominan *objetos*.

**Objeto**: por simplicidad y coherencia, en este artículo se usa el término *objeto* para hacer referencia a cualquier instancia de una clase o estructura y, cuando se usa en el sentido general, incluye todos los tipos, incluso las variables escalares.

**Tipo Pod** (datos antiguos sin formato): esta categoría informal de tipos de C++ datos de hace referencia a los tipos que son escalares (vea la sección de tipos fundamentales) o son *clases Pod*. Una clase POD no tiene ningún miembro de datos estático que no sea también POD, y no tiene ningún constructor definido por el usuario, ningún destructor definido por el usuario ni ningún operador de asignación definido por el usuario. Además, las clases POD no tienen funciones virtuales, clases base ni ningún miembro de datos no estático privado o protegido. Los tipos POD suelen utilizarse para el intercambio de datos externos, por ejemplo, con un módulo escrito en lenguaje C (que solo tiene tipos POD).

## <a name="specifying-variable-and-function-types"></a>Especificar tipos de variable y función

C++es un lenguaje *fuertemente tipado* y también tiene *tipo estático*; cada objeto tiene un tipo y ese tipo nunca cambia (no debe confundirse con los objetos de datos estáticos).
**Al declarar una variable** en el código, debe especificar explícitamente su tipo o utilizar la palabra clave **auto** para indicar al compilador que deduzca el tipo del inicializador.
**Al declarar una función** en el código, debe especificar el tipo de cada argumento y su valor devuelto, o bien **void** si la función no devuelve ningún valor. La excepción se produce cuando se utilizan plantillas de función, que están permitidas en los argumentos de tipos arbitrarios.

Una vez que se declara por primera vez una variable, no se puede cambiar su tipo. Sin embargo, el valor de la variable o el valor devuelto por una función se puede copiar en otra variable de distinto tipo. Estas operaciones se denominan *conversiones de tipo*, que a veces son necesarias, pero también son posibles orígenes de pérdida de datos o incorrectas.

Cuando se declara una variable de tipo POD, se recomienda encarecidamente iniciarla, lo que significa darle un valor inicial. Una variable, hasta que se inicializa, tiene el valor "no utilizado", que se compone de los bits que estaban previamente en esa ubicación de memoria. Este es un aspecto importante de C++ que debe recordarse, sobre todo si anteriormente utilizaba otro lenguaje que controlaba la inicialización sin su intervención. Cuando se declara una variable de un tipo que pertenece una clase que no es POD, el constructor controla la inicialización.

En el ejemplo siguiente se muestran algunas sencillas declaraciones de variable con descripciones de cada una de ellas. En el ejemplo se muestra también cómo el compilador utiliza la información de tipo para permitir o no permitir que posteriormente se realicen ciertas operaciones en la variable.

```cpp
int result = 0;              // Declare and initialize an integer.
double coefficient = 10.8;   // Declare and initialize a floating
                             // point value.
auto name = "Lady G.";       // Declare a variable and let compiler
                             // deduce the type.
auto address;                // error. Compiler cannot deduce a type
                             // without an intializing value.
age = 12;                    // error. Variable declaration must
                             // specify a type or use auto!
result = "Kenny G.";         // error. Can’t assign text to an int.
string result = "zero";      // error. Can’t redefine a variable with
                             // new type.
int maxValue;                // Not recommended! maxValue contains
                             // garbage bits until it is initialized.
```

## <a name="fundamental-built-in-types"></a>Tipos (integrados) fundamentales

A diferencia de algunos lenguajes, C++ no tiene un tipo base universal del que se deriven todos los demás tipos. El lenguaje incluye muchos *tipos fundamentales*, también conocidos como *tipos integrados*. Esto incluye tipos numéricos como **int**, **Double**, **Long**, **bool**, además de los tipos **Char** y **wchar_t** para caracteres ASCII y Unicode, respectivamente. La mayoría de los tipos fundamentales (excepto **bool**, **Double**, **wchar_t** y los tipos relacionados) tienen versiones sin signo, que modifican el intervalo de valores que la variable puede almacenar. Por ejemplo, un **int**, que almacena un entero con signo de 32 bits, puede representar un valor comprendido entre-2.147.483.648 y 2.147.483.647. Un **int sin signo**, que también se almacena como 32 bits, puede almacenar un valor comprendido entre 0 y 4.294.967.295. El número total de valores posibles en cada caso es el mismo; solo cambia el intervalo.

El compilador reconoce los tipos fundamentales y tiene reglas integradas que rigen las operaciones que se pueden realizar en esos tipos y cómo se pueden convertir en otros tipos fundamentales. Para obtener una lista completa de los tipos integrados y sus límites de tamaño y numéricos, vea [tipos fundamentales](../cpp/fundamental-types-cpp.md).

En la ilustración siguiente se muestran los tamaños relativos de los tipos integrados:

![Tamaño en bytes de los&#45;tipos integrados](../cpp/media/built-intypesizes.png "Tamaño en bytes de los&#45;tipos integrados")

En la tabla siguiente se muestran los tipos fundamentales que se usan con más frecuencia:

|Tipo|Tamaño|Comentario|
|----------|----------|-------------|
|int|4 bytes|Opción predeterminada para los valores enteros.|
|double|8 bytes|Opción predeterminada para los valores de punto flotante.|
|bool|1 byte|Representa valores que pueden ser true o false.|
|char|1 byte|Se utiliza en los caracteres ASCII de cadenas de estilo C antiguas u objetos std::string que nunca tendrán que convertirse a UNICODE.|
|wchar_t|2 bytes|Representa valores de caracteres “anchos” que se pueden codificar en formato UNICODE (UTF-16 en Windows; puede diferir en otros sistemas operativos). Es el tipo de carácter que se utiliza en las cadenas de tipo `std::wstring`.|
|unsigned&nbsp;Char|1 byte|C++ no tiene un tipo `byte` integrado.  Utilice un carácter sin signo para representar un valor byte.|
|unsigned int|4 bytes|Opción predeterminada para los marcadores de bits.|
|long long|8 bytes|Representa valores enteros muy grandes.|

## <a name="the-void-type"></a>El tipo void

El tipo **void** es un tipo especial; no se puede declarar una variable de tipo **void**, pero se puede declarar una variable de tipo __void \*__ (puntero a **void**), que a veces es necesario al asignar memoria sin procesar (sin tipo). Sin embargo, los punteros a **void** no tienen seguridad de tipos y, por lo general, no se recomienda C++su uso en moderno. En una declaración de función, un valor devuelto **void** significa que la función no devuelve un valor. se trata de un uso común y aceptable de **void**. Aunque el lenguaje C requería funciones que no tienen ningún parámetro para declarar **void** en la lista de parámetros, por ejemplo, `fou(void)`, esta práctica no se recomienda C++ en moderno y debe declararse `fou()`. Para obtener más información, vea [conversiones de tipos y seguridad de tipos](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>Calificador de tipo const

Cualquier tipo integrado o definido por el usuario se puede calificar con la palabra clave const. Además, las funciones miembro pueden ser **const**-Qualified e incluso **const**-overloadd. El valor de un tipo **const** no se puede modificar una vez inicializado.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.
```

El calificador **const** se usa exhaustivamente en las declaraciones de funciones y variables y la "corrección const" es un concepto C++importante en; esencialmente, significa que se debe usar **const** para garantizar, en tiempo de compilación, que los valores no se modifican de forma involuntaria. Para obtener más información, vea [const](../cpp/const-cpp.md).

Un tipo **const** es distinto de su versión no const; por ejemplo, **const int** es un tipo distinto de **int**. Puede usar el C++ operador de **const_cast** en esas raras ocasiones en las que debe quitar *const-* ABDe una variable. Para obtener más información, vea [conversiones de tipos y seguridad de tipos](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>Tipos string

En realidad, el C++ lenguaje no tiene ningún tipo de cadena integrado; **Char** y **wchar_t** almacenan caracteres individuales: debe declarar una matriz de estos tipos para aproximar una cadena, agregando un valor de terminación null (por ejemplo, ASCII `'\0'`) al elemento de la matriz, uno después del último carácter válido (también denominado *cadena de estilo C*). En las cadenas de estilo C, era necesario escribir mucho más código o usar funciones de bibliotecas de utilidades de cadena externas. Pero en moderno C++, tenemos los tipos de biblioteca estándar `std::string` (para cadenas de caracteres de tipo **Char**de 8 bits) o `std::wstring` (para cadenas de caracteres de tipo **wchar_t**de 16 bits). Estos C++ contenedores de la biblioteca estándar se pueden considerar como tipos de cadenas nativas porque forman parte de las bibliotecas estándar que se incluyen en C++ cualquier entorno de compilación compatible. Solo tiene que usar la directiva `#include <string>` para que estos tipos estén disponibles en el programa. (Si usa MFC o ATL, la clase CString también está disponible, pero no forma parte del C++ estándar). No se recomienda usar matrices de caracteres terminadas en null (las cadenas de estilo C mencionadas previamente) en moderno C++.

## <a name="user-defined-types"></a>Tipos definidos por el usuario

Cuando se define una **clase**, un **struct**, una **Unión**o una **enumeración**, esa construcción se utiliza en el resto del código como si fuera un tipo fundamental. Esa construcción tiene un tamaño conocido en memoria y se aplican ciertas reglas sobre su uso durante la comprobación en tiempo de compilación y, en tiempo de ejecución, durante la vida útil del programa. Las diferencias principales entre los tipos fundamentales integrados y los tipos definidos por el usuario son las siguientes:

- El compilador no tiene conocimiento integrado de un tipo definido por el usuario. Aprende del tipo cuando encuentra por primera vez la definición durante el proceso de compilación.

- El usuario especifica las operaciones que se pueden realizar en el tipo y cómo se puede convertir en otros tipos definiendo (mediante sobrecarga) los operadores adecuados, como los miembros de clase o las funciones que no son miembro. Para obtener más información, vea [sobrecarga de funciones](function-overloading.md) .

## <a name="pointer-types"></a>Tipos de puntero

Desde las primeras versiones del lenguaje C, C++ sigue permitiendo declarar una variable de un tipo de puntero mediante el declarador especial `*` (asterisco). Un tipo de puntero almacena la dirección de la ubicación en memoria donde se almacena el valor de datos real. En moderno C++, estos se conocen como *punteros sin formato*y se tiene acceso a ellos en el código a través de operadores especiales `*` (asterisco) o `->` (guión con mayor que). Esto se denomina *desreferenciar*y el que se usa depende de si se va a desreferenciar un puntero a un valor escalar o un puntero a un miembro de un objeto. Trabajar con tipos de puntero ha sido uno de los aspectos más difíciles y confusos del desarrollo de programación de C y C++. En esta sección se describen algunos hechos y prácticas que ayudan a usar punteros sin formato si se desea, pero en C++ moderno ya no es necesario (o se recomienda) usar punteros sin formato para la propiedad del objeto, debido a la evolución del [puntero inteligente](../cpp/smart-pointers-modern-cpp.md) (que se describe más al final de esta sección). Todavía resulta útil y seguro utilizar punteros sin formato para inspeccionar objetos, pero si es necesario utilizarlos para la propiedad del objeto, debe hacerse con precaución y debe valorarse cuidadosamente el modo en que los objetos de su propiedad se crean y se destruyen.

Lo primero que debe saber es que, al declarar una variable de puntero sin formato, se asignará solo la memoria necesaria para almacenar una dirección de la ubicación de memoria a la que el puntero hará referencia cuando esté desreferenciado. Todavía no se ha asignado la asignación de la memoria para el propio valor de datos (también denominado *memoria auxiliar*). Es decir, al declarar una variable de puntero sin formato, se crea una variable de la dirección de memoria, no una variable real de los datos. Si se desreferencia una variable de puntero antes de tener la seguridad de que contiene una dirección válida en una memoria auxiliar, se producirá un comportamiento no definido (normalmente un error irrecuperable) en el programa. En el siguiente ejemplo se muestra este tipo de error:

```cpp
int* pNumber;       // Declare a pointer-to-int variable.
*pNumber = 10;      // error. Although this may compile, it is
                    // a serious error. We are dereferencing an
                    // uninitialized pointer variable with no
                    // allocated memory to point to.
```

En el ejemplo se desreferencia un tipo de puntero que no tiene ninguna memoria asignada para almacenar los datos enteros reales ni una dirección de memoria válida asignada. El código siguiente corrige esto errores:

```cpp
    int number = 10;          // Declare and initialize a local integer
                              // variable for data backing store.
    int* pNumber = &number;   // Declare and initialize a local integer
                              // pointer variable to a valid memory
                              // address to that backing store.
...
    *pNumber = 41;            // Dereference and store a new value in
                              // the memory pointed to by
                              // pNumber, the integer variable called
                              // "number". Note "number" was changed, not
                              // "pNumber".
```

En el ejemplo de código corregido se utiliza la memoria local de la pila para crear la memoria auxiliar a la que `pNumber` apunta. Utilizamos un tipo fundamental para simplificar. En la práctica, la memoria auxiliar de los punteros son los tipos definidos por el usuario que se asignan dinámicamente en un área de memoria denominada *montón* (o *almacén libre*) mediante el uso de una **nueva** expresión de palabra clave (en programación de estilo c, se usó la antigua función de biblioteca en tiempo de ejecución de c `malloc()`). Una vez asignadas, estas variables se denominan normalmente objetos, sobre todo si se basan en una definición de clase. La memoria que se asigna con **New** debe eliminarse mediante una instrucción **Delete** correspondiente (o, si ha usado la función `malloc()` para asignarla, la función en tiempo de ejecución de C `free()`).

Sin embargo, es fácil olvidarse de eliminar un objeto asignado dinámicamente, especialmente en el código complejo, lo que provoca un error de recurso denominado *pérdida de memoria*. Por esta razón, el uso de punteros sin formato no es recomendable en el lenguaje C++ actual. Casi siempre es mejor ajustar un puntero sin formato en un [puntero inteligente](../cpp/smart-pointers-modern-cpp.md), que libera automáticamente la memoria cuando se invoca su destructor (cuando el código sale del ámbito del puntero inteligente); mediante el uso de punteros inteligentes, se elimina prácticamente una clase completa de C++ errores en los programas. En el ejemplo siguiente, suponga que `MyClass` es un tipo definido por el usuario que tiene un método público `DoSomeWork();`

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

Para obtener más información sobre los punteros inteligentes, vea [punteros inteligentes](../cpp/smart-pointers-modern-cpp.md).

Para obtener más información sobre las conversiones de puntero, vea [conversiones de tipos y seguridad de tipos](../cpp/type-conversions-and-type-safety-modern-cpp.md).

Para obtener más información sobre los punteros en general, vea [punteros](../cpp/pointers-cpp.md).

## <a name="windows-data-types"></a>Tipos de datos de Windows

En la programación Win32 clásica de C y C++, la mayoría de las funciones utilizan definiciones de tipos y macros #define (definidas en `windef.h`) específicas de Windows para especificar los tipos de parámetros y los valores devueltos. Estos tipos de datos de Windows son principalmente nombres especiales (alias) asignados a tiposC++ integrados de C/. Para obtener una lista completa de estas definiciones de tipo y las definiciones de preprocesador, vea [tipos de datos de Windows](/windows/win32/WinProg/windows-data-types). Algunas de estas definiciones de tipos, como HRESULT y LCID, son útiles y significativas. Otras, como INT, no tienen ningún significado especial y son solo alias para los tipos fundamentales de C++. Otros tipos de datos de Windows tienen nombres que se provienen de la época de programación de C y de los procesadores de 16 bits, y no tienen ningún propósito o significado en el hardware y sistemas operativos modernos. También hay tipos de datos especiales asociados a la biblioteca de Windows Runtime, que se enumeran como [Windows Runtime tipos de datos base](/windows/win32/WinRT/base-data-types). En el lenguaje C++ actual, la regla general establece una preferencia por los tipos fundamentales de C++, a menos que el tipo de Windows comunique un significado adicional sobre cómo debe interpretarse el valor.

## <a name="more-information"></a>Más información

Para obtener más información sobre el sistema de tipos de C++, vea los temas siguientes.

|||
|-|-|
|[Tipos de valor](../cpp/value-types-modern-cpp.md)|Describe los *tipos de valor* junto con problemas relacionados con su uso.|
|[Conversiones de tipos y seguridad de tipos](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Describe problemas de conversión de tipos comunes y muestra cómo evitarlos.|

## <a name="see-also"></a>Vea también

[Bienvenido de nuevo aC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
