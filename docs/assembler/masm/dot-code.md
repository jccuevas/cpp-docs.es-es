---
title: ".CODE | Microsoft Docs"
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
  - ".CODE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".CODE directive"
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .CODE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando se utiliza con [.MODEL](../../assembler/masm/dot-model.md), indica el inicio de un segmento de código.  
  
## Sintaxis  
  
```  
.CODE [[name]]  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`name`|Parámetro opcional que especifica el nombre del segmento de código.  El nombre predeterminado es \_TEXT para [modelos](../../assembler/masm/dot-model.md)en minúscula, pequeño, compacto, y plano.  el nombre predeterminado es \_TEXT de *modulename*para otros modelos.|  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)