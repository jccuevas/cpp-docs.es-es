---
title: "operator IMAGEREL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "operator IMAGEREL"
  - "IMAGEREL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator IMAGEREL"
  - "IMAGEREL operator"
ms.assetid: 5b5ea425-36f0-467c-9262-62c484b7fdb4
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# operator IMAGEREL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve la diferencia de relativa de la imagen de `expression`.  
  
## Sintaxis  
  
```  
IMAGEREL expression  
```  
  
## Comentarios  
 El valor resultante se conoce a menudo como dirección virtual de RVA o de Relativo.  
  
 IMAGEREL solo está disponible con la emisión del objeto COFF.  
  
## Vea también  
 [Operators Reference](../../assembler/masm/operators-reference.md)