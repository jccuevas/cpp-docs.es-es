---
title: Error del compilador C3483 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: decc04f25689b24c560f59a71fd22a9708754352
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091691"
---
# <a name="compiler-error-c3483"></a>Error del compilador C3483

'var' ya forma parte de la lista de capturas lambda

Pasó la misma variable a la lista de capturas de una expresión lambda más de una vez.

### <a name="to-correct-this-error"></a>Para corregir este error

- Quite todas las instancias adicionales de la variable de la lista de capturas.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3483 porque la variable `n` aparece más de una vez en la lista de capturas de la expresión lambda:

```
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)