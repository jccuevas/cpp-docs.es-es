---
title: Error del compilador C2514 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2514
dev_langs:
- C++
helpviewer_keywords:
- C2514
ms.assetid: 4b7085e5-6714-4261-80b7-bc72e64ab3e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 392c46224078c35df5ae02a88503726b193c87f3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085516"
---
# <a name="compiler-error-c2514"></a>Error del compilador C2514

'class': clase no tiene constructores

La clase, estructura o unión no tiene ningún constructor con una lista de parámetros que coincida con los parámetros que se usa para crear instancias de ella.

Una clase debe declararse completamente antes de que se pueden crear instancias.

El ejemplo siguiente genera C2514:

```
// C2514.cpp
// compile with: /c
class f;

class g {
public:
    g (int x);
};

class fmaker {
   f *func1() {
      return new f(2);   // C2514
   }

   g *func2() {
      return new g(2);   // OK
   }
};
```