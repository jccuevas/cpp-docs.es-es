---
title: "Error del compilador C3179 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3179"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3179"
ms.assetid: 60d7e41b-25fd-48ac-8b79-830c062f4dcd
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C3179
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se permite un tipo administrado sin nombre o WinRT  
  
 Todas las clases y structs CLR y WinRT deben tener nombres.  
  
 El ejemplo siguiente genera el error C3179 y muestra cómo corregirlo:  
  
```  
// C3179a.cpp  
// compile with: /clr /c  
typedef value struct { // C3179  
// try the following line instead  
// typedef value struct MyStruct {  
   int i;  
} V;  
```  
  
 El ejemplo siguiente genera el error C3179 y muestra cómo corregirlo:  
  
```  
// C3179b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
typedef __value struct {   // C3179  
// try the following line instead  
// typedef __value struct MyStruct {  
   int i;  
} V;  
```