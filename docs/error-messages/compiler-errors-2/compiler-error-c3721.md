---
title: "Error del compilador C3721 | Microsoft Docs"
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
  - "C3721"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3721"
ms.assetid: c696ca38-3e00-4875-abbe-7bce0f46930e
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3721
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'firma': firma no compatible para el evento  
  
 Se declaró incorrectamente un evento.  Para obtener más información, vea [\_\_event](../../cpp/event.md).  
  
 Sólo se puede reproducir el error C3721 utilizando **\/clr:oldSyntax**.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3721.  
  
```  
// C3721.cpp  
// compile with: /clr:oldSyntax /c  
using namespace System;  
  
public __delegate void MyDel();  
  
public __gc class X {  
   __event void add_E1();      // C3721  
   // try the following line instead  
   // __event void add_E1(MyDel * p);  
  
   __event void remove_E1();   // C3721  
   // __event void remove_E1(MyDel * p);  
   // try the following line instead  
  
   __event void raise_E1();  
};  
```