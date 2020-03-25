---
title: Advertencia del compilador (nivel 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 601b99eec4625e9b598ece4cbb74d0039ad04bf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161794"
---
# <a name="compiler-warning-level-2-c4412"></a>Advertencia del compilador (nivel 2) C4412

> '*función*': la firma de la función contiene el tipo '*tipo*'; C++ los objetos no son seguros para pasar entre código puro y mixto o nativo.

## <a name="remarks"></a>Observaciones

La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017. Si tiene código que debe ser puro, se recomienda trasladarlo a C#.

El compilador detectó una situación potencialmente no segura que podría dar lugar a un error de tiempo de ejecución: se está realizando una llamada desde una operación de compilación **/clr: Pure** a una función que se importó a través de DllImport y la firma de la función contiene un tipo no seguro. Un tipo no es seguro si contiene una función miembro o tiene un miembro de datos que es un tipo no seguro o un direccionamiento indirecto a un tipo no seguro.

Esto no es seguro debido a la diferencia entre las convenciones de llamada predeterminadas entre código puro y nativo (o nativo y administrado mixto). Al importar (a través de `dllimport`) una función en una operación de compilación **/clr: Pure** , asegúrese de que las declaraciones de cada tipo de la firma sean idénticas a las de la compilación que exporta la función (lo que es especialmente cuidado en las diferencias en las convenciones de llamada implícitas).

Una función miembro virtual es especialmente propensa a proporcionar resultados inesperados.  Sin embargo, incluso se debe probar una función no virtual para asegurarse de que obtiene los resultados correctos. Si está seguro de que obtiene los resultados correctos, puede omitir esta advertencia.

C4412 está desactivado de forma predeterminada. Vea [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) y [dllexport, DllImport](../../cpp/dllexport-dllimport.md) para obtener más información.

Para resolver esta advertencia, quite todas las funciones del tipo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4412.

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

El ejemplo siguiente es un archivo de encabezado que declara dos tipos. El tipo de `Unsafe` no es seguro porque tiene una función miembro.

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

La Convención de llamada predeterminada en una compilación **/clr: Pure** es diferente de una compilación nativa.  Cuando se incluye C4412. h, `Test` tiene como valor predeterminado `__clrcall`. Si compila y ejecuta este programa (no use **/c**), el programa iniciará una excepción.

En el ejemplo siguiente se genera C4412.

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
