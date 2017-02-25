---
title: "Error del compilador C2410 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2410"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2410"
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C2410
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': nombre de miembro ambiguo en 'contexto'  
  
 El identificador es miembro de más de una estructura o unión en este contexto.  
  
 Utilice un especificador de estructura o unión en el operando que causó el error.  Un especificador de estructura o unión es un identificador de tipo `struct` o `union` \(un nombre `typedef` o una variable del mismo tipo que la estructura o unión a que se hace referencia\).  El especificador debe ser el operando izquierdo del primer operador de selección de miembro \(.\) que utilice el operando.