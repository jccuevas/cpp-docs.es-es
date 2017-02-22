---
title: "Error del compilador C3800 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3800"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3800"
ms.assetid: c653240a-b6db-4437-8d65-fa58f0e6fcf4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3800
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaración': no se pueden mezclar propiedades y eventos  
  
 No se puede declarar una construcción para que sea a la vez una propiedad y un evento.  
  
 Sólo se puede reproducir el error C3800 utilizando **\/clr:oldSyntax**.  
  
 El código siguiente genera el error C3800:  
  
```  
// C3800.cpp  
// compile with: /clr:oldSyntax  
#using "mscorlib.dll"  
  
__delegate void MyDel();  
public __gc struct S  
{  
   __property __event void set_E(MyDel*)  
   {  
   }   // C3800  
};  
  
int main()  
{  
}  
```