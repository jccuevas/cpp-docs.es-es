---
title: Compilador advertencia (nivel 2) C4412 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4412
dev_langs:
- C++
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47659a9ba0469b8ee719dbc686ba611e876d32c1
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704018"
---
# <a name="compiler-warning-level-2-c4412"></a>Advertencia del compilador (nivel 2) C4412

> '*función*': función firma contiene el tipo '*tipo*'; Los objetos de C++ son no es seguro pasar entre código puro y mixto o nativo.

## <a name="remarks"></a>Comentarios

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017. Si tiene código que deba ser puros, se recomienda que se traslade a C#.

El compilador detectó una situación potencialmente inseguro que podría producir un error en tiempo de ejecución: se está realizando una llamada desde un **/CLR: pure** compiland a una función que se importó mediante dllimport y la firma de función contiene un tipo no seguro . Un tipo no es seguro si contiene una función miembro o tiene un miembro de datos que es un tipo no seguro o un direccionamiento indirecto a un tipo no seguro.

Esto no es seguro debido a la diferencia en el valor predeterminado al llamar a las convenciones entre código puro y nativo (o mixto nativo y administrado). Al importar (a través de `dllimport`) una función en un **/CLR: pure** proceso de compilación, asegúrese de que las declaraciones de cada tipo en la firma son idénticas a las de la operación de compilación que exporta la función (tenga especial cuidado al diferencias en las convenciones de llamada implícita).

Una función miembro virtual es especialmente propensa a proporcionar resultados inesperados.  Sin embargo, incluso una función no virtual deberá probarse para asegurarse de que obtiene los resultados correctos. Si estás seguro de que está obteniendo los resultados correctos, puede omitir esta advertencia.

C4412 está desactivada de forma predeterminada. Vea [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) y [dllexport, dllimport](../../cpp/dllexport-dllimport.md) para obtener más información.

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

El valor predeterminado convención de llamada un **/CLR: pure** compilación es diferente de una compilación nativa.  Cuando se incluye, C4412.h `Test` tiene como valor predeterminado `__clrcall`. Si se compila y ejecuta este programa (no utilice **/c**), el programa iniciará una excepción.

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