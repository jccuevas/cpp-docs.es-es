---
title: Advertencia del compilador (nivel 3) C4191
ms.date: 11/04/2016
f1_keywords:
- C4191
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
ms.openlocfilehash: 817e74d278aa3d91c65ffeb8ab9ac5844041446e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198970"
---
# <a name="compiler-warning-level-3-c4191"></a>Advertencia del compilador (nivel 3) C4191

'operador/operación': conversión no segura de 'tipo de expresión' a 'tipo necesario'

Varias operaciones que comprenden punteros a función no se consideran seguras:

- Los tipos de función con diferentes convenciones de llamada.

- Los tipos de función con diferentes convenciones de devolución.

- Los tipos de valor devuelto o argumento con diferentes tamaños, categorías de tipo o clasificaciones.

- Las longitudes de la lista de argumentos son diferentes (en `__cdecl`, solo en la conversión de una lista más larga a otra más corta, incluso si la más corta es varargs).

- El puntero a los datos (excepto **void** <strong>\*</strong>) se alisa con un puntero a la función.

- Cualquier otra diferencia de tipos que pueda producir un error o una advertencia en `reinterpret_cast`.

Llamar a esta función a través del puntero de resultados, podría provocar el bloqueo del programa.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

El ejemplo siguiente genera la advertencia C4191:

```cpp
// C4191.cpp
// compile with: /W3 /clr
#pragma warning(default: 4191)

void __clrcall f1() { }
void __cdecl   f2() { }

typedef void (__clrcall * fnptr1)();
typedef void (__cdecl   * fnptr2)();

int main() {
   fnptr1 fp1 = static_cast<fnptr1>(&f1);
   fnptr2 fp2 = (fnptr2) &f2;

   fnptr1 fp3 = (fnptr1) &f2;   // C4191
   fnptr2 fp4 = (fnptr2) &f1;   // C4191
};
```
