---
title: "Error irrecuperable C1190 | Microsoft Docs"
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
  - "C1190"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1190"
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1190
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

un código de destino administrado requiere una opción '\/clr'  
  
 Está usando construcciones CLR, pero no especificó **\/clr**.  
  
 Para obtener más información, consulta [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 El ejemplo siguiente genera la advertencia C1190:  
  
```  
// C1190.cpp // compile with: /c __gc class A {};   // C1190 ref class A {};  
```