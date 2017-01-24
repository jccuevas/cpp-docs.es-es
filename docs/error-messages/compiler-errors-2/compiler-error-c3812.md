---
title: "Error del compilador C3812 | Microsoft Docs"
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
  - "C3812"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3812"
ms.assetid: 326ac706-9a5f-4851-b9d2-b90c64c75532
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3812
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'propiedad' debe ser el primer símbolo \(token\) en una declaración de propiedad  
  
 Al declarar una propiedad, la palabra clave [\_\_property](../../misc/property.md) debe ser el primer símbolo \(token\) en la línea.  
  
 Sólo se puede llegar al error C3812 utilizando **\/clr:oldSyntax**.  
  
 El código siguiente genera el error C3812:  
  
```  
// C3812.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
  
__gc class X {  
   static __property int get_Size() { // C3812, remove static specifier  
      return 0;  
   }  
};  
```