---
title: "Error del compilador C3065 | Microsoft Docs"
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
  - "C3065"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3065"
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3065
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se permite la declaración de propiedad en un ámbito que no es de clase  
  
 El modificador \_\_declspec de [propiedad](../../cpp/property-cpp.md) se usó fuera de una clase.  Una propiedad solo puede declararse dentro de una clase.  
  
 El ejemplo siguiente genera la advertencia C3065:  
  
```  
// C3065.cpp // compile with: /c __declspec(property(get=get_i)) int i;   // C3065 class x { public: __declspec(property(get=get_i)) int i;   // OK };  
```