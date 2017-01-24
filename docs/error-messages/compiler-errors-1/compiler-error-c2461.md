---
title: "Error del compilador C2461 | Microsoft Docs"
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
  - "C2461"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2461"
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2461
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase' : en la sintaxis del constructor faltan parámetros formales  
  
 El constructor de la clase no especifica ningún parámetro formal.  La declaración de un constructor debe especificar un parámetro formal. La lista puede ser nula.  
  
 Agregue un par de paréntesis después de `class``::``class`  
  
 El código siguiente genera el error C2461:  
  
```  
// C2461.cpp  
// compile with: /c  
class C {  
   C::C;   // C2461  
   C::C();   // OK  
};  
```