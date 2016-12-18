---
title: "Paso de par&#225;metros | Microsoft Docs"
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
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Paso de par&#225;metros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los primeros cuatro argumentos enteros se pasan en registros.  Los valores enteros se pasan \(en el orden de izquierda a derecha\) en RCX, RDX, R8, y R9.  Los argumentos cinco y más alta se pasan en la pila.  Todos los argumentos se justifican a la derecha en registros.  De este modo, el destinatario puede omitir los bits superiores del registro si es necesario y tiene acceso únicamente a la parte del registro que necesita.  
  
 Los argumentos de punto flotante y de precisión doble se pasan en XMM0 a XMM3 \(hasta 4\), con la ranura para enteros \(RCX, RDX, R8 y R9\) que se utilizaría normalmente para que se omitirse la ranura para cardinales \(vea el ejemplo\) y viceversa.  
  
 valor inmediato nunca pasan a tipos, las matrices y las cadenas de [\_\_m128](../cpp/m128.md) pero un puntero se pasa bastante a memoria asignada por el llamador.  Structs\/las uniones, 16, 32 ó 64 de los bits un tamaño de 8, y de \_\_m64 se pasa como si fueran enteros del mismo tamaño.  Structs\/las uniones distinto de estos tamaños se pasa como puntero a la memoria asignada por el llamador.  Para estos tipos agregados pasados como un puntero \(incluso \_\_m128\), la memoria temporal asignada por el llamador tendrá alineación de 16 bytes.  
  
 Las funciones intrínsecas que no asignan espacio de la pila y no llaman a otras funciones pueden usar otros registros variables para pasar argumentos de registro adicionales, ya que hay una estrecha relación entre el compilador y la implementación de la función intrínseca.  Esta es una oportunidad más para mejorar el rendimiento.  
  
 El destinatario tiene la responsabilidad de volcar los parámetros de registro en su espacio central si es necesario.  
  
 La tabla siguiente resume cómo se pasan los parámetros:  
  
|Tipo de parámetro|Cómo se pasa|  
|-----------------------|------------------|  
|Punto flotante|4 primeros parámetros \- XMM0 a XMM3.  Otros se pasan en la pila.|  
|Integer|4 primeros parámetros \- RCX, RDX, R8, R9.  Otros se pasan en la pila.|  
|Agregados \(8, 16, 32 ó 64 bits\) y \_\_m64|4 primeros parámetros \- RCX, RDX, R8, R9.  Otros se pasan en la pila.|  
|Agregados \(otros\)|Mediante puntero.  4 primeros parámetros pasados como punteros en RCX, RDX, R8 y R9|  
|\_\_m128|Mediante puntero.  4 primeros parámetros pasados como punteros en RCX, RDX, R8 y R9|  
  
## Ejemplo de paso de argumentos 1 \- todos los enteros  
  
```  
func1(int a, int b, int c, int d, int e);    
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack  
```  
  
## Ejemplo de paso de argumentos 2 \- todos los flotantes  
  
```  
func2(float a, double b, float c, double d, float e);    
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack  
```  
  
## Ejemplo de paso de argumentos 3 \- enteros y flotantes combinados  
  
```  
func3(int a, double b, int c, float d);    
// a in RCX, b in XMM1, c in R8, d in XMM3  
```  
  
## Ejemplo de paso de argumentos 4 \- \_\_m64, \_\_m128 y agregados  
  
```  
func4(__m64 a, _m128 b, struct c, float d);  
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3  
```  
  
## Vea también  
 [Convención de llamada](../build/calling-convention.md)