---
title: Error del compilador C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: 78f90ee1c44a0d42e529a027b1e7fc90a0da3cdb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738328"
---
# <a name="compiler-error-c3491"></a>Error del compilador C3491

'var': una captura por valor no se puede modificar en una expresión lambda no mutable

Una expresión lambda no mutable no puede modificar el valor de una variable capturada por valor.

### <a name="to-correct-this-error"></a>Para corregir este error

- Declare la expresión lambda con la palabra clave `mutable` , o

- Pase la variable por referencia a la lista de captura de la expresión lambda.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3491 porque el cuerpo de una expresión lambda no mutable modifica la variable de captura `m`:

```cpp
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se resuelve el error C3491 mediante la declaración de la expresión lambda con la palabra clave `mutable` :

```cpp
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
