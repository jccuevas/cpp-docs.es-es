---
title: Clases de almacenamiento (C++)
ms.date: 11/04/2016
f1_keywords:
- thread_local_cpp
- external_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: 31f9ba4e16fa1216db4fb66c7b7faeca333f2c43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520332"
---
# <a name="storage-classes-c"></a>Clases de almacenamiento (C++)

Un *clase de almacenamiento* en el contexto de C++, las declaraciones de variable es un especificador de tipo que rige la ubicación de memoria, la vinculación y la duración de objetos. Un objeto determinado puede tener solo una clase de almacenamiento. Las variables definidas dentro de un bloque tienen almacenamiento automático a menos que especifique lo contrario mediante el **extern**, **estático**, o `thread_local` especificadores. Las variables y objetos automáticos no tienen ninguna vinculación; no son visibles para código fuera del bloque.

**Notas**

1. El [mutable](../cpp/mutable-data-members-cpp.md) palabra clave puede considerarse un especificador de clase de almacenamiento. Sin embargo, solo está disponible en la lista de miembros de una definición de clase.

1. **Visual C++ 2010 y versiones posteriores:** el **automática** palabra clave ya no es un especificador de clase de almacenamiento de C++ y el **registrar** palabra clave está desusada. **Visual Studio 2017 versión 15.7 y versiones posterior:** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): el **registrar** palabra clave se quitará el lenguaje C++.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="in-this-section"></a>En esta sección:

- [static](#static)
- [extern](#extern)
- [thread_local](#thread_local)

## <a name="static"></a> Estático

El **estático** palabra clave puede utilizarse para declarar variables y funciones en el ámbito global, el ámbito de espacio de nombres y ámbito de clase. También se pueden declarar variables estáticas en el ámbito local.

Duración estática significa que el objeto o la variable se asignan cuando se inicia el programa y se desasignan cuando finaliza el programa. Vinculación externa significa que el nombre de la variable puede verse desde fuera del archivo en el que se declara la variable. A la inversa, la vinculación interna significa que el nombre no es visible fuera del archivo en el que se declara la variable. De forma predeterminada, una variable o un objeto que se defina en el espacio de nombres global tiene duración estática y vinculación externa. El **estático** palabra clave puede utilizarse en las situaciones siguientes.

1. Cuando se declara una variable o función en el ámbito de archivo (global o ámbito de espacio de nombres), el **estático** palabra clave especifica que la variable o función tiene vinculación interna. Cuando se declara una variable, la variable tiene duración estática y el compilador la inicializa como 0, a menos que se especifique otro valor.

1. Cuando se declara una variable en una función, el **estático** palabra clave especifica que la variable mantiene su estado entre llamadas a esa función.

1. Cuando se declara un miembro de datos en una declaración de clase, el **estático** palabra clave especifica que una copia del miembro es compartida por todas las instancias de la clase. Un miembro de datos estático se debe definir en el ámbito de archivo. Un miembro de datos integral que se declara como **static const** puede tener un inicializador.

1. Cuando se declara una función miembro en una declaración de clase, el **estático** palabra clave especifica que la función es compartida por todas las instancias de la clase. Una función miembro estática no puede tener acceso a un miembro de instancia porque la función no tiene un modo implícito **esto** puntero. Para tener acceso a un miembro de instancia, declare la función con un parámetro que sea un puntero o referencia de instancia.

1. No puede declarar los miembros de una unión como estáticos. Sin embargo, se debe declarar explícitamente una unión anónima declarada globalmente **estático**.

En este ejemplo se muestra cómo declarar una variable **estático** en una función conserva su estado entre las llamadas a esa función.

```cpp
// static1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void showstat( int curr ) {
   static int nStatic;    // Value of nStatic is retained
                          // between each function call
   nStatic += curr;
   cout << "nStatic is " << nStatic << endl;
}

int main() {
   for ( int i = 0; i < 5; i++ )
      showstat( i );
}
```

```Output
nStatic is 0
nStatic is 1
nStatic is 3
nStatic is 6
nStatic is 10
```

En este ejemplo se muestra el uso de **estático** en una clase.

```cpp
// static2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CMyClass {
public:
   static int m_i;
};

int CMyClass::m_i = 0;
CMyClass myObject1;
CMyClass myObject2;

int main() {
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject1.m_i = 1;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject2.m_i = 2;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   CMyClass::m_i = 3;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;
}
```

```Output
0
0
1
1
2
2
3
3
```

En este ejemplo se muestra una variable local declarada **estático** en una función miembro. La variable estática está disponible para el programa completo; todas las instancias del tipo comparten la misma copia de la variable estática.

```cpp
// static3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
struct C {
   void Test(int value) {
      static int var = 0;
      if (var == value)
         cout << "var == value" << endl;
      else
         cout << "var != value" << endl;

      var = value;
   }
};

int main() {
   C c1;
   C c2;
   c1.Test(100);
   c2.Test(100);
}
```

```Output
var != value
var == value
```

A partir de C ++ 11, se garantiza que la inicialización de la variable local estática sea segura para subprocesos. Esta característica se denomina a veces *mágicas estática*. Sin embargo, en una aplicación con subprocesamiento múltiple todas las asignaciones posteriores deben estar sincronizadas. Se puede deshabilitar la característica de la inicialización estática segura para subprocesos mediante el uso de la [/Zc: threadsafeinit](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) marca para evitar llevar una dependencia en CRT.

## <a name="extern"></a> extern

Los objetos y las variables declaradas como **extern** declarar un objeto que se define en otra unidad de traducción o en un ámbito envolvente como si tuvieran vinculación externa.

Declaración de **const** variables con el **extern** clase de almacenamiento fuerza la variable a tener vinculación externa. Una inicialización de un **extern const** variable se permite en la unidad de traducción de definición. Las inicializaciones en unidades de traducción distintas de la unidad de traducción de la definición generan resultados sin definir. Para obtener más información, consulte [usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)

El [/Zc: externconstexpr](../build/reference/zc-externconstexpr.md) opción del compilador hace que el compilador aplique [vinculación externa]() a las variables declaradas con `extern constexpr`. En versiones anteriores de Visual Studio y de forma predeterminada o si **/Zc:externConstexpr-** se especifica, Visual Studio aplica vinculación interna a **constexpr** aunque se utilicen las variables del **extern** se utiliza la palabra clave. El **/Zc: externconstexpr** opción está disponible a partir de Visual Studio 2017 15.6 de actualización. y está desactivada de forma predeterminada. El /permissive-option no permite/Zc: externconstexpr.

El código siguiente muestra dos **extern** declaraciones, `DefinedElsewhere` (que hace referencia a un nombre definido en una unidad de traducción diferente) y `DefinedHere` (que hace referencia a un nombre definido en un ámbito de inclusión):

```cpp
// external.cpp
// DefinedElsewhere is defined in another translation unit
extern int DefinedElsewhere;
int main() {
   int DefinedHere;
   {
      // refers to DefinedHere in the enclosing scope
      extern int DefinedHere;
   }
}
```

## <a name="thread_local"></a> thread_local (C ++ 11)

Una variable declarada con el especificador `thread_local` solo es accesible en el subproceso en el que se crea. La variable se crea cuando se crea el subproceso y se destruye cuando se destruye el subproceso. Cada subproceso tiene su propia copia de la variable. En Windows, `thread_local` es funcionalmente equivalente a específico de Microsoft [__declspec (thread)](../cpp/thread.md) atributo.

```cpp
thread_local float f = 42.0; // Global namespace. Not implicitly static.

struct S // cannot be applied to type definition
{
    thread_local int i; // Illegal. The member must be static.
    thread_local static char buf[10]; // OK
};

void DoSomething()
{
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;
}
```

Cosas a tener en cuenta sobre el `thread_local` especificador:

- Las variables locales de subproceso inicializadas dinámicamente en archivos DLL no pueden inicializarse correctamente en todos los subprocesos que realiza la llamada. Para obtener más información, consulte el [subproceso](thread.md).

- El `thread_local` especificador puede combinarse con **estático** o **extern**.

- Puede aplicar `thread_local` solo a las declaraciones de datos y las definiciones; `thread_local` no puede usarse en definiciones o declaraciones de función.

- Solo puede especificar `thread_local` en elementos de datos con duración de almacenamiento estática. Esto incluye los objetos de datos globales (tanto **estático** y **extern**), objetos estáticos locales y miembros de datos estáticos de clases. Cualquier variable local declarada `thread_local` es implícitamente estático si no se proporciona ninguna otra clase de almacenamiento; es decir, en el ámbito de bloque `thread_local` es equivalente a `thread_local static`.

- Debe especificar `thread_local` para la declaración y la definición de un objeto local para el subproceso, ya sea que la declaración y la definición se realicen en el mismo archivo o en archivos distintos.

En Windows, `thread_local` es funcionalmente equivalente a [__declspec (Thread)](../cpp/thread.md) , salvo que **__declspec (Thread)** se pueden aplicar a una definición de tipo y es válido en el código de C. Siempre que sea posible, use `thread_local` porque forma parte del estándar de C++ y, por tanto, es más portátil.

##  <a name="register"></a>  registrar

**Visual Studio 2017 versión 15.3 y versiones posterior** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): el **registrar** palabra clave ya no es una clase de almacenamiento compatibles. La palabra clave se mantiene en el estándar para un uso futuro.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Ejemplo: automático frente a la inicialización estática

Una variable o un objeto automático local se inicializa cada vez que el flujo de control alcanza su definición. Una variable o un objeto estático local se inicializa la primera vez que el flujo de control alcanza su definición.

Considere el ejemplo siguiente, que define una clase que registra la inicialización y la destrucción de objetos y, a continuación, define tres objetos, `I1`, `I2` e `I3`:

```cpp
// initialization_of_objects.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>
using namespace std;

// Define a class that logs initializations and destructions.
class InitDemo {
public:
    InitDemo( const char *szWhat );
    ~InitDemo();

private:
    char *szObjName;
    size_t sizeofObjName;
};

// Constructor for class InitDemo
InitDemo::InitDemo( const char *szWhat ) :
    szObjName(NULL), sizeofObjName(0) {
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {
        // Allocate storage for szObjName, then copy
        // initializer szWhat into szObjName, using
        // secured CRT functions.
        sizeofObjName = strlen( szWhat ) + 1;

        szObjName = new char[ sizeofObjName ];
        strcpy_s( szObjName, sizeofObjName, szWhat );

        cout << "Initializing: " << szObjName << "\n";
    }
    else {
        szObjName = 0;
    }
}

// Destructor for InitDemo
InitDemo::~InitDemo() {
    if( szObjName != 0 ) {
        cout << "Destroying: " << szObjName << "\n";
        delete szObjName;
    }
}

// Enter main function
int main() {
    InitDemo I1( "Auto I1" ); {
        cout << "In block.\n";
        InitDemo I2( "Auto I2" );
        static InitDemo I3( "Static I3" );
    }
    cout << "Exited block.\n";
}
```

```Output
Initializing: Auto I1
In block.
Initializing: Auto I2
Initializing: Static I3
Destroying: Auto I2
Exited block.
Destroying: Auto I1
Destroying: Static I3
```

Este ejemplo se muestra cómo y cuándo los objetos `I1`, `I2`, y `I3` se inicializan y cuando se destruyen.

Hay varios puntos a tener en cuenta sobre el programa:

- En primer lugar, `I1` e `I2` se destruyen automáticamente cuando el flujo de control sale del bloque en el que están definidos.

- En segundo lugar, en C++, no es necesario declarar objetos o variables al principio de un bloque. Además, estos objetos se inicializan solo cuando el flujo de control alcanza sus definiciones. (`I2` y `I3` son ejemplos de dichas definiciones). La salida muestra exactamente cuándo se inicializan.

- Por último, las variables locales estáticas como `I3` conservan sus valores mientras dura el programa, pero se destruyen cuando el programa finaliza.

## <a name="see-also"></a>Vea también

[Declaraciones y definiciones](../cpp/declarations-and-definitions-cpp.md)