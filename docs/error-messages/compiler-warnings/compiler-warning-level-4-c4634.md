---
title: "Advertencia del compilador (nivel 4) C4634 | Microsoft Docs"
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
  - "C4634"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4634"
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4634
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Comentario del documento XML: no se puede aplicar: motivo  
  
 No se pueden aplicar etiquetas de documentación XML a todas las construcciones C\+\+.  Por ejemplo, no puede agregar un comentario de documentación a un espacio de nombres o plantilla.  
  
 Para obtener más información, consulta [Documentación de XML](../../ide/xml-documentation-visual-cpp.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4634.  
  
```  
// C4634.cpp // compile with: /W4 /doc /c /// This is a namespace.   // C4634 namespace hello { class MyClass  {}; };  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4634.  
  
```  
// C4634_b.cpp // compile with: /W4 /doc /c /// This is a template.   // C4634 template <class T> class MyClass  {};  
```