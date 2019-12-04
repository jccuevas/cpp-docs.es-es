---
title: Error del compilador C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: 1d51d4c7873d43a655dc11fa8e0fa297b8a69bff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735949"
---
# <a name="compiler-error-c2059"></a>Error del compilador C2059

error de sintaxis: ' token '

El token provocó un error de sintaxis.

En el ejemplo siguiente se genera un mensaje de error para la línea que declara `j`.

```cpp
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

Para determinar la causa del error, examine no solo la línea que aparece en el mensaje de error, sino también las líneas anteriores. Si el examen de las líneas no da ninguna pista sobre el problema, intente comentar la línea que aparece en el mensaje de error y quizás varias líneas por encima.

Si el mensaje de error se produce en un símbolo que sigue inmediatamente a una variable de `typedef`, asegúrese de que la variable se define en el código fuente.

El error C2059 se genera cuando se vuelve a usar un nombre de símbolo de preprocesador como identificador. En el ejemplo siguiente, el compilador ve `DIGITS.ONE` como el número 1, que no es válido como nombre de elemento de enumeración:

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

Puede obtener C2059 si un símbolo se evalúa como Nothing, como puede ocurrir cuando se usa **/d**_Symbol_ **=** para compilar.

```cpp
// C2059a.cpp
// compile with: /DTEST=
#include <stdio.h>

int main() {
   #ifdef TEST
      printf_s("\nTEST defined %d", TEST);   // C2059
   #else
      printf_s("\nTEST not defined");
   #endif
}
```

Otro caso en el que se puede producir el error C2059 es cuando se compila una aplicación que especifica una estructura en los argumentos predeterminados de una función. El valor predeterminado de un argumento debe ser una expresión. Una lista de inicializadores, por ejemplo, una que se usa para inicializar una estructura, no es una expresión.  Para resolver este problema, defina un constructor para realizar la inicialización necesaria.

En el ejemplo siguiente se genera C2059:

```cpp
// C2059b.cpp
// compile with: /c
struct ag_type {
   int a;
   float b;
   // Uncomment the following line to resolve.
   // ag_type(int aa, float bb) : a(aa), b(bb) {}
};

void func(ag_type arg = {5, 7.0});   // C2059
void func(ag_type arg = ag_type(5, 7.0));   // OK
```

El error C2059 puede producirse en una conversión con formato incorrecto.

El ejemplo siguiente genera C2059:

```cpp
// C2059c.cpp
// compile with: /clr
using namespace System;
ref class From {};
ref class To : public From {};

int main() {
   From^ refbase = gcnew To();
   To^ refTo = safe_cast<To^>(From^);   // C2059
   To^ refTo2 = safe_cast<To^>(refbase);   // OK
}
```

El error C2059 también puede producirse si se intenta crear un nombre de espacio de nombres que contenga un punto.

El ejemplo siguiente genera C2059:

```cpp
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

El error C2059 puede producirse cuando un operador que puede calificar un nombre (`::`, `->`y `.`) debe ir seguido de la palabra clave `template`, tal como se muestra en este ejemplo:

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::Rebind<X>::Other AX; // error C2059
};
```

De forma predeterminada C++ , supone que `AY::Rebind` no es una plantilla; por lo tanto, el `<` siguiente se interpreta como un signo menor que.  Debe indicar explícitamente al compilador que `Rebind` es una plantilla para que pueda analizar correctamente el corchete angular. Para corregir este error, use la palabra clave `template` en el nombre del tipo dependiente, como se muestra aquí:

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::template Rebind<X>::Other AX; // correct
};
```
