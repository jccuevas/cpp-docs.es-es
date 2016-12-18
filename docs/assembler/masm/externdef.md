---
title: "EXTERNDEF | Microsoft Docs"
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
  - "EXTERNDEF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EXTERNDEF directive"
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# EXTERNDEF
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Define una o más variables externas, etiquetas, o símbolos denominados name cuyo tipo es `type`.  
  
## Sintaxis  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## Comentarios  
 Si *el nombre* está definido en el módulo, se trata como [PÚBLICO](../../assembler/masm/public-masm.md).  si el *nombre* se hace referencia en el módulo, se trata como [EXTERN](../../assembler/masm/extern-masm.md).  si el *nombre* no se hace referencia, se omite.  `type` puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *nombre* como constante.  Utilizado normalmente en archivos de inclusión.  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)