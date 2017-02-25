---
title: "Error del compilador C2862 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2862"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2862"
ms.assetid: c04d8499-b799-48a1-9fb4-7902a0b0ac8e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2862
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'interfaz' : una interfaz sólo puede tener miembros públicos  
  
 Los miembros protegidos y privados sólo son accesibles desde otras funciones miembro.  Tales miembros no se usan en una interfaz, ya que ésta no proporciona implementaciones para ninguno de sus miembros.  
  
 El código siguiente genera el error C2862:  
  
```  
// C2862.cpp  
// compile with: /c  
#include <unknwn.h>  
  
[object, uuid="60719E20-EF37-11D1-978D-0000F805D73B"]  
__interface IMyInterface {  
   HRESULT mf1(void);   // OK  
protected:  
   HRESULT mf2(int *b);   // C2862  
private:  
   HRESULT mf3(int *c);   // C2862  
};  
```