---
title: "Error del compilador C2480 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2480"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2480"
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2480
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : 'thread' sólo es válido para elementos de datos de extensión estática  
  
 No puede utilizar el atributo `thread` con una variable automática, un miembro de datos no estático o un parámetro de función, ni en declaraciones de función o definiciones.  
  
 Utilice el atributo `thread` únicamente para variables globales, miembros de datos estáticos y variables estáticas locales.  
  
 El código siguiente genera el error C2480:  
  
```  
// C2480.cpp  
// compile with: /c  
__declspec( thread ) void func();   // C2480  
__declspec( thread ) static int i;   // OK  
```