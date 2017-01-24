---
title: "Error del compilador C3902 | Microsoft Docs"
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
  - "C3902"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3902"
ms.assetid: feb3bb29-f836-4d77-ba71-3876f7f4f216
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3902
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'descriptor de acceso': el tipo del último parámetro debe ser 'tipo'  
  
 El tipo del último parámetro de un método set debe coincidir con el tipo de la propiedad.  Para obtener más información, vea [propiedad](../../windows/property-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3902:  
  
```  
// C3902.cpp  
// compile with: /clr /c  
using namespace System;  
ref class X {  
   property String ^Name {  
      void set(int);   // C3902  
      // try the following line instead  
      // void set(String^){}  
   }  
  
   property double values[int,int] {  
      void set(int, int, float);   // C3902  
      // try the following line instead  
      // void set(int, int, double){}  
   }  
};  
```