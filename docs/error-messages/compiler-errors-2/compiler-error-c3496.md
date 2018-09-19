---
title: Error del compilador C3496 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3496
dev_langs:
- C++
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ec4602e6a0061f5eb750ab29587209a6c97985d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062298"
---
# <a name="compiler-error-c3496"></a>Error del compilador C3496

'this' siempre se captura por valor: se ha omitido '&'

No se puede capturar el `this` puntero por referencia.

### <a name="to-correct-this-error"></a>Para corregir este error

- Capture el puntero `this` por valor.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3496 porque una referencia al puntero `this` aparece en la lista de captura de una expresión lambda:

```
// C3496.cpp
// compile with: /c

class C
{
   void f()
   {
      [&this] {}(); // C3496
   }
};
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)