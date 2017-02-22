---
title: "Error del compilador C3136 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3136"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3136"
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3136
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'interfaz' : una interfaz COM sólo puede heredar de otra interfaz COM; 'interfaz' no es una interfaz COM  
  
 Una interfaz a la que se aplicó un [atributo de interfaz](../../windows/interface-attributes.md) hereda de una interfaz que no es una interfaz COM.  Una interfaz COM, en última instancia, hereda de `IUnknown`.  Cualquier interfaz que vaya precedida de un atributo de interfaz es una interfaz COM.  
  
 El código siguiente genera C3136:  
  
```  
// C3136.cpp  
#include "unknwn.h"  
  
__interface A   // C3136  
// try the following line instead  
// _interface A : IUnknown  
{  
   int a();  
};  
  
[object]  
__interface B : A  
{  
   int aa();  
};  
```