---
title: "___lc_locale_name_func | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "___lc_locale_name_func"
apilocation: 
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "___lc_locale_name_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "___lc_locale_name_func"
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# ___lc_locale_name_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Función de CRT interna.  Recupera el nombre de configuración regional local del subproceso.  
  
## Sintaxis  
  
```cpp  
wchar_t** ___lc_locale_name_func(void);  
```  
  
## Valor devuelto  
 Puntero a una cadena que contiene el nombre de configuración regional local del subproceso.  
  
## Comentarios  
 `___lc_locale_name_func` es una función de CRT interna a la que recurren otras funciones de CRT para obtener el nombre de configuración local actual del almacén local de subprocesos de datos de CRT.  Esta información también se puede obtener mediante la función [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md) o las funciones [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 Las funciones de CRT internas son específicas de la implementación y están sujetas a cambio en cada versión.  Se desaconseja usarlas en el código.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`___lc_locale_name_func`|crt\\src\\setlocal.h|  
  
## Vea también  
 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale, \_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../c-runtime-library/reference/free-locale.md)