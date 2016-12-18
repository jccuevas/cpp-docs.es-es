---
title: "ALIAS (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Alias"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ALIAS directive"
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ALIAS (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la directiva de **Alias** crea un nombre alternativo para una función.  Esto permite crear varios nombres para una función, o crear bibliotecas que permiten que el vinculador \(LINK.exe\) asigna una antigua función a una nueva función.  
  
## Sintaxis  
  
```  
  
ALIAS  <  
alias  
> = <  
actual-name  
>  
  
```  
  
#### Parámetros  
 `actual-name`  
 El nombre real de la función o el procedimiento.  se requieren los corchetes angulares.  
  
 `alias`  
 El suplente o el alias.  se requieren los corchetes angulares.  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)