---
title: "Error del compilador C2646 | Microsoft Docs"
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
  - "C2646"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2646"
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2646
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una unión o un struct anónimo en un ámbito global o de espacio de nombres se debe declarar como static  
  
 Una unión o un struct anónimo tiene un ámbito global o de espacio de nombres pero no se ha declarado como `static`.  
  
 El ejemplo siguiente genera el error C2646 y muestra cómo corregirlo:  
  
```  
// C2646.cpp  
// compile with: /c  
union { int i; };   // C2646 not static  
  
// OK  
static union { int j; };  
union U { int i; };  
```