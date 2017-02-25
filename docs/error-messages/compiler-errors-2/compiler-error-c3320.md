---
title: "Error del compilador C3320 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3320"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3320"
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3320
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': el tipo no puede tener el mismo nombre que la propiedad de módulo 'nombre'  
  
 Un tipo definido por el usuario \(UDT\) exportado, que podría ser una estructura, una clase, una enumeración, una unión o [\_\_value](../../misc/value.md), no puede tener el mismo nombre que el parámetro pasado a la propiedad de nombre del atributo [module](../../windows/module-cpp.md).  
  
 El ejemplo siguiente genera la advertencia C3320:  
  
```  
// C3320.cpp #include "unknwn.h" [module(name="xx")]; [export] struct xx {   // C3320 // Try the following line instead // [export] struct yy { int i; };  
```