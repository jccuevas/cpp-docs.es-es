---
title: "Advertencia del compilador (nivel 1) C4794 | Microsoft Docs"
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
  - "C4794"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4794"
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4794
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Segmento de la variable de almacenamiento local 'variable' que cambió de 'section name' a '.tls$'  
  
 Usó [\#pragma data\_seg](../../preprocessor/data-seg.md) para colocar una variable tls en una sección que no comenzaba por .tls$.  
  
 La sección .tls$*x* existirá en el archivo objeto donde están definidas las variables [\_\_declspec\(thread\)](../../cpp/thread.md). Una sección .tls del archivo EXE o DLL será el resultado de estas secciones.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4794:  
  
```  
// C4794.cpp // compile with: /W1 /c #pragma data_seg(".someseg") __declspec(thread) int i;   // C4794 // OK #pragma data_seg(".tls$9") __declspec(thread) int j;  
```