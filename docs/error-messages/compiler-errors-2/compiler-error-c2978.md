---
title: "Error del compilador C2978 | Microsoft Docs"
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
  - "C2978"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2978"
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2978
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis: se esperaba 'palabraClave1' o 'palabraClave2'; se encontró el tipo 'palabraClave3'; no se admiten parámetros sin tipo en genéricos  
  
 Se declaró una clase genérica incorrectamente. Vea [Genéricos](../../windows/generics-cpp-component-extensions.md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C2978.  
  
```  
// C2978.cpp // compile with: /clr /c generic <ref class T>   // C2978 // try the following line instead // generic <typename T>   // OK ref class Utils { static void sort(T elems, size_t size); }; generic <int> // try the following line instead // generic <class T> ref class Utils2 { static void sort(T elems, size_t size); };  
```