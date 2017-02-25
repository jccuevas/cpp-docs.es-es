---
title: "MMWORD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MMWORD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MMWORD directive"
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# MMWORD
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza para los operandos multimedia 64 bits con las instrucciones MMX y de SSE \(MMX\).  
  
## Sintaxis  
  
```  
MMWORD  
```  
  
## Comentarios  
 `MMWORD` es un tipo.  Antes de MMWORD que fue agregado a MASM, la funcionalidad equivalente podría haberse lograr con:  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 Aunque ambas instrucciones funcionan en los operandos de 64 bits, `QWORD` es el tipo para enteros sin signo de 64 bits y `MMWORD` es el tipo por un valor multimedia 64 bits.  
  
 `MMWORD` está pensado para representar el mismo tipo que [\_\_m64](../../cpp/m64.md).  
  
## Ejemplo  
  
```  
movq     mm0, mmword ptr [ebx]  
```