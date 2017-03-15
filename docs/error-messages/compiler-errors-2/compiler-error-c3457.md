---
title: "Error del compilador C3457 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3457"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3457"
ms.assetid: 5c1e366a-fa75-4cca-b9a3-86d4ebe4090e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3457
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'atributo': el atributo no admite argumentos sin nombre  
  
 Los atributos de anotación del código fuente, a diferencia del atributo personalizado de CLR o los atributos de compilador, solo admiten argumentos con nombre.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3457.  
  
```  
#include "SourceAnnotations.h" [vc_attributes::Post( 1 )] int f();   // C3457 [vc_attributes::Post( Valid=vc_attributes::Yes )] int f2();   // OK  
```