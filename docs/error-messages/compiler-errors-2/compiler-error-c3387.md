---
title: "Compiler Error C3387 | Microsoft Docs"
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
  - "C3387"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3387"
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C3387
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' : \_\_declspec\(dllexport\)\/\_\_declspec\(dllimport\) no se puede aplicar a un miembro de un tipo WinRT o administrado  
  
 Los modificadores `dllimport` y [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` no son válidos en miembros de un tipo de Windows en tiempo de ejecución o administrado.  
  
 El ejemplo siguiente genera el error C3387 y muestra cómo corregirlo:  
  
```  
// C3387a.cpp  
// compile with: /clr /c  
ref class X2 {  
   void __declspec(dllexport) mf() {   // C3387  
   // try the following line instead  
   // void mf() {  
   }  
};  
```