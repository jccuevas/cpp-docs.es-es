---
title: "Advertencia del compilador (nivel 2) C4826 | Microsoft Docs"
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
  - "C4826"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4826"
ms.assetid: 286f5c1d-8c14-43f7-aaa6-a891db2fdc64
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 2) C4826
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La conversión de 'tipo1 ' a 'tipo\_2' produce una extensión de signo.Esto puede provocar un comportamiento en tiempo de ejecución inesperado.  
  
 Esta advertencia indica que el compilador realizó la extensión de signo cuando un puntero de 32 bits se convirtió en una variable de 64 bits.  
  
 Si la extensión se realizó en un tipo HANDLE de ventanas, es seguro omitir esta advertencia.  Si la extensión se realizó en un tipo de puntero, debería modificar la conversión de tipos para evitar la extensión de signo \(vea el ejemplo siguiente\).  
  
 La advertencia C4826 está desactivada de manera predeterminada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4826.  
  
```  
// C4826.cpp  
// compile with: /W2 /c  
#include <windows.h>  
#pragma warning(default: 4826)  
  
void * __ptr64 F1 (void * __ptr32 P ) {  
   return (void * __ptr64)P;   // C4826  
   // try the following line instead  
   // return (void * __ptr64)(ULONGLONG)(ULONG)P;  
}  
  
void * __ptr64 F2 ( void * P ) {  
   return (void * __ptr64)P;   // C4826  
   // try the following line instead  
   // return (void * __ptr64)(ULONGLONG)(ULONG)P;  
}  
  
unsigned __int64 F3r ( void * P ) {  
   return (unsigned __int64)P;   // C4826  
   // try the following line instead  
   // return (unsigned __int64)(ULONGLONG)(ULONG)P;  
}  
```