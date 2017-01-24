---
title: "Error del compilador C3342 | Microsoft Docs"
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
  - "C3342"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3342"
ms.assetid: 5c6d784f-bebe-4f7e-8615-44ca6f78bfba
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3342
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'atributo': atributo ambiguo  
  
 El compilador encontró más de una definición de un atributo.  
  
 Un atributo se definió más de una vez.  
  
 Para obtener más información, consulte [Atributos definidos por el usuario](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3342:  
  
```  
// C3342.cpp // compile with: /clr /c using namespace System; using namespace System::Reflection; [AttributeUsage(AttributeTargets::All)] public ref class XAttribute : public  Attribute {}; [AttributeUsage(AttributeTargets::All)] public ref class X : public Attribute {}; [X]   // C3342 could refer to X or XAttribute // try the following line instead // [XAttribute] public ref class Class4 {};  
```