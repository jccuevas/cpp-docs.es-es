---
title: Advertencia del compilador (nivel 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: f552a5d76d1a778cdf72cbe079138f609350ffb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401103"
---
# <a name="compiler-warning-level-4-c4221"></a>Advertencia del compilador (nivel 4) C4221

ha utilizado una extensión no estándar: 'identifier': no se puede inicializar utilizando la dirección de la variable automática

Con las extensiones de Microsoft (/Ze) de forma predeterminada, se puede inicializar un tipo agregado (**matriz**, `struct`, o **unión**) con la dirección de una variable local (automática).

## <a name="example"></a>Ejemplo

```
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

Inicializaciones no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).