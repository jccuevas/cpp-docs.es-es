---
title: "___setlc_active_func, ___unguarded_readlc_active_add_func | Microsoft Docs"
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
  - "___setlc_active_func"
  - "___unguarded_readlc_active_add_func"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "___unguarded_readlc_active_add_func"
  - "___setlc_active_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "___setlc_active_func"
  - "___unguarded_readlc_active_add_func"
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ___setlc_active_func, ___unguarded_readlc_active_add_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OBSOLETO.  CRT exporta estas funciones internas únicamente para conservar la compatibilidad binaria.  
  
## Sintaxis  
  
```cpp  
int ___setlc_active_func(void); int * ___unguarded_readlc_active_add_func(void);  
```  
  
## Valor devuelto  
 El valor devuelto no es significativo.  
  
## Comentarios  
 Las funciones de CRT internas `___setlc_active_func` y `___unguarded_readlc_active_add_func` están obsoletas y ya no se usan, pero la biblioteca de CRT las puede exportar para conservar la compatibilidad binaria.  La finalidad primera de `___setlc_active_func` era devolver el número de llamadas activas actualmente a la función `setlocale`.  La finalidad primera de `___unguarded_readlc_active_add_func` era devolver el número de funciones que hacían referencia a la configuración local sin bloquearla.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|ninguna|  
  
## Vea también  
 [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)