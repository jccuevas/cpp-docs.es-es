---
title: "Error del compilador C2262 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2262"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2262"
ms.assetid: 727d1c6e-53e8-40e5-b7b8-6a7ac2011727
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Error del compilador C2262
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'attribute\_specifiers': las declaraciones InternalsVisibleTo no pueden especificar una versión, referencia cultural o arquitectura de procesador.  
  
 El atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> no se especificó correctamente.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C2262.  
  
```  
// C2262.cpp // compile with: /clr /c using namespace System::Runtime::CompilerServices; [assembly: InternalsVisibleTo("assembly_name, version=1.2.3.7")];   // C2262 [assembly: InternalsVisibleTo("assembly_name ")];   // OK  
```