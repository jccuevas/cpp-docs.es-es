---
title: "Advertencia del compilador (nivel 1) C4286 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4286"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4286"
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4286
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo1' : ha sido detectado por la clase base \('tipo2'\) en la línea 'number'  
  
 El tipo de excepción especificado ya lo controla un controlador anterior.  El tipo de la segunda captura de excepción se deriva del tipo de la primera.  Las excepciones de una clase base capturan también las excepciones de una clase derivada.  
  
## Ejemplo  
  
```  
//C4286.cpp  
// compile with: /W1  
#include <eh.h>  
class C {};  
class D : public  C {};  
int main()  
{  
    try  
    {  
        throw "ooops!";  
    }  
    catch( C ) {}  
    catch( D ) {}  // warning C4286, D is derived from C  
}  
```