---
title: "Advertencia del compilador (nivel 1) C4526 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4526"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4526"
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4526
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : una función miembro static no puede reemplazar la función virtual 'función virtual' no se reemplazará; la función virtual se ocultará  
  
 La función miembro estática cumple los criterios necesarios para reemplazar la función virtual, lo que convierte la función miembro en virtual y static.  
  
 El código siguiente genera la advertencia C4526:  
  
```  
// C4526.cpp  
// compile with: /W1 /c  
// C4526 expected  
struct myStruct1 {  
   virtual void __stdcall func( int ) = 0;  
};  
  
struct myStruct2: public myStruct1 {  
   static void __stdcall func( int );  
};  
```  
  
 Las siguientes son posibles soluciones:  
  
-   Si la función debía reemplazar la función virtual de clase base, quite el especificador static.  
  
-   Si la función debía ser una función miembro static, cambie su nombre para que no entre en conflicto con la función virtual de clase base.