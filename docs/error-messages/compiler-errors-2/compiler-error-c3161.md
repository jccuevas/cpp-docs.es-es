---
title: "Error del compilador C3161 | Microsoft Docs"
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
  - "C3161"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3161"
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3161
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'interfaz' : el anidamiento de una clase, struct, unión o interfaz en una interfaz no es válido; el anidamiento de una interfaz en una clase, struct o unión no es válido  
  
 La palabra clave [\_\_interface](../../cpp/interface.md) sólo puede aparecer en el ámbito global o dentro de un espacio de nombres.  Una clase, struct o unión no pueden aparecer en una interfaz.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3161.  
  
```  
// C3161.cpp  
// compile with: /c  
__interface X {  
   __interface Y {};   // C3161 A nested interface  
};  
```