---
title: "Advertencia del compilador C4430 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4430"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4430"
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador C4430
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

falta el especificador de tipo; se presupone int.Nota: C\+\+ no admite default\-int  
  
 Este error puede producirse como consecuencia del trabajo de conformidad del compilador realizado para Visual C\+\+ 2005: todas las declaraciones deben especificar el tipo de forma explícita; ya no se presupone int.  
  
 La advertencia C4430 siempre se emite como error.  Puede desactivar esta advertencia con `#pragma warning` o **\/wd**; vea [warning](../../preprocessor/warning.md) o [\/w, \/Wn, \/WX, \/Wall, \/wln, \/wdn, \/wen, \/won \(Nivel de advertencia\)](../../build/reference/compiler-option-warning-level.md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4430.  
  
```  
// C4430.cpp  
// compile with: /c  
struct CMyClass {  
   CUndeclared m_myClass;  // C4430  
   int m_myClass;  // OK  
};  
  
typedef struct {  
   POINT();   // C4430  
   // try the following line instead  
   // int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```