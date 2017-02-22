---
title: "__CxxFrameHandler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__CxxFrameHandler"
apilocation: 
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__CxxFrameHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__CxxFrameHandler"
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# __CxxFrameHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Función de CRT interna.  CRT la usa para controlar los marcos de excepción estructurados.  
  
## Sintaxis  
  
```cpp  
EXCEPTION_DISPOSITION __CxxFrameHandler(       EHExceptionRecord  *pExcept,       EHRegistrationNode *pRN,       void               *pContext,        DispatcherContext  *pDC    )  
```  
  
#### Parámetros  
 `pExcept`  
 Registro de excepción que se pasa a las posibles instrucciones `catch`.  
  
 `pRN`  
 Información dinámica sobre el marco de pila que se usa para controlar la excepción.  Para más información, vea ehdata.h.  
  
 `pContext`  
 Contexto.  \(No se usa en procesadores Intel\).  
  
 `pDC`  
 Información extra sobre la entrada de la función y el marco de pila.  
  
## Valor devuelto  
 Uno de los valores de *expresión de filtro* usado por la [try\-except \(Instrucción\)](../cpp/try-except-statement.md).  
  
## Comentarios  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_\_CxxFrameHandler|excpt.h, ehdata.h|