---
title: "Advertencia del compilador C4694 | Microsoft Docs"
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
  - "C4694"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4694"
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador C4694
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase\_1': una clase abstracta sellada no puede tener una clase base 'clase\_base'  
  
 Una clase abstracta y sellada no puede heredar de un tipo de referencia. Una clase sellada y abstracta no puede implementar las funciones de clase base ni permitir que se use como clase base.  
  
 Para obtener más información, vea [abstractas](../../windows/abstract-cpp-component-extensions.md), [sellado](../../windows/sealed-cpp-component-extensions.md) y [Clases y structs](../../windows/classes-and-structs-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4694.  
  
```  
// C4694.cpp // compile with: /c /clr ref struct A {}; ref struct B sealed abstract : A {};   // C4694  
```