---
title: "jitintrinsic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "jitintrinsic"
  - "jitintrinsic_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], jitintrinsic"
  - "jitintrinsic __declspec (modificador)"
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# jitintrinsic
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Marca la función como significativa para Common Language Runtime de 64 bits.  Se utiliza en algunas funciones de bibliotecas proporcionadas por Microsoft.  
  
## Sintaxis  
  
```  
__declspec(jitintrinsic)  
```  
  
## Comentarios  
 `jitintrinsic` agrega un objeto MODOPT \(<xref:System.Runtime.CompilerServices.IsJitIntrinsic>\) a una firma de función.  
  
 No se recomienda a los usuarios que utilicen este modificador `__declspec`, ya que pueden producirse resultados inesperados.  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)