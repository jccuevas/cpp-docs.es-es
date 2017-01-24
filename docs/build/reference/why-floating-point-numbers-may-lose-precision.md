---
title: "Por qu&#233; los n&#250;meros de punto flotante pierden precisi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DBL_EPSILON (constante)"
  - "números de punto flotante, precisión"
  - "FLT_EPSILON (constante)"
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
caps.latest.revision: 10
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Por qu&#233; los n&#250;meros de punto flotante pierden precisi&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En general, los valores decimales de punto flotante no tienen una representación binaria exacta.  Éste es un efecto secundario derivado de la forma en que la CPU representa los datos de punto flotante.  Por esta razón, estos datos podrían perder precisión y algunas operaciones de punto flotante podrían producir resultados inesperados.  
  
 Este comportamiento es el resultado de una de las causas siguientes:  
  
-   La representación binaria del número decimal puede no ser exacta.  
  
-   Los tipos de los números utilizados no coinciden \(por ejemplo, cuando se mezclan los tipos de datos float y double\).  
  
 Para corregir este comportamiento, la mayoría de los programadores se aseguran de que el valor sea mayor o menor que el necesario, o utilizan una biblioteca en formato Binary Coded Decimal \(BCD\), que mantendrá la precisión.  
  
 La representación binaria de los valores de punto flotante afectan a la precisión y la exactitud de los cálculos de punto flotante.  Microsoft Visual C\+\+ utiliza el [Formato de punto flotante de IEEE](../../build/reference/ieee-floating-point-representation.md).  
  
## Ejemplo  
  
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
  
  **¡No son iguales\!  El valor de c es 2,4679999352 o 2,468000**    
## Comentarios  
 Para EPSILON, puede utilizar la constante FLT\_EPSILON, que se define como 1,192092896e\-07F para datos de tipo float, o la constante DBL\_EPSILON, que se define como 2,2204460492503131e\-016.  Es necesario incluir float.h en estas constantes.  Se definen como el menor número positivo x tal que x\+1,0 no sea igual que 1,0.  Como se trata de un número muy pequeño, debe utilizar la tolerancia definida por el usuario en los cálculos que impliquen el uso de números muy grandes.  
  
## Vea también  
 [Optimizar el código](../../build/reference/optimizing-your-code.md)