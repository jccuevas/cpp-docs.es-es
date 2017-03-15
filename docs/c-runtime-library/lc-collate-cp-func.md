---
title: "___lc_collate_cp_func | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "___lc_collate_cp_func"
apilocation: 
  - "msvcr120.dll"
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "___lc_collate_cp_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "___lc_collate_cp_func"
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# ___lc_collate_cp_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Función de CRT interna.  Recupera la página de código de intercalación actual del subproceso.  
  
## Sintaxis  
  
```cpp  
UINT ___lc_codepage_func(void);  
```  
  
## Valor devuelto  
 Página de código de intercalación actual del subproceso.  
  
## Comentarios  
 `___lc_collate_cp_func` es una función de CRT interna a la que recurren otras funciones de CRT para obtener la página de código de intercalación actual del almacén local de subprocesos de datos de CRT.  Esta información también se puede obtener mediante la función [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md).  
  
 Las funciones de CRT internas son específicas de la implementación y están sujetas a cambio en cada versión.  Se desaconseja usarlas en el código.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`___lc_collate_cp_func`|crt\\src\\setlocal.h|  
  
## Vea también  
 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale, \_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../c-runtime-library/reference/free-locale.md)