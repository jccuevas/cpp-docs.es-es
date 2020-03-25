---
title: Advertencia del compilador (nivel 4) C4213
ms.date: 11/04/2016
f1_keywords:
- C4213
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
ms.openlocfilehash: e462fcc2d0283d2519796127612123f7d792d00e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161300"
---
# <a name="compiler-warning-level-4-c4213"></a>Advertencia del compilador (nivel 4) C4213

se ha utilizado una extensión no estándar: conversión en valor l

Con las extensiones de Microsoft (/ZE) predeterminadas, puede usar conversiones en el lado izquierdo de una instrucción de asignación.

## <a name="example"></a>Ejemplo

```c
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

Tales conversiones no son válidas con compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
