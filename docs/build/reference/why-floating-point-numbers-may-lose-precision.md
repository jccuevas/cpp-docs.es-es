---
title: Por qué los números de punto flotante pierden precisión
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 4b001bff2f5327599fc5ad2ecae141976403ec58
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424072"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Por qué los números de punto flotante pierden precisión

Por lo general los valores decimales de punto flotante no tienen una representación binaria exacta. Se trata de un efecto secundario de cómo la CPU representa los datos de punto flotante. Por este motivo, puede experimentar una pérdida de precisión y algunas operaciones de punto flotante pueden producir resultados inesperados.

Este comportamiento es el resultado de una de las siguientes acciones:

- La representación binaria del número decimal puede no ser exacta.

- Hay una discordancia entre los números utilizados (por ejemplo, mezcla float y double).

Para corregir este comportamiento, asegúrese de que el valor es mayor o menor que lo que es necesario, o bien puedan obtengan y usar una biblioteca de Binary Coded Decimal (BCD) que mantendrá la precisión de los programadores.

Representación binaria de los valores de punto flotante afecta a la precisión y la precisión de los cálculos de punto flotante. Microsoft Visual C++ utiliza [formato de punto flotante de IEEE](../../build/reference/ieee-floating-point-representation.md).

## <a name="example"></a>Ejemplo

```
// Floating-point_number_precision.c
// Compile options needed: none. Value of c is printed with a decimal
// point precision of 10 and 6 (printf rounded value by default) to
// show the difference
#include <stdio.h>

#define EPSILON 0.0001   // Define your own tolerance
#define FLOAT_EQ(x,v) (((v - EPSILON) < x) && (x <( v + EPSILON)))

int main() {
   float a, b, c;

   a = 1.345f;
   b = 1.123f;
   c = a + b;
   // if (FLOAT_EQ(c, 2.468)) // Remove comment for correct result
   if (c == 2.468)            // Comment this line for correct result
      printf_s("They are equal.\n");
   else
      printf_s("They are not equal! The value of c is %13.10f "
                "or %f",c,c);
}
```

```Output
They are not equal! The value of c is  2.4679999352 or 2.468000
```

## <a name="comments"></a>Comentarios

Para EPSILON, puede utilizar la constante FLT_EPSILON, que se define para float como 1.192092896e-07F, o DBL_EPSILON, que se define para como 2, 2204460492503131e-016. Debe incluir float.h para estas constantes. Estas constantes se definen como positivo menor el número x, tal que x + 1,0 no es igual a 1,0. Se trata de un número muy pequeño, debería emplear tolerancia definido por el usuario para los cálculos que implican a números muy grandes.

## <a name="see-also"></a>Vea también

[Optimizar el código](../../build/reference/optimizing-your-code.md)
