---
title: Advertencia del compilador (nivel 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 2c9d50fc3433321c0ca92366a512892212545754
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402442"
---
# <a name="compiler-warning-level-2-c4412"></a>Advertencia del compilador (nivel 2) C4412

> '*función*': función firma contiene el tipo '*tipo*'; Los objetos de C++ son no es seguro pasar entre código puro y mixto o nativo.

## <a name="remarks"></a>Comentarios

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017. Si tiene código que deba ser puros, se recomienda trasladarlo a C#.

El compilador detectó una situación potencialmente insegura que podría provocar un error en tiempo de ejecución: se realiza una llamada desde un **/CLR: pure** compiland a una función que se importó a través de dllimport y la firma de función contiene un tipo no seguro . Un tipo no es seguro si contiene una función miembro o tiene un miembro de datos es un tipo no seguro o un direccionamiento indirecto a un tipo no seguro.

Esto no es seguro debido a la diferencia en la llamada convenciones entre código puro y nativo predeterminada (o mixto nativo y administrado). Al importar (a través de `dllimport`) una función en un **/CLR: pure** proceso de compilación, asegúrese de que las declaraciones de cada tipo en la firma son idénticas a las de la operación de compilación que exporta la función (especial cuidado al diferencias en las convenciones de llamada implícitas).

Una función miembro virtual es especialmente propensa a proporcionar resultados inesperados.  Sin embargo, incluso una función no virtual debe probarse para asegurarse de que obtiene los resultados correctos. Si está seguro de que se obtienen los resultados correctos, puede omitir esta advertencia.

C4412 está desactivada de forma predeterminada. Consulte [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) y [dllexport, dllimport](../../cpp/dllexport-dllimport.md) para obtener más información.

Para resolver esta advertencia, quite todas las funciones del tipo.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4412.

```cpp
// C4412.cpp
// compile with: /c /W2 /clr:pure
#pragma warning (default : 4412)

struct Unsafe {
   virtual void __cdecl Test();
};

struct Safe {
   int i;
};

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   Unsafe *pUnsafe = func();   // C4412
   // pUnsafe->Test();

   Safe *pSafe = func2();   // OK
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente es un archivo de encabezado que declara dos tipos. El `Unsafe` tipo no es seguro porque tiene una función miembro.

```cpp
// C4412.h
struct Unsafe {
   // will be __clrcall if #included in pure compilation
   // defaults to __cdecl in native or mixed mode compilation
   virtual void Test(int * pi);

   // try the following line instead
   // virtual void __cdecl Test(int * pi);
};

struct Safe {
   int i;
};
```

## <a name="example"></a>Ejemplo

Este ejemplo exporta funciones con los tipos definidos en el archivo de encabezado.

```cpp
// C4412_2.cpp
// compile with: /LD
#include "C4412.h"

void Unsafe::Test(int * pi) {
   *pi++;
}

__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }
```

## <a name="example"></a>Ejemplo

El valor predeterminado la convención de llamada un **/CLR: pure** compilación es diferente de una compilación nativa.  Cuando se incluye, C4412.h `Test` el valor predeterminado es `__clrcall`. Si compila y ejecuta este programa (no utilice **/c**), el programa iniciará una excepción.

El ejemplo siguiente genera C4412.

```cpp
// C4412_3.cpp
// compile with: /W2 /clr:pure /c /link C4412_2.lib
#pragma warning (default : 4412)
#include "C4412.h"

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   int n = 7;
   Unsafe *pUnsafe = func();   // C4412
   pUnsafe->Test(&n);

   Safe *pSafe = func2();   // OK
}
```