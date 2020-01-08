---
title: Por qué los números de punto flotante pierden precisión
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 373ce9fa2c2c96fac349940076873a4a637a9dbe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298719"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Por qué los números de punto flotante pierden precisión

Los valores decimales de punto flotante no suelen tener una representación binaria exacta. Este es un efecto secundario de cómo la CPU representa los datos de punto flotante. Por esta razón, puede experimentar una pérdida de precisión y algunas operaciones de punto flotante pueden producir resultados inesperados.

Este comportamiento es el resultado de uno de los siguientes:

- La representación binaria del número decimal no puede ser exacta.

- Hay una falta de coincidencia de tipos entre los números usados (por ejemplo, mezclando float y Double).

Para resolver el comportamiento, la mayoría de los programadores garantizan que el valor sea mayor o menor que el necesario, o que obtengan y usen una biblioteca binaria codificada decimal (BCD) que mantendrá la precisión.

La representación binaria de valores de punto flotante afecta a la precisión y la precisión de los cálculos de punto flotante. Microsoft Visual C++ usa [el formato de punto flotante de IEEE](ieee-floating-point-representation.md).

## <a name="example"></a>Ejemplo

```c
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

Para épsilon, puede usar las constantes FLT_EPSILON, que se define para Float como 1.192092896 e-07F, o DBL_EPSILON, que se define para Double como 2, 2204460492503131e e-016. Debe incluir float. h para estas constantes. Estas constantes se definen como el número positivo menor x, de modo que x + 1,0 no es igual a 1,0. Dado que se trata de un número muy pequeño, debe emplear la tolerancia definida por el usuario para realizar cálculos que impliquen números muy grandes.

## <a name="see-also"></a>Vea también

[Optimizar el código](optimizing-your-code.md)
