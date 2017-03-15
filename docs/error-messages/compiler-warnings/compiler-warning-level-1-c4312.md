---
title: "Advertencia del compilador (nivel 1) C4312 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4312"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4312"
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Advertencia del compilador (nivel 1) C4312
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operación' : conversión de 'tipo1' a 'tipo2' de mayor tamaño  
  
 Esta advertencia detecta un intento de asignar un valor de 32 bits a un tipo de puntero de 64 bits, por ejemplo, la conversión de un valor `int` o `long` de 32 bits a un puntero de 64 bits.  
  
 Puede tratarse de una conversión no segura, incluso para los valores de puntero que se ajusten a 32 bits cuando se produce la extensión de signo.  Si un entero negativo de 32 bits se asigna a un tipo de puntero de 64 bits, la extensión de signo provoca que el valor del puntero haga referencia a una dirección de memoria distinta a la del valor del entero.  
  
 Esta advertencia solo se genera para destinos de compilación de 64 bits.  Para obtener más información, vea el tema sobre [reglas para usar punteros](http://msdn.microsoft.com/library/windows/desktop/aa384242).  
  
 El ejemplo de código siguiente genera el error C4312 cuando se compila para destinos de 64 bits:  
  
```  
// C4312.cpp  
// compile by using: cl /W1 /LD C4312.cpp  
void* f(int i) {  
   return (void*)i;   // C4312 for 64-bit targets  
}  
  
void* f2(__int64 i) {  
   return (void*)i;   // OK  
}  
```