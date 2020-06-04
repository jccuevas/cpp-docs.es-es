---
title: Advertencia del compilador (nivel 4) C4204
ms.date: 11/04/2016
f1_keywords:
- C4204
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
ms.openlocfilehash: 45ed4817dbf2c7ecd63cd0c669d6e1cf768184bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174055"
---
# <a name="compiler-warning-level-4-c4204"></a>Advertencia del compilador (nivel 4) C4204

se ha utilizado una extensión no estándar: inicializador agregado no constante

Con las extensiones de Microsoft (/ZE), puede inicializar tipos agregados (matrices, estructuras, uniones y clases) con valores que no son constantes.

## <a name="example"></a>Ejemplo

```c
// C4204.c
// compile with: /W4
int func1()
{
   return 0;
}
struct S1
{
   int i;
};

int main()
{
   struct S1 s1 = { func1() };   // C4204
   return s1.i;
}
```

Tales inicializaciones no son válidas con compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
