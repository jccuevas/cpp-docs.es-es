---
title: Compilador advertencia (nivel 4) C4208 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4208
dev_langs:
- C++
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ee87ad1d43b20c4d0a72b877b05b1ba4c084a1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064629"
---
# <a name="compiler-warning-level-4-c4208"></a>Advertencia del compilador (nivel 4) C4208

ha utilizado una extensión no estándar: delete [exp]; expresión evaluada pero omitida

Con las extensiones de Microsoft (/Ze), puede eliminar una matriz con un valor entre corchetes con el [delete (operador)](../../cpp/delete-operator-cpp.md). El valor se omite.

```
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

Estos valores no son válidos en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).