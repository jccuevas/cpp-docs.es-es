---
title: Doble thunk (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
ms.openlocfilehash: 89cca9ef42910d295cbae8bb677fb51927dbcdd2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545352"
---
# <a name="double-thunking-c"></a>Doble thunk (C++)

Double thunk se refiere a la pérdida de rendimiento que puede experimentar cuando una llamada de función en un contexto administrado C++ llama a una función administrada visual y donde la ejecución del programa llama al punto de entrada nativo de la función para llamar a la función administrada. En este tema se describe dónde se produce double thunk y cómo puede evitarlo para mejorar el rendimiento.

## <a name="remarks"></a>Observaciones

De forma predeterminada, al compilar con **/CLR**, la definición de una función administrada hace que el compilador genere un punto de entrada administrado y un punto de entrada nativo. Esto permite llamar a la función administrada desde sitios de llamadas nativos y administrados. Sin embargo, cuando existe un punto de entrada nativo, puede ser el punto de entrada para todas las llamadas a la función. Si una función de llamada es administrada, el punto de entrada nativo llamará al punto de entrada administrado. En efecto, se necesitan dos llamadas para invocar la función (por lo tanto, thunk doble). Por ejemplo, siempre se llama a las funciones virtuales a través de un punto de entrada nativo.

Una resolución consiste en indicar al compilador que no genere un punto de entrada nativo para una función administrada, que solo se llamará a la función desde un contexto administrado mediante el uso de la Convención de llamada de [__clrcall](../cpp/clrcall.md) .

Del mismo modo, si exporta ([dllexport, DllImport](../cpp/dllexport-dllimport.md)) una función administrada, se genera un punto de entrada nativo y cualquier función que importe y llame a esa función llamará a través del punto de entrada nativo. Para evitar el doble thunk en esta situación, no utilice la semántica de exportación/importación nativa; simplemente haga referencia a los metadatos a través de `#using` (vea [la directiva #using](../preprocessor/hash-using-directive-cpp.md)).

El compilador se ha actualizado para reducir el doble thunk innecesario. Por ejemplo, cualquier función con un tipo administrado en la firma (incluido el tipo de valor devuelto) se marcará implícitamente como `__clrcall`.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el siguiente ejemplo se muestra double thunk. Cuando se compila Native (sin **/CLR**), la llamada a la función virtual en `main` genera una llamada al constructor de copias de `T`y una llamada al destructor. Se consigue un comportamiento similar cuando la función virtual se declara con **/CLR** y `__clrcall`. Sin embargo, cuando se acaba de compilar con **/CLR**, la llamada de función genera una llamada al constructor de copias, pero hay otra llamada al constructor de copias debido al código thunk nativo a administrado.

### <a name="code"></a>Código

```cpp
// double_thunking.cpp
// compile with: /clr
#include <stdio.h>
struct T {
   T() {
      puts(__FUNCSIG__);
   }

   T(const T&) {
      puts(__FUNCSIG__);
   }

   ~T() {
      puts(__FUNCSIG__);
   }

   T& operator=(const T&) {
      puts(__FUNCSIG__);
      return *this;
   }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;

   printf("calling struct S\n");
   pS->f(t);
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>Salida de ejemplo

```
__thiscall T::T(void)
calling struct S
__thiscall T::T(const struct T &)
__thiscall T::T(const struct T &)
__thiscall T::~T(void)
__thiscall T::~T(void)
after calling struct S
__thiscall T::~T(void)
```

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo anterior se mostró la existencia de double thunk. Este ejemplo muestra su efecto. El bucle `for` llama a la función virtual y el programa informa del tiempo de ejecución. La hora más lenta se registra cuando el programa se compila con **/CLR**. Las horas más rápidas se indican al compilar sin **/CLR** o si la función virtual se declara con `__clrcall`.

### <a name="code"></a>Código

```cpp
// double_thunking_2.cpp
// compile with: /clr
#include <time.h>
#include <stdio.h>

#pragma unmanaged
struct T {
   T() {}
   T(const T&) {}
   ~T() {}
   T& operator=(const T&) { return *this; }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;
   clock_t start, finish;
   double  duration;
   start = clock();

   for ( int i = 0 ; i < 1000000 ; i++ )
      pS->f(t);

   finish = clock();
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);
   printf( "%2.1f seconds\n", duration );
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>Salida de ejemplo

```
4.2 seconds
after calling struct S
```

## <a name="see-also"></a>Consulte también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)
