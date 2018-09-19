---
title: Compilador advertencia (nivel 1) C4545 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4545
dev_langs:
- C++
helpviewer_keywords:
- C4545
ms.assetid: 43f8f34f-ed46-4661-95c0-c588c577ff73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d78e80972cdfecc11c94dc7315258fbebd15c787
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046815"
---
# <a name="compiler-warning-level-1-c4545"></a>Advertencia del compilador (nivel 1) C4545

la expresión antes de la coma se evalúa como una función a la que le falta una lista de argumentos

El compilador detectó una expresión de coma mal formada.

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

El ejemplo siguiente genera el error C4545:

```
// C4545.cpp
// compile with: /W1
#pragma warning (default : 4545)

void f() { }

int main()
{
   *(&f), 10;   // C4545
   // try the following line instead
   // (*(&f))(), 10;
}
```