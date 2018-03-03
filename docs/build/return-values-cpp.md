---
title: Valores devueltos (C++) | Documentos de Microsoft
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
ms.assetid: 53583524-b337-4228-a9c6-c9bf516babe8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cdd02ab9c30e641ba7389923062f46dbbed534ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="return-values-c"></a>Valores devueltos (C++)
Un valor escalar devuelto que puede caber en 64 bits se devuelve mediante RAX. Esto incluye tipos __m64. Los tipos no escalares como flotantes, dobles y tipos de vector como [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) se devuelven en XMM0. El estado de bits no usados en el valor devuelto en RAX o XMM0 es indefinido.  
  
 Se pueden devolver tipos definidos por el usuario por valor de funciones globales y funciones miembro estáticas. Para devolverse por valor en RAX, los tipos definidos por el usuario deben tener una longitud de 1, 2, 4, 8, 16, 32 o 64 bits; ningún constructor definido por el usuario, destructor u operador de asignación de copia; ningún miembro de datos no estáticos privado o protegido; ningún miembro de datos no estáticos de tipo de referencia; ninguna clases base; ninguna función virtual; y ningún miembro de datos que tampoco cumpla estos requisitos. (Esto es esencialmente la definición de un tipo POD de C++03. Como la definición cambió en el estándar C++11, no se recomienda usar `std::is_pod` para esta prueba). De lo contrario, el llamador asume la responsabilidad de asignar memoria y pasar un puntero para el valor devuelto como primer argumento. Los argumentos subsiguientes se desplazan entonces un argumento a la derecha. El destinatario debe devolver el mismo puntero en RAX.  
  
 Estos ejemplos muestran cómo se pasan los parámetros y valores devueltos para las funciones con las declaraciones especificadas:  
  
## <a name="example-of-return-value-1---64-bit-result"></a>Ejemplo de resultado de 1 y 64 bits de valor devuelto  
  
```Output  
__int64 func1(int a, float b, int c, int d, int e);  
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,  
// callee returns __int64 result in RAX.  
```  
  
## <a name="example-of-return-value-2---128-bit-result"></a>Ejemplo de resultado de 2 de 128 bits de valor devuelto  
  
```Output  
__m128 func2(float a, double b, int c, __m64 d);   
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,   
// callee returns __m128 result in XMM0.  
```  
  
## <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Ejemplo de valor devuelto 3: resultado de tipo de usuario por puntero  
  
```Output  
struct Struct1 {  
   int j, k, l;    // Struct1 exceeds 64 bits.   
};  
Struct1 func3(int a, double b, int c, float d);   
// Caller allocates memory for Struct1 returned and passes pointer in RCX,   
// a in RDX, b in XMM2, c in R9, d pushed on the stack;   
// callee returns pointer to Struct1 result in RAX.  
```  
  
## <a name="example-of-return-value-4---user-type-result-by-value"></a>Ejemplo de valor devuelto 4 - resultados de tipo de usuario por valor  
  
```Output  
struct Struct2 {  
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.  
};  
Struct2 func4(int a, double b, int c, float d);   
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;   
// callee returns Struct2 result by value in RAX.  
```  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)