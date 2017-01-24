---
title: "Error irrecuperable C1103 | Microsoft Docs"
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
  - "C1103"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1103"
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1103
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error irrecuperable al importar el id. de programa: 'mensaje'  
  
 El compilador detectó un problema al importar una biblioteca de tipos.  Por ejemplo, no se puede especificar una biblioteca de tipos con id. de programa y también `no_registry`.  
  
 Para obtener más información, consulte [\#import \(Directiva\)](../../preprocessor/hash-import-directive-cpp.md).  
  
 El ejemplo siguiente genera el error C1103:  
  
```  
// C1103.cpp #import "progid:a.b.id.1.5" no_registry auto_search   // C1103  
```