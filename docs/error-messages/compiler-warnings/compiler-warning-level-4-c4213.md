---
title: Advertencia del compilador (nivel 4) C4213
ms.date: 11/04/2016
f1_keywords:
- C4213
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
ms.openlocfilehash: 8a3697b3bf63ac2a7a1e4e4bd0bf3a626c6bd631
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401155"
---
# <a name="compiler-warning-level-4-c4213"></a>Advertencia del compilador (nivel 4) C4213

extensión no estándar utilizada: convertir en valor l

Con las extensiones de Microsoft (/Ze), puede usar conversiones de tipos en el lado izquierdo de una instrucción de asignación.

## <a name="example"></a>Ejemplo

```
// C4213.c
// compile with: /W4
void *a;
void f()
{
   int   i[3];
   a = &i;
   *(( int * )a )++ = 3;  // C4213
}

int main()
{
}
```

Tales conversiones son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).