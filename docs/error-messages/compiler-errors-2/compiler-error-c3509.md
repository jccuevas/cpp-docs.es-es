---
title: "Error del compilador C3509 | Microsoft Docs"
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
  - "C3509"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3509"
ms.assetid: cc2db39a-2f98-4e40-b803-496e585494e6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3509
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': tipo de valor devuelto de automatización no válido; cuando se marca un parámetro como 'retval', el tipo de valor devuelto debe ser 'void', 'HRESULT' o 'SCODE'  
  
 Un método de una interfaz COM debe devolver void o HRESULT.  
  
 El código siguiente genera el error C3509:  
  
```  
// C3509.cpp  
#define _ATL_DEBUG_QI  
  
#define WIN32_LEAN_AND_MEAN   // Exclude rarely-used stuff from Windows headers  
#define STRICT  
#ifndef _WIN32_WINNT  
#define _WIN32_WINNT 0x0400  
#endif  
  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
extern CComModule _Module;  
#include <atlcom.h>  
#include <atlctl.h>  
#include <atlstr.h>  
  
[module(name=oso)];  
  
[dispinterface, uuid(00000000-0000-0000-0000-000000000001)]  
__interface I {  
   [id(1)] int f([out, retval] int*);   // C3509  
   // try the following line instead  
   // [id(1)] void f([out, retval] int*);  
};  
  
[coclass, uuid(00000000-0000-0000-0000-000000000002)]  
struct C : I {  
   int f(int*) {  
   // try the following line instead, and delete return statement  
   // void f(int*) {  
      return 0;  
   }  
};  
  
int main() {  
}  
```