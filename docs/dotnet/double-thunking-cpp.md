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
ms.openlocfilehash: dc36679a9457939bb5fb110219b2ddfbf05c643e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546411"
---
# <a name="double-thunking-c"></a>Doble thunk (C++)

Doble thunk hace referencia a la pérdida de rendimiento que pueden surgir al punto de entrada nativo de la función llama a una llamada de función en un contexto administrado llama función administrada de Visual C++ y donde la ejecución del programa para poder llamar a la función administrada. Este tema describe dónde se produce doble thunk y cómo se puede evitar para mejorar el rendimiento.

## <a name="remarks"></a>Comentarios

De forma predeterminada, cuando se compila con **/CLR**, la definición de una función administrada hace que el compilador genere un punto de entrada administrado y un punto de entrada nativo. Esto permite que la función administrada que se llame desde sitios de llamada nativo y administrado. Sin embargo, cuando existe un punto de entrada nativo, puede ser el punto de entrada para todas las llamadas a la función. Si una función que realiza la llamada está administrada, el punto de entrada nativo, a continuación, llamará a punto de entrada administrado. En efecto, se necesitan dos llamadas para invocar la función (por lo tanto, doble código thunk). Por ejemplo, siempre se llama a funciones virtuales a través de un punto de entrada nativo.

Una resolución consiste en indicar al compilador que no se genere un punto de entrada nativo para una función administrada, que la función solo se llamará desde un contexto administrado, mediante el uso de la [__clrcall](../cpp/clrcall.md) convención de llamada.

De forma similar, si exporta ([dllexport, dllimport](../cpp/dllexport-dllimport.md)) una función administrada, se genera un punto de entrada nativo y cualquier función que se importa y llama a esa función llamará a través del punto de entrada nativo. Para evitar el doble código thunk en esta situación, no utilice la semántica de importación/exportación nativa; basta con hacer referencia a los metadatos a través de `#using` (consulte [#using](../preprocessor/hash-using-directive-cpp.md)).

El compilador se actualizó para reducir el doble código thunk innecesario. Por ejemplo, cualquier función con un tipo administrado en la firma (incluido el tipo de valor devuelto) implícitamente se marcará como `__clrcall`. Para obtener más información sobre la eliminación de doble código thunk, vea [ https://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx ](https://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx).

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

El ejemplo siguiente muestra el doble código thunk. Cuando se compila nativo (sin **/CLR**), la llamada a la función virtual en `main` genera una llamada a `T`de copia de constructor y una llamada al destructor. Se consigue un comportamiento similar de la función virtual se declara con **/CLR** y `__clrcall`. Sin embargo, cuando se acaba de compilar con **/CLR**, la llamada de función genera una llamada al constructor de copias, pero hay otra llamada al constructor de copias debido al código thunk de nativo a administrado.

### <a name="code"></a>Código

```
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

### <a name="sample-output"></a>Resultados del ejemplo

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

El ejemplo anterior muestra la existencia de doble código thunk. En este ejemplo se muestra su efecto. El `for` bucle que llama a la función virtual y el tiempo de ejecución de informes de programa. Se notifica la hora más lenta cuando el programa se compila con **/CLR**. Los tiempos más rápidos se notifican cuando se compila sin **/CLR** o si la función virtual se declara con `__clrcall`.

### <a name="code"></a>Código

```
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

### <a name="sample-output"></a>Resultados del ejemplo

```
4.2 seconds
after calling struct S
```

## <a name="see-also"></a>Vea también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)