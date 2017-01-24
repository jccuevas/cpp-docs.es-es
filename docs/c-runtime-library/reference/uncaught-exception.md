---
title: "__uncaught_exception | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__uncaught_exception"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__uncaught_exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__uncaught_exception"
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __uncaught_exception
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica si se han producido una o más excepciones, pero todavía no se han administrados por el bloque correspondiente de `catch` de una instrucción de [intento\-captura](../../cpp/try-throw-and-catch-statements-cpp.md) .  
  
## Sintaxis  
  
```cpp  
bool __uncaught_exception(  
   );  
```  
  
## Valor devuelto  
 `true` desde el momento en que se produce una excepción en `try` bloqueado hasta que se inicialice el bloque coincidentes de `catch` ; si no, `false`.  
  
## Comentarios  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_\_uncaught\_exception|eh.h|  
  
## Vea también  
 [Instrucciones try, throw y catch \(C\+\+\)](../../cpp/try-throw-and-catch-statements-cpp.md)