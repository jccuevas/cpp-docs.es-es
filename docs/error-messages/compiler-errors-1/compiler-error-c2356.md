---
title: "Error del compilador C2356 | Microsoft Docs"
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
  - "C2356"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2356"
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2356
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el segmento de inicialización no debe cambiar durante la unidad de traducción  
  
 Causas posibles:  
  
-   `#pragma init_seg` precedido por código de inicialización de segmento  
  
-   `#pragma init_seg` precedido por otro `#pragma init_seg`  
  
 Para solucionarlo, traslade el código de inicialización del segmento al comienzo del módulo.  Si es necesario inicializar varias áreas, trasládelas a módulos separados.  
  
 El código siguiente genera el error C2356:  
  
```  
// C2356.cpp  
#pragma warning(disable : 4075)  
  
int __cdecl myexit(void (__cdecl *)());  
int __cdecl myexit2(void (__cdecl *)());  
  
#pragma init_seg(".mine$m",myexit)  
#pragma init_seg(".mine$m",myexit2)   // C2356  
```