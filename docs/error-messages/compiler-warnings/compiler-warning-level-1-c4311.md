---
title: "Advertencia del compilador (nivel 1) C4311 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4311"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4311"
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# Advertencia del compilador (nivel 1) C4311
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable' : truncamiento de puntero de 'tipo' a 'tipo'  
  
 Esta advertencia detecta problemas de truncamiento de puntero de 64 bits.  Por ejemplo, si el código se compila para una arquitectura de 64 bits, el valor de un puntero \(64 bits\) se truncará si se asigna a un `int` \(32 bits\).  Para obtener más información, vea este artículo sobre las [reglas para usar punteros](http://msdn.microsoft.com/library/windows/desktop/aa384242).  
  
 Para obtener información adicional acerca de las causas comunes de advertencia C4311, vea [Errores comunes del compilador](http://msdn.microsoft.com/library/windows/desktop/aa384160).  
  
 En el ejemplo de código siguiente se genera la advertencia C4311 cuando se compila para un destino de 64 bits; a continuación, se muestra cómo corregirlo:  
  
```  
// C4311.cpp  
// compile by using: cl /W1 C4311.cpp  
int main() {  
   void* p = &p;  
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets  
   unsigned long long j = (unsigned long long) p;   // OK  
}  
  
```