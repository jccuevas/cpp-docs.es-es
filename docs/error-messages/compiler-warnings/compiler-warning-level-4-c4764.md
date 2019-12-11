---
title: Advertencia del compilador (nivel 4) C4764
ms.date: 11/04/2016
f1_keywords:
- C4764
helpviewer_keywords:
- C4764
ms.assetid: 7bd4296f-966b-484c-bf73-8dbc8e85b4a9
ms.openlocfilehash: 28672d2271e380f6a8240bff98326d5334a0f98f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989185"
---
# <a name="compiler-warning-level-4-c4764"></a>Advertencia del compilador (nivel 4) C4764

No se pueden alinear objetos detectados con elementos mayores de 16 bytes

Se especificó una alineación superior a 16, pero en algunas plataformas, si la función lanza una excepción, la pila forzará una alineación de no más de 16.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4764:

```cpp
// C4764.cpp
// compile with: /W4 /EHsc
// processor: x64 IPF
#include <stdio.h>

class A
{
public:
    int x;
};

typedef __declspec(align(32)) A ALIGNEDA;

int main()
{
    ALIGNEDA a;
    try
    {
        a.x = 15;
        throw a;
    }
    catch (ALIGNEDA b) // can’t align b to > 16 bytes
    {
        printf_s("%d\n", b.x);
    }
}   // C4764
```
