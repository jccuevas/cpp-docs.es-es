---
title: "Error del compilador C3292 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3292"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3292"
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3292
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el espacio de nombres cli no se puede abrir de nuevo  
  
 El espacio de nombres cli no se puede declarar en su código.  Para obtener más información, consulta [Espacios de nombres de plataforma, predeterminado y CLI](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3292.  
  
```  
// C3292.cpp // compile with: /clr /c namespace cli {};   // C3292  
```