---
title: "Error del compilador C2268 | Microsoft Docs"
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
  - "C2268"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2268"
ms.assetid: 0ed055c9-3c6f-4df2-a5b6-85cf0e01a249
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2268
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' es una aplicación auxiliar de biblioteca predefinida para el compilador. Las aplicaciones auxiliares de biblioteca no se admiten con\/GL; compile el archivo objeto 'file' sin \/GL.  
  
 Una función definida en el código de origen tiene el mismo nombre que una función interna del compilador. Compile el módulo que contiene la función sin [\/GL](../../build/reference/gl-whole-program-optimization.md).  
  
 El ejemplo siguiente genera la advertencia C2268:  
  
```  
// C2268.c // compile with: /c // processor: x86 extern int SHFusionLoadLibrary(int lpLibFileName); int __cdecl _except_handler3(void) { return SHFusionLoadLibrary(0); } extern int main(void); void* mainCRTStartup(void* p) { p = main; return p; }  
```  
  
 y luego:  
  
```  
// C2268b.c // compile with: C2268.c /EHsc /GL /Ob0 /O2 /Fa /GS- /link /nodefaultlib // processor: x86 extern int SHFusionLoadLibrary(int lpLibFileName); extern int __cdecl _except_handler3(void); extern void mainCRTStartup(void*); int g = 2; #define ENTERCONTEXT(fail) \ int ulCookie = 0;\ if (!SHActivateContext(&ulCookie)) \ return fail;\ __try { #define LEAVECONTEXT \ } __finally {SHDeactivateContext(ulCookie);} int SHActivateContext(int* a) { return *a == g || !*a ||_except_handler3(); } void SHDeactivateContext(int a) { g = a; } int SHFusionLoadLibrary(int lpLibFileName) {   // C2268 ENTERCONTEXT(0) g = lpLibFileName; LEAVECONTEXT return lpLibFileName; } int main(void) { g = SHFusionLoadLibrary(10); return 0; }  
```