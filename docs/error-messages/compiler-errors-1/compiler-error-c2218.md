---
title: "Error del compilador C2218 | Microsoft Docs"
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
  - "C2218"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2218"
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2218
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\_\_vectorcall' no se puede usar con '\/arch:IA32'  
  
 La convención de llamada `__vectorcall` solo se admite en código nativo en procesadores x86 y x64 que incluyen Extensiones SIMD de streaming 2 \(SSE2\) y versiones posteriores.  Para obtener más información, vea [\_\_vectorcall](../../cpp/vectorcall.md).  
  
 Para corregir este error, cambie las opciones del compilador para que se dirijan a los conjuntos de instrucciones SSE2, AVX o AVX2.  Para obtener más información, vea [\/arch \(x86\)](../../build/reference/arch-x86.md).