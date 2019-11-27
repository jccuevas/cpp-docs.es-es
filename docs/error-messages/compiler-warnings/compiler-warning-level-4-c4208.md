---
title: Advertencia del compilador (nivel 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: e15140bd2f0983bde64c89a054fd733d1ab902ac
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541864"
---
# <a name="compiler-warning-level-4-c4208"></a>Advertencia del compilador (nivel 4) C4208

se ha utilizado una extensión no estándar: delete [exp]-exp evaluada pero omitida

Con las extensiones de Microsoft (/ZE), puede eliminar una matriz utilizando un valor entre corchetes con el [operador Delete](../../cpp/delete-operator-cpp.md). Se omite el valor.

```cpp
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

Estos valores no son válidos con compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).