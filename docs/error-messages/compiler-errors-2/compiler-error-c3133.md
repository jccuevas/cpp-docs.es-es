---
title: "Error del compilador C3133 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3133"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3133"
ms.assetid: 4a709405-b67b-4061-8a2a-19fa5fb34a2a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3133
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede aplicar atributos a varargs de C\+\+  
  
 Se ha aplicado incorrectamente un atributo.  No se pueden aplicar atributos a puntos suspensivos que representen argumentos variables.  
  
 Para obtener más información, vea [Atributos definidos por el usuario](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3133.  
  
```  
// C3133.cpp  
// compile with: /clr /c  
ref struct MyAttr: System::Attribute {};   
void Func([MyAttr]...);   // C3133  
void Func2([MyAttr] int i);   // OK  
```