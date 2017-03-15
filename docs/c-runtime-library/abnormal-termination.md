---
title: "_abnormal_termination | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_abnormal_termination"
apilocation: 
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_abnormal_termination"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_abnormal_termination"
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# _abnormal_termination
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica si el bloque de `__finally` de [instrucción try \- final](../cpp/try-finally-statement.md) se incorpora mientras el sistema ejecuta una lista de controladores de terminación.  
  
## Sintaxis  
  
```cpp  
int   _abnormal_termination(  
   );  
```  
  
## Valor devuelto  
 `true` si el sistema *está desenredando* la pila; si no, `false`.  
  
## Comentarios  
 Esto es una función interna utilizada para administrar excepciones el desenredo, y no está diseñada para denominada de código de usuario.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_abnormal\_termination|excpt.h|  
  
## Vea también  
 [try\-finally \(Instrucción\)](../cpp/try-finally-statement.md)