---
title: "Error del compilador C3068 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3068"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3068"
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3068
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : una función 'naked' no puede contener objetos que requerirían desenredo si se produjera una excepción de C\+\+  
  
 El compilador no puedo efectuar el desenredo de la pila en una función [naked](../../cpp/naked-cpp.md) que produjo una excepción porque se creó un objeto temporal en la función y se especificó un control de excepciones de C\+\+ \([\/EHsc](../../build/reference/eh-exception-handling-model.md)\).  
  
 Para resolver este error, realice al menos una de las acciones siguientes:  
  
-   No compile con \/EHsc.  
  
-   No marque la función como `naked`.  
  
-   No cree un objeto temporal en la función.  
  
 Si una función crea un objeto temporal en la pila, si la función produce una excepción y está habilitado el control de excepciones de C\+\+, el compilador limpiará la pila si se produce una excepción.  
  
 Cuando se produce una excepción, el código generado por el compilador, llamado prólogo y epílogo y que no está presente en una función naked, se ejecuta para una función.  
  
## Ejemplo  
 El código siguiente genera el error C3068:  
  
```  
// C3068.cpp  
// compile with: /EHsc  
// processor: x86  
class A {  
public:  
   A(){}  
   ~A(){}  
};  
  
void b(A){}  
  
__declspec(naked) void c() {  
   b(A());   // C3068   
};  
```