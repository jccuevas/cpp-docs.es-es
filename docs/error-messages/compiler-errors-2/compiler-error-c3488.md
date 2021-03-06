---
title: Error del compilador C3488
ms.date: 11/04/2016
f1_keywords:
- C3488
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
ms.openlocfilehash: 2b69ed4ac8b7e706096d107e9dfaa4447ca1bc79
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738432"
---
# <a name="compiler-error-c3488"></a>Error del compilador C3488

No se permite el uso de 'var' cuando el modo de captura predeterminado es por referencia

Cuando se especifica que el modo de captura predeterminado de una expresión lambda es por referencia, no se puede pasar una variable por referencia a la cláusula capture de dicha expresión.

### <a name="to-correct-this-error"></a>Para corregir este error

- No pase explícitamente la variable a la cláusula de captura.

- No especifique por referencia como el modo de captura predeterminado.

- Especifique por valor como el modo de captura predeterminado.

- Pase la variable por valor a la cláusula de captura. (Esto podría cambiar el comportamiento de la expresión lambda).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el código C3488 porque una referencia a la variable `n` aparece en la cláusula de captura de una expresión lambda cuya modo predeterminado es por referencia:

```cpp
// C3488a.cpp

int main()
{
   int n = 5;
   [&, &n]() { return n; } (); // C3488
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cuatro las posibles resoluciones a C3488:

```cpp
// C3488b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass &n to the capture clause.
   [&]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-reference as the default capture mode.
   [&n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-value as the default capture mode.
   [=, &n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by value to the capture clause.
   [n]() { return n; } ();
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
