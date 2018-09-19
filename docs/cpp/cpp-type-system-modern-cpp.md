---
title: Sistema de tipos de C++ (C++ moderno) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63af117df6f53f2b280dc990d58a099441679f44
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060296"
---
# <a name="c-type-system-modern-c"></a>Sistema de tipos de C++ (C++ moderno)

El concepto de *tipo* es muy importante en C++. Cada variable, argumento de función y valor devuelto por una función debe tener un tipo para compilarse. Asimismo, antes de evaluar cada una de las expresiones (incluidos los valores literales), el compilador da implícitamente un tipo a estas expresiones. Algunos ejemplos de tipos **int** que almacena valores integrales, **doble** para almacenar valores de punto flotante (también conocido como *escalares* tipos de datos), o la clase de la biblioteca estándar [std:: basic_string](../standard-library/basic-string-class.md) para almacenar texto. Puede crear su propio tipo definiendo un **clase** o **struct**. El tipo especifica la cantidad de memoria que se asignará para la variable (o el resultado de la expresión), las clases de valores que se pueden almacenar en esa variable, cómo se interpretan estos valores (como patrones de bits) y las operaciones que se pueden realizar en ella. Este artículo contiene información general sobre las principales características del sistema de tipos de C++.

## <a name="terminology"></a>Terminología

**Variable**: el vínculo simbólico nombre de una cantidad de datos para que el nombre se puede utilizar para tener acceso a los datos que hace referencia en el ámbito del código donde se define. En C++, *variable* generalmente se usa para hacer referencia a las instancias de tipos de datos escalares, mientras que las instancias de otros tipos normalmente se denominan *objetos*.

**Objeto**: por simplicidad y coherencia, este artículo usa el término *objeto* para hacer referencia a cualquier instancia de una clase o estructura, y cuando se usa en el sentido general incluye todos los tipos, incluso las variables escalares.

**Tipo POD** (datos antiguos): esta categoría informal de tipos de datos en C++ hace referencia a tipos que son escalares (consulte la sección de tipos fundamentales) o son *clases POD*. Una clase POD no tiene ningún miembro de datos estático que no sea también POD, y no tiene ningún constructor definido por el usuario, ningún destructor definido por el usuario ni ningún operador de asignación definido por el usuario. Además, las clases POD no tienen funciones virtuales, clases base ni ningún miembro de datos no estático privado o protegido. Los tipos POD suelen utilizarse para el intercambio de datos externos, por ejemplo, con un módulo escrito en lenguaje C (que solo tiene tipos POD).

## <a name="specifying-variable-and-function-types"></a>Especificar tipos de variable y función

C++ es un *fuertemente tipadas* lenguaje y también es *tipos estáticos*; cada objeto tiene un tipo y ese tipo nunca cambia (para no confundir con los objetos de datos estáticos).
**Al declarar una variable** en el código, debe especificar explícitamente su tipo, o usar el **automática** palabra clave para indicar al compilador que deduzca el tipo del inicializador.
**Cuando se declara una función** en el código, debe especificar el tipo de cada argumento y su valor devuelto, o **void** si se devuelve ningún valor por la función. La excepción se produce cuando se utilizan plantillas de función, que están permitidas en los argumentos de tipos arbitrarios.

Una vez que se declara por primera vez una variable, no se puede cambiar su tipo. Sin embargo, el valor de la variable o el valor devuelto por una función se puede copiar en otra variable de distinto tipo. Estas operaciones se denominan *las conversiones de tipos*, que a veces son necesarios, pero también son posibles orígenes de datos o pérdidas.

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

A diferencia de algunos lenguajes, C++ no tiene un tipo base universal del que se deriven todos los demás tipos. La implementación del lenguaje de Visual C++ incluye muchas *tipos fundamentales*, también conocida como *tipos integrados*. Esto incluye los tipos numéricos, como **int**, **doble**, **largo**, **bool**, más el **char** y **wchar_t** tipos de caracteres ASCII y UNICODE, respectivamente. Los tipos más fundamentales (excepto **bool**, **doble**, **wchar_t** y tipos relacionados) todos tienen versiones sin signo, que modifican el intervalo de valores que puede almacenar la variable. Por ejemplo, un **int**, que almacena un entero con signo de 32 bits, puede representar un valor entre -2.147.483.648 a 2.147.483.647. Un **int sin signo**, que también se almacena como 32 bits, puede almacenar un valor comprendido entre 0 y 4.294.967.295. El número total de valores posibles en cada caso es el mismo; solo cambia el intervalo.

El compilador reconoce los tipos fundamentales y tiene reglas integradas que rigen las operaciones que se pueden realizar en esos tipos y cómo se pueden convertir en otros tipos fundamentales. Para obtener una lista completa de tipos integrados y su tamaño y los límites numéricos, vea [tipos fundamentales](../cpp/fundamental-types-cpp.md).

En la ilustración siguiente se muestran los tamaños relativos de los tipos integrados:

![Compila el tamaño en bytes de&#45;en tipos](../cpp/media/built-intypesizes.png "integrados inTYpeSizes")

En la tabla siguiente se muestran los tipos fundamentales que se usan con más frecuencia:

|Tipo|Tamaño|Comentario|
|----------|----------|-------------|
|int|4 bytes|Opción predeterminada para los valores enteros.|
|double|8 bytes|Opción predeterminada para los valores de punto flotante.|
|bool|1 byte|Representa valores que pueden ser true o false.|
|char|1 byte|Se utiliza en los caracteres ASCII de cadenas de estilo C antiguas u objetos std::string que nunca tendrán que convertirse a UNICODE.|
|wchar_t|2 bytes|Representa valores de caracteres “anchos” que se pueden codificar en formato UNICODE (UTF-16 en Windows; puede diferir en otros sistemas operativos). Es el tipo de carácter que se utiliza en las cadenas de tipo `std::wstring`.|
|unsigned char|1 byte|C++ no tiene un tipo `byte` integrado.  Utilice un carácter sin signo para representar un valor byte.|
|unsigned int|4 bytes|Opción predeterminada para los marcadores de bits.|
|long long|8 bytes|Representa valores enteros muy grandes.|

## <a name="the-void-type"></a>El tipo void

El **void** tipo es un tipo especial; no se puede declarar una variable de tipo **void**, pero no se puede declarar una variable de tipo `void *` (puntero a **void**), que es a veces es necesario cuando la asignación de memoria (sin tipo) sin procesar. Sin embargo, punteros a **void** son no de seguridad de tipos y su uso en general no es recomendable en C++ moderno. En una declaración de función, un **void** valor devuelto significa que la función no devuelve un valor; se trata de un uso común y aceptable de **void**. Mientras que las funciones de idioma que requiere de C que tienen ningún parámetro declararan **void** en la lista de parámetros, por ejemplo, `fou(void)`, esta práctica no es recomendable en C++ moderno y se debe declarar como `fou()`. Para obtener más información, consulte [las conversiones de tipos y seguridad de tipos](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>Calificador de tipo const

Cualquier tipo integrado o definido por el usuario se puede calificar con la palabra clave const. Además, las funciones miembro pueden ser **const**-completo e incluso **const**-sobrecargado. El valor de un **const** tipo no puede modificarse después de inicializarse.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.

```

El **const** calificador se usa habitualmente en las declaraciones de función y la variable y "exactitud de const" es un concepto importante en C++; básicamente significa usar **const** para garantizar que, en tiempo de compilación que los valores no se modifican involuntariamente. Para obtener más información, consulte [const](../cpp/const-cpp.md).

Un **const** tipo es distinto de su versión no const; por ejemplo, **const int** es un tipo distinto de **int**. Puede usar C++ **const_cast** operador en esas raras ocasiones en las que deba quitar *declaración como constante* desde una variable. Para obtener más información, consulte [las conversiones de tipos y seguridad de tipos](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>Tipos string

En realidad, el lenguaje C++ no tiene ningún tipo de cadena integradas; **char** y **wchar_t** almacenan caracteres individuales: debe declarar una matriz de estos tipos para aproximarse a una cadena, agregando un valor final null (por ejemplo, ASCII `'\0'`) al elemento de matriz más allá del último carácter válido (también denominado una *cadena de estilo C*). En las cadenas de estilo C, era necesario escribir mucho más código o usar funciones de bibliotecas de utilidades de cadena externas. Pero en C++ moderno, tenemos los tipos de biblioteca estándar `std::string` (de 8 bits **char**-escriba las cadenas de caracteres) o `std::wstring` (de 16 bits **wchar_t**: escriba las cadenas de caracteres). Estos contenedores de la biblioteca estándar de C++ pueden considerarse como tipos de cadena nativa porque forman parte de las bibliotecas estándar que se incluyen en cualquier entorno de compilación de C++ compatible. Solo tiene que usar la directiva `#include <string>` para que estos tipos estén disponibles en el programa. (Si usa MFC o ATL, la clase CString también está disponible, pero no forma parte del estándar de C++). En el lenguaje C++ actual, se desaconseja completamente usar matrices de caracteres que terminen con un valor null (las cadenas de estilo C mencionadas previamente).

## <a name="user-defined-types"></a>Tipos definidos por el usuario

Al definir un **clase**, **struct**, **unión**, o **enum**, esa construcción se utiliza en el resto del código como si fuera un tipo fundamental . Esa construcción tiene un tamaño conocido en memoria y se aplican ciertas reglas sobre su uso durante la comprobación en tiempo de compilación y, en tiempo de ejecución, durante la vida útil del programa. Las diferencias principales entre los tipos fundamentales integrados y los tipos definidos por el usuario son las siguientes:

- El compilador no tiene conocimiento integrado de un tipo definido por el usuario. Aprende de tipo de la primera vez que encuentra la definición durante el proceso de compilación.

- El usuario especifica las operaciones que se pueden realizar en el tipo y cómo se puede convertir en otros tipos definiendo (mediante sobrecarga) los operadores adecuados, como los miembros de clase o las funciones que no son miembro. Para obtener más información, consulte [sobrecarga de funciones](function-overloading.md).

- No es necesario que tengan tipos estáticos (la regla establece que el tipo de un objeto nunca cambia). Mediante los mecanismos de *herencia* y *polimorfismo*, una variable declarada como un tipo definido por el usuario de clase (denominada una instancia de objeto de una clase) podría tener un tipo diferente en tiempo de ejecución que en tiempo de compilación. Para obtener más información, vea [Herencia](../cpp/inheritance-cpp.md).

## <a name="pointer-types"></a>Tipos de puntero

Desde las primeras versiones del lenguaje C, C++ sigue permitiendo declarar una variable de un tipo de puntero mediante el declarador especial `*` (asterisco). Un tipo de puntero almacena la dirección de la ubicación en memoria donde se almacena el valor de datos real. En C++ moderno, estos se conocen como *punteros sin formato*y son accesibles en el código a través de los operadores especiales `*` (asterisco) o `->` (guion con mayor-a). Esto se denomina *desreferenciación*, y que utilice dependerá de si se va a desreferenciar un puntero a un valor escalar o un puntero a un miembro de un objeto. Trabajar con tipos de puntero ha sido uno de los aspectos más difíciles y confusos del desarrollo de programación de C y C++. En esta sección se describe algunos hechos y prácticas para ayudar a utilizar punteros sin formato si se desea, pero en C++ moderno, no tiene ya no es necesario (o recomienda) utilizar punteros sin formato para la propiedad del objeto en absoluto, debido a la evolución de la [puntero inteligente](../cpp/smart-pointers-modern-cpp.md) () se describe más al final de esta sección). Todavía resulta útil y seguro utilizar punteros sin formato para inspeccionar objetos, pero si es necesario utilizarlos para la propiedad del objeto, debe hacerse con precaución y debe valorarse cuidadosamente el modo en que los objetos de su propiedad se crean y se destruyen.

Lo primero que debe saber es que, al declarar una variable de puntero sin formato, se asignará solo la memoria necesaria para almacenar una dirección de la ubicación de memoria a la que el puntero hará referencia cuando esté desreferenciado. Asignación de memoria para el propio valor de datos (también denominada *auxiliar*) todavía no está asignada. Es decir, al declarar una variable de puntero sin formato, se crea una variable de la dirección de memoria, no una variable real de los datos. Si se desreferencia una variable de puntero antes de tener la seguridad de que contiene una dirección válida en una memoria auxiliar, se producirá un comportamiento no definido (normalmente un error irrecuperable) en el programa. En el siguiente ejemplo se muestra este tipo de error:

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

En el ejemplo de código corregido se utiliza la memoria local de la pila para crear la memoria auxiliar a la que `pNumber` apunta. Utilizamos un tipo fundamental para simplificar. En la práctica, el almacén de respaldo para los punteros son tipos más a menudo definido por el usuario que están asignados dinámicamente en un área de memoria denominada el *montón* (o *almacén libre*) mediante el uso de un **nuevo** expresión de la palabra clave (en la programación de estilo C, las antiguas `malloc()` se usó la función de biblioteca en tiempo de ejecución de C). Una vez asignados, estas variables normalmente se conocen como objetos, especialmente si se basan en una definición de clase. Memoria asignada con **nueva** debe eliminarse por correspondiente **eliminar** instrucción (o, si ha usado el `malloc()` función para asignarlas, la función de tiempo de ejecución de C `free()`).

Sin embargo, es fácil olvidarse de eliminar una asignada dinámicamente objetos, especialmente cuando el código complejo, lo que provoca un error de recurso denominado un *fuga de memoria*. Por esta razón, el uso de punteros sin formato no es recomendable en el lenguaje C++ actual. Casi siempre es mejor incluir un puntero sin formato en un [puntero inteligente](../cpp/smart-pointers-modern-cpp.md), que liberará automáticamente la memoria cuando se invoque su destructor (cuando el código sale del ámbito del puntero inteligente); mediante el uso de punteros inteligentes, prácticamente elimina toda una clase de errores en los programas de C++. En el ejemplo siguiente, suponga que `MyClass` es un tipo definido por el usuario que tiene un método público `DoSomeWork();`

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

Para obtener más información sobre los punteros inteligentes, consulte [punteros inteligentes](../cpp/smart-pointers-modern-cpp.md).

Para obtener más información sobre las conversiones de puntero, vea [las conversiones de tipos y seguridad de tipos](../cpp/type-conversions-and-type-safety-modern-cpp.md).

Para obtener más información sobre los punteros en general, vea [punteros](../cpp/pointers-cpp.md).

## <a name="windows-data-types"></a>Tipos de datos de Windows

En la programación Win32 clásica de C y C++, la mayoría de las funciones utilizan definiciones de tipos y macros #define (definidas en `windef.h`) específicas de Windows para especificar los tipos de parámetros y los valores devueltos. Estos tipos de datos de Windows son principalmente solo nombres especiales (alias) dados a los tipos integrados de C o C++. Para obtener una lista completa de estas definiciones de tipos y definiciones del preprocesador, vea [tipos de datos de Windows](/windows/desktop/WinProg/windows-data-types). Algunas de estas definiciones de tipos, como HRESULT y LCID, son útiles y significativas. Otras, como INT, no tienen ningún significado especial y son solo alias para los tipos fundamentales de C++. Otros tipos de datos de Windows tienen nombres que se provienen de la época de programación de C y de los procesadores de 16 bits, y no tienen ningún propósito o significado en el hardware y sistemas operativos modernos. También hay tipos de datos especiales asociados con la biblioteca en tiempo de ejecución de Windows, aparece como [tipos de datos base en tiempo de ejecución de Windows](/windows/desktop/WinRT/base-data-types). En el lenguaje C++ actual, la regla general establece una preferencia por los tipos fundamentales de C++, a menos que el tipo de Windows comunique un significado adicional sobre cómo debe interpretarse el valor.

## <a name="more-information"></a>Obtener más información

Para obtener más información sobre el sistema de tipos de C++, vea los temas siguientes.

|||
|-|-|
|[Tipos de valor](../cpp/value-types-modern-cpp.md)|Describe *los tipos de valor* junto con los problemas relacionados con su uso.|
|[Las conversiones de tipos y seguridad de tipos](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Describe problemas de conversión de tipos comunes y muestra cómo evitarlos.|

## <a name="see-also"></a>Vea también

[Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)