---
title: "___lc_codepage_func | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "___lc_codepage_func"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lc_codepage_func"
  - "___lc_codepage_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "___lc_codepage_func"
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# ___lc_codepage_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Función de CRT interna.  Recupera la página de código actual del subproceso.  
  
## Sintaxis  
  
```cpp  
UINT ___lc_codepage_func(void);  
```  
  
## Valor devuelto  
 Página de código actual del subproceso.  
  
## Comentarios  
 `___lc_codepage_func` es una función de CRT interna a la que recurren otras funciones de CRT para obtener la página de código actual del almacén local de subprocesos de datos de CRT.  Esta información también se puede obtener mediante la función [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md).  
  
 Una *página de código* es una asignación de códigos de byte único o de doble byte a caracteres individuales.  Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.  Para obtener más información sobre las páginas de códigos, vea [Páginas de códigos](../c-runtime-library/code-pages.md).  
  
 Las funciones de CRT internas son específicas de la implementación y están sujetas a cambio en cada versión.  Se desaconseja usarlas en el código.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`___lc_codepage_func`|crt\\src\\setlocal.h|  
  
## Vea también  
 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale, \_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../c-runtime-library/reference/free-locale.md)