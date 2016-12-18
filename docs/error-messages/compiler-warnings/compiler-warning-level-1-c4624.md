---
title: "Advertencia del compilador (nivel 1) C4624 | Microsoft Docs"
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
  - "C4624"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4624"
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4624
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'derived class': el destructor se definió implícitamente como eliminado porque un destructor de clase base es inaccesible o se ha eliminado  
  
 Un destructor no está accesible o se eliminó en una clase base y, por tanto, no se generó para una clase derivada.  Cualquier intento de crear un objeto de este tipo en la pila provocará un error del compilador.  
  
 El ejemplo siguiente genera el error C4624 y muestra cómo corregirlo:  
  
```  
// C4624.cpp  
// compile with: /W1 /c  
class B {  
// Uncomment the following line to fix.  
// public:  
   ~B();  
};  
  
class D : public B {};   // C4624 B's destructor not public  
```