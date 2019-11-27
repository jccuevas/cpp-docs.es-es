---
title: Advertencia del compilador (nivel 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: fa87c240472df2926753781f0f14cbd69752de00
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541924"
---
# <a name="compiler-warning-level-4-c4221"></a>Advertencia del compilador (nivel 4) C4221

se ha utilizado una extensión no estándar: ' Identifier ': no se puede inicializar con la dirección de la variable automática

Con las extensiones predeterminadas de Microsoft (/ZE), puede inicializar un tipo de agregado (**matriz**, `struct`o **Unión**) con la dirección de una variable local (automática).

## <a name="example"></a>Ejemplo

```c
// C4221.c
// compile with: /W4
struct S
{
   int *i;
};

void func()
{
   int j;
   struct S s1 = { &j };   // C4221
}

int main()
{
}
```

Tales inicializaciones no son válidas con compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).