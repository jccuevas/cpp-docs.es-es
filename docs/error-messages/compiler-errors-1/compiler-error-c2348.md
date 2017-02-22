---
title: "Error del compilador C2348 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2348"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2348"
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2348
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre de tipo' : no es un agregado de estilo de C; no se puede exportar en IDL incrustado  
  
 Para colocar `struct` en un archivo .idl con el atributo [export](../../windows/export.md), `struct` sólo debe contener datos.  
  
 El código siguiente genera el error C2348:  
  
```  
// C2348.cpp  
// C2348 error expected  
[ module(name="SimpleMidlTest") ];  
  
[export]  
struct Point {  
   // Delete the following two lines to resolve.  
   Point() : m_i(0), m_j(0) {}  
   Point(int i, int j) : m_i(i), m_j(j) {}  
  
   int m_i;  
   int m_j;  
};  
```