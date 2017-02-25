---
title: "LOCAL (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Local"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LOCAL directive"
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# LOCAL (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En la primera directiva, dentro de una macro, **LOCAL** define las etiquetas que son únicas para cada instancia de la macro.  
  
## Sintaxis  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## Comentarios  
 En la segunda directiva, dentro de una definición de procedimiento \(**PROCEDURE**\), **LOCAL** crea variables pila\-basadas que existen para la duración del procedimiento.  *La etiqueta* puede ser una variable simple o una matriz que contiene elementos *de recuento* .  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)