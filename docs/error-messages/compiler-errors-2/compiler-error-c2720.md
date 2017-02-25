---
title: "Error del compilador C2720 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2720"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2720"
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2720
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : el especificador de clase de almacenamiento 'specifier' no es válido para miembros  
  
 La clase de almacenamiento no se puede usar en los miembros de clase externos a la declaración.  Para corregir este error, quite el [especificador de clase de almacenamiento](http://msdn.microsoft.com/es-es/10b3d22d-cb40-450b-994b-08cf9a211b6c) innecesario de la definición del miembro externo a la declaración de clase.  
  
 El ejemplo siguiente genera el error C2720 y muestra cómo corregirlo:  
  
```  
// C2720.cpp  
struct S {  
   static int i;  
};  
static S::i;   // C2720 - remove the unneeded 'static' to fix it  
  
```