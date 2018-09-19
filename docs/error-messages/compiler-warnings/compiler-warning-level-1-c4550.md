---
title: Compilador advertencia (nivel 1) C4550 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4550
dev_langs:
- C++
helpviewer_keywords:
- C4550
ms.assetid: f902b4ed-5f17-48ea-b693-92f4fb8c8054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 926a2bcca82fb76e4fb13450531a9ceb0089c979
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052984"
---
# <a name="compiler-warning-level-1-c4550"></a>Advertencia del compilador (nivel 1) C4550

expresión se evalúa como una función que le falta una lista de argumentos

Un puntero a una función sin referencia falta una lista de argumentos.

## <a name="example"></a>Ejemplo

```
// C4550.cpp
// compile with: /W1
bool f()
{
   return true;
}

typedef bool (*pf_t)();

int main()
{
   pf_t pf = f;
   if (*pf) {}  // C4550
   return 0;
}
```