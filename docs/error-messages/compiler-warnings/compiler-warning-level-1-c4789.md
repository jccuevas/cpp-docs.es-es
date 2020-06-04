---
title: Advertencia del compilador (nivel 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36278615631d017db1d1c2fc4eecf8c1612892de
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518405"
---
# <a name="compiler-warning-level-1-c4789"></a>Advertencia del compilador (nivel 1) C4789

> se producirá una saturación del búfer '*Identifier*' de tamaño *N* bytes; Se escribirán *M* bytes empezando en el desplazamiento *L*

## <a name="remarks"></a>Notas

**C4789** advierte sobre las saturaciones del búfer cuando se usan funciones específicas de tiempo de ejecución de C (CRT). También puede informar de las discrepancias de tamaño cuando se pasan parámetros o se realizan asignaciones. La advertencia es posible si los tamaños de datos se conocen en tiempo de compilación. Esta advertencia se usa en situaciones en las que puede eludirse la detección de discrepancias de tamaño de datos.

**C4789** advierte cuando se copian datos en un bloque de datos que se sabe que es demasiado pequeño en tiempo de compilación.

La advertencia se produce si la copia utiliza la forma intrínseca de una de estas funciones de CRT:

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

La advertencia también aparece cuando se convierte un parámetro en un tipo de datos mayor y, a continuación, se realiza una asignación de copia de una referencia lvalue.

Visual C++ puede generar esta advertencia para una ruta de acceso de código que nunca se ejecuta. La advertencia se puede deshabilitar temporalmente con `#pragma`, como se muestra en este ejemplo:

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

Esta expresión impide que C++ visual genere la advertencia para ese bloque específico de código. `#pragma warning(push)` conserva el estado antes de que `#pragma warning(disable: 4789)` lo cambie. `#pragma warning(pop)` restaura el estado insertado y quita los efectos de la `#pragma warning(disable:4789)`. Para obtener más información sobre C++ la Directiva de preprocesador `#pragma`, vea directivas pragma y [Warning](../../preprocessor/warning.md) [y la palabra clave __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C4789.

```cpp
// C4789.cpp
// compile with: /Oi /W1 /c
#include <string.h>
#include <stdio.h>

int main()
{
    char a[20];
    strcpy(a, "0000000000000000000000000\n");   // C4789

    char buf2[20];
    memset(buf2, 'a', 21);   // C4789

    char c;
    wchar_t w = 0;
    memcpy(&c, &w, sizeof(wchar_t));
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente también genera el error C4789.

```cpp
// C4789b.cpp
// compile with: /W1 /O2 /c
// processor: x86
short G;

int main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```
