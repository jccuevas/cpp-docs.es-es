---
title: Pasar parámetros | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec0c5b6fe00430c8b08fefdd8781b677004085e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="parameter-passing"></a>Paso de parámetros
Los primeros cuatro argumentos de entero se pasan en registros. Valores enteros se pasan (en orden de izquierda a derecha) en RCX, RDX, R8 y R9. Argumentos de cinco y superior se pasan en la pila. Todos los argumentos son justificado a la derecha en los registros. Esto se hace por lo que el destinatario puede omitir los bits superiores del registro si tienen que ser y puede tener acceso a solo la parte del registro que necesita.  
  
 Argumentos de punto flotante y precisión doble se pasan en XMM0: XMM3 (hasta 4) con la ranura para enteros (RCX, RDX, R8 y R9) que normalmente se utilizarían para esa ranura cardinal que se pasa por alto (vea el ejemplo) y viceversa.  
  
 [__m128](../cpp/m128.md) tipos, matrices y cadenas nunca se pasan por valor inmediato, pero en su lugar se pasa un puntero a la memoria asignada por el llamador. Los structs o uniones de tamaño 8, 16, 32 o 64 bits y __m64 se pasan como si fueran enteros del mismo tamaño. Los structs o uniones de tamaños distintos a estos se pasan como un puntero a la memoria asignada por el llamador. Para estos tipos agregados se pasa como un puntero (incluidos \__m128), la memoria temporal asignada por el llamador será alineada de 16 bytes.  
  
 Funciones intrínsecas que no asignan espacio de pila y no llaman a otras funciones pueden utilizar otros registros variables para pasar argumentos de registro adicionales porque no hay una estrecha relación entre el compilador y la implementación de la función intrínseca. Se trata de una oportunidad adicional para mejorar el rendimiento.  
  
 El destinatario tiene la responsabilidad de volcar los parámetros de registro en su espacio de sombra si es necesario.  
  
 En la tabla siguiente se resume cómo se pasan los parámetros:  
  
|Tipo de parámetro|Cómo se pasa|  
|--------------------|----------------|  
|Punto flotante|4 primeros parámetros - XMM0 a XMM3. Otros se pasan en la pila.|  
|Integer|4 primeros parámetros - RCX, RDX, R8, R9. Otros se pasan en la pila.|  
|Agregados (8, 16, 32 o 64 bits) y __m64|4 primeros parámetros - RCX, RDX, R8, R9. Otros se pasan en la pila.|  
|Agregados (otros)|Por el puntero. 4 primeros parámetros pasados como punteros en RCX, RDX, R8 y R9|  
|__m128|Por el puntero. 4 primeros parámetros pasados como punteros en RCX, RDX, R8 y R9|  
  
## <a name="example-of-argument-passing-1---all-integers"></a>Ejemplo de 1 - todos los enteros de pasar argumentos  
  
```  
func1(int a, int b, int c, int d, int e);    
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-2---all-floats"></a>Ejemplo de paso 2: todos los valores de punto flotante de argumentos  
  
```  
func2(float a, double b, float c, double d, float e);    
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Ejemplo de 3 - enteros y flotantes combinados de pasar argumentos  
  
```  
func3(int a, double b, int c, float d);    
// a in RCX, b in XMM1, c in R8, d in XMM3  
```  
  
## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Ejemplo del argumento de paso 4-__m64, \__m128 y agregados  
  
```  
func4(__m64 a, _m128 b, struct c, float d);  
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3  
```  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)