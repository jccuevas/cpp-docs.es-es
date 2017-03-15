---
title: "__p__commode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__p__commode"
apilocation: 
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__p__commode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__p__commode"
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# __p__commode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Señala la variable global de `_commode` , que especifica *el modo de confirmación* del archivo predeterminado para las operaciones de E\/S de archivo.  
  
## Sintaxis  
  
```cpp  
int * __p__commode(  
   );  
```  
  
## Valor devuelto  
 Puntero a la variable global de `_commode` .  
  
## Comentarios  
 La función de `__p__commode` es para uso interno, y no se debe llamar desde código de usuario.  
  
 El modo de confirmación de archivo especifica cuando los datos crítico se escribe en el disco.  Para obtener más información, vea [fflush](../c-runtime-library/reference/fflush.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_\_p\_\_commode|internal.h|