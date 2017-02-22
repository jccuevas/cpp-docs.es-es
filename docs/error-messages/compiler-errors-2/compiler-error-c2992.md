---
title: "Error del compilador C2992 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2992"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2992"
ms.assetid: 01b16447-43fe-4e91-9a5a-af884a166a31
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C2992
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase': falta la lista de parámetros de tipo o no es válida  
  
 La clase está precedida por la palabra clave `template` o **generic** sin parámetros o con parámetros no válidos.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C2992:  
  
```  
// C2992.cpp // compile with: /c template <class T> struct TC1 { template <class U> struct TC2; }; template <class T>   struct TC1<T>::TC2 {};   // C2992 // OK template <class T> template <class U> struct TC1<T>::TC2 {}; // C2992 can also occur when using generics: // C2992c.cpp // compile with: /clr /c generic <class T> ref struct GC1 { generic <class U> ref struct GC2; }; generic <class T> ref struct GC1<T>::GC2 {};   // C2992 // OK generic <class T> generic <class U> ref struct GC1<T>::GC2 {};  
```