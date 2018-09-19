---
title: Error del compilador C3491 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3491
dev_langs:
- C++
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64d7b2e4bd602a53afeba2f77293c31bb28902d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068772"
---
# <a name="compiler-error-c3491"></a>Error del compilador C3491

'var': una captura por valor no se puede modificar en una expresión lambda no mutable

Una expresión lambda no mutable no puede modificar el valor de una variable capturada por valor.

### <a name="to-correct-this-error"></a>Para corregir este error

- Declare la expresión lambda con la palabra clave `mutable` , o

- Pase la variable por referencia a la lista de captura de la expresión lambda.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3491 porque el cuerpo de una expresión lambda no mutable modifica la variable de captura `m`:

```
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se resuelve el error C3491 mediante la declaración de la expresión lambda con la palabra clave `mutable` :

```
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)