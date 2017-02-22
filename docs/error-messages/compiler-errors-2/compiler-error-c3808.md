---
title: "Error del compilador C3808 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3808"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3808"
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3808
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : una clase con el atributo ComImport no puede definir el miembro 'member'; solamente se permiten las funciones abstract o dllimport  
  
 Un tipo que se haya derivado de <xref:System.Runtime.InteropServices.ComImportAttribute> no podrá definir el miembro `member`.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3808.  
  
```  
// C3808.cpp  
// compile with: /c /clr:pure user32.lib  
using namespace System::Runtime::InteropServices;  
  
[System::Runtime::InteropServices::ComImportAttribute()]  
ref struct S1 {  
   int f() {}   // C3808  
   virtual int g() abstract;   // OK  
  
   [DllImport("msvcrt.dll")]  
   int printf(System::String ^, int i);   // OK  
};  
```