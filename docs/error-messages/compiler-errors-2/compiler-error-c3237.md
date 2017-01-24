---
title: "Error del compilador C3237 | Microsoft Docs"
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
  - "C3237"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3237"
ms.assetid: 690970c8-e13b-4ff3-96e3-5fd93c4d356b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3237
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'generic\_class': una clase genérica no puede ser un atributo personalizado  
  
 Las clases genéricas no pueden ser atributos definidos por el usuario.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3237.  
  
```  
// C3237.cpp // compile with: /clr /c // C3237 expected using namespace System; generic <class T> // Delete the following line to resolve. [attribute(AttributeTargets::All, AllowMultiple=true)] public ref class GR {};  
```