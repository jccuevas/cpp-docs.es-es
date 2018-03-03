---
title: "¿Por qué los números de punto flotante pierden precisión | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 371aad5dc573a13ca834d8d6d9667a43bb40324e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Por qué los números de punto flotante pierden precisión
Por lo general valores decimales de punto flotante no tiene una representación binaria exacta. Se trata de un efecto secundario de cómo la CPU representa los datos de punto flotante. Por este motivo, puede experimentar una pérdida de precisión y algunas operaciones de punto flotante pueden producir resultados inesperados.  
  
 Este comportamiento es el resultado de uno de los siguientes:  
  
-   La representación binaria del número decimal puede no ser exacta.  
  
-   Hay una discordancia de tipos entre los números utilizados (por ejemplo, combinación float y double).  
  
 Para resolver este comportamiento, los programadores Asegúrese de que el valor es mayor o menor que lo que es necesario, o bien obtengan y utilizar una biblioteca de Binary Coded Decimal (BCD) que mantendrá la precisión.  
  
 Representación binaria de los valores de punto flotante afecta a la precisión y la exactitud de los cálculos de punto flotante. Microsoft Visual C++ utiliza [formato de punto flotante de IEEE](../../build/reference/ieee-floating-point-representation.md).  
  
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
 Para EPSILON, puede utilizar la constante FLT_EPSILON, que se define para float como 1, 192092896e-07F, o la constante DBL_EPSILON, que se define para como 2, 2204460492503131e-016. Debe incluir float.h para estas constantes. Estas constantes se definen como menor positivo número x, de modo que x + 1,0 no es igual a 1,0. Dado que se trata de un número muy pequeño, debe emplear tolerancia definido por el usuario para los cálculos que implican a números muy grandes.  
  
## <a name="see-also"></a>Vea también  
 [Optimizar el código](../../build/reference/optimizing-your-code.md)