---
title: "Valores devueltos (C++) | Microsoft Docs"
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
ms.assetid: 53583524-b337-4228-a9c6-c9bf516babe8
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Valores devueltos (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un valor escalar devuelto que puede caber en 64 bits se devuelve mediante RAX. Esto incluye tipos \_\_m64.  Se devuelven tipos no escalares, incluidos tipos flotantes, dobles y de vector como [\_\_m128](../cpp/m128.md), [\_\_m128i](../cpp/m128i.md), [\_\_m128d](../cpp/m128d.md) en XMM0.  El estado de bits no usados en el valor devuelto en RAX o XMM0 es indefinido.  
  
 Se pueden devolver tipos definidos por el usuario por valor de funciones globales y funciones miembro estáticas.  Para devolverse por valor en RAX, los tipos definidos por el usuario deben tener una longitud de 1, 2, 4, 8, 16, 32 o 64 bits; ningún constructor definido por el usuario, destructor u operador de asignación de copia; ningún miembro de datos no estáticos privado o protegido; ningún miembro de datos no estáticos de tipo de referencia; ninguna clases base; ninguna función virtual; y ningún miembro de datos que tampoco cumpla estos requisitos.  \(Esto es esencialmente la definición de un tipo POD de C\+\+03.  Como la definición cambió en el estándar C\+\+11, no se recomienda usar `std::is_pod` para esta prueba\). De lo contrario, el llamador asume la responsabilidad de asignar memoria y pasar un puntero para el valor devuelto como primer argumento.  Los argumentos subsiguientes se desplazan entonces un argumento a la derecha.  El destinatario debe devolver el mismo puntero en RAX.  
  
 Estos ejemplos muestran cómo se pasan los parámetros y valores devueltos para las funciones con las declaraciones especificadas:  
  
## Ejemplo de resultado de 1 a 64 bits del valor devuelto  
  **\_\_int64 func1\(int a, float b, int c, int d, int e\);**  
**\/\/ El llamador pasa a en RCX, b en XMM1, c en R8, d en R9, e insertado en una pila,**  
**\/\/ el destinatario devuelve el resultado \_\_int64 en RAX.**   
## Ejemplo de resultado de 2 a 128 bits del valor devuelto  
  **\_\_m128 func2\(float a, double b, int c, \_\_m64 d\);**   
**\/\/ El llamador pasa a en XMM0, b en XMM1, c en R8, d en R9,**   
**\/\/ el destinatario devuelve el resultado \_\_m128 en XMM0.**   
## Ejemplo de resultado de 3 al tipo de usuario del valor devuelto por puntero  
  **struct Struct1 {**  
 **int j, k, l;    \/\/ Struct1 supera los 64 bits.  };**  
**Struct1 func3\(int a, double b, int c, float d\);**   
**\/\/ El llamador asigna memoria para el Struct1 devuelto y pasa el puntero en RCX,**   
**\/\/ a en RDX, b en XMM2, c en R9, d insertado en la pila;**   
**\/\/ el destinatario devuelve el puntero al resultado Struct1 en RAX.**    
## Ejemplo de resultado de 4 al tipo de usuario del valor devuelto por valor  
  **struct Struct2 {**  
 **int j, k;    \/\/ Struct2 se ajusta a 64 bits y cumple los requisitos de devolución por valor.  };**  
**Struct2 func4\(int a, double b, int c, float d\);**   
**\/\/ El llamador pasa a en RCX, b en XMM1, c en R8 y d en XMM3;**   
**\/\/ el destinatario devuelve resultados Struct2 por valor en RAX.**    
## Vea también  
 [Convención de llamada](../build/calling-convention.md)