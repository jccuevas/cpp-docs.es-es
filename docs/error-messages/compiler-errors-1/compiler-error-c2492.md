---
title: "Error del compilador C2492 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2492"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2492"
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2492
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable' : es posible que los datos 'thread' no tengan una interfaz DLL  
  
 La variable está declarada con el atributo [thread](../../cpp/thread.md) y con la interfaz DLL.  La dirección de la variable `thread` sólo se conoce en tiempo de ejecución, por lo que no puede vincularse a una importación o exportación de DLL.  
  
 El código siguiente genera el error C2492:  
  
```  
// C2492.cpp  
// compile with: /c  
class C {  
public:  
   char   ch;  
};  
  
__declspec(dllexport) __declspec(thread) C c_1;   // C2492  
__declspec(thread) C c_1;   // OK  
```