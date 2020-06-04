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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298719"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Por qué los números de punto flotante pierden precisión

En general, los valores decimales de punto flotante no tienen una representación binaria exacta. Este es un efecto secundario de cómo la CPU representa los datos de punto flotante. Por este motivo, puede experimentar una pérdida de precisión y algunas operaciones de punto flotante pueden producir resultados inesperados.

Este comportamiento es el resultado de una de las siguientes causas:

- La representación binaria del número decimal puede que no sea exacta.

- Hay una falta de coincidencia de tipos entre los números usados (por ejemplo, combinando flotantes y dobles).

Para resolver el comportamiento, la mayoría de los programadores se aseguran de que el valor sea mayor o menor que el necesario, u obtienen y usan una biblioteca de decimales codificados binariamente (BCD) que mantendrá la precisión.

La representación binaria de valores de punto flotante afecta a la precisión y la validez de los cálculos de punto flotante. Microsoft Visual C++ utiliza el [formato de punto flotante de IEEE](ieee-floating-point-representation.md).

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

Para EPSILON, se pueden usar las constantes FLT_EPSILON, que se define para flotante como 1.192092896e-07F, o DBL_EPSILON, que se define para doble como 2.2204460492503131e-016. Se debe incluir float.h para estas constantes. Estas constantes se definen como el número positivo menor x, de manera que x+1,0 no es igual a 1,0. Dado que se trata de un número muy pequeño, debe emplear la tolerancia definida por el usuario para realizar cálculos que impliquen números muy grandes.

## <a name="see-also"></a>Vea también

[Optimizar el código](optimizing-your-code.md)
