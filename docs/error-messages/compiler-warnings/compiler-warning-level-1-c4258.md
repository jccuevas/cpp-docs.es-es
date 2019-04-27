---
title: Advertencia del compilador (nivel 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: a3ce4c81a86920baddfc1b277df0236a96254be4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207401"
---
# <a name="compiler-warning-level-1-c4258"></a>Advertencia del compilador (nivel 1) C4258

'variable': definición de la de bucle se omite; se utiliza la definición del ámbito envolvente"

En [/Ze](../../build/reference/za-ze-disable-language-extensions.md) y [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md), las variables definidas en un [para](../../cpp/for-statement-cpp.md) bucle salen del ámbito después de la **para** termina un bucle. Esta advertencia se produce si se utiliza una variable con el mismo nombre que la variable de bucle, pero definida en el bucle envolvente, de nuevo en el ámbito que contiene el **para** bucle. Por ejemplo:

```
// C4258.cpp
// compile with: /Zc:forScope /W1
int main()
{
   int i;
   {
      for (int i =0; i < 1; i++)
         ;
      i = 20;   // C4258 i (in for loop) has gone out of scope
   }
}
```