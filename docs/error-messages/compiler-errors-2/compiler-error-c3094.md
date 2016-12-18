---
title: "Error del compilador C3094 | Microsoft Docs"
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
  - "C3094"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3094"
ms.assetid: 10da9b7c-e72d-4013-9925-c83e1bb142db
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3094
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'attribute': uso anónimo no permitido  
  
 Un atributo no estaba dirigido correctamente.  Para obtener más información, consulta [Atributos definidos por el usuario](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3094:  
  
```  
// C3094.cpp // compile with: /clr /c using namespace System; [AttributeUsage(AttributeTargets::Class)] public ref class AAttribute : Attribute {}; [A];   // C3094 // OK [A] ref class x{};  
```