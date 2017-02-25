---
title: "Advertencia del compilador (nivel 1) C4688 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4688"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4688"
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 1) C4688
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'constraint': la lista de restricciones contiene un tipo privado de ensamblado 'type'  
  
 Una lista de restricciones tiene un tipo privado de ensamblado, lo que significa que no estará disponible cuando se acceda al tipo desde fuera del ensamblado. Para obtener más información, consulta [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4688.  
  
```  
// C4688.cpp // compile with: /clr /c /W1 ref struct A {};   // private type public ref struct B {}; // Delete the following 3 lines to resolve. generic <class T> where T : A   // C4688 public ref struct M {}; generic <class T> where T : B public ref struct N {};  
```