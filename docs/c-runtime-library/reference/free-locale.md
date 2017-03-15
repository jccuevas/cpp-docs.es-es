---
title: "_free_locale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_free_locale"
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
  - "api-ms-win-crt-locale-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__free_locale"
  - "free_locale"
  - "_free_locale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__free_locale (función)"
  - "_free_locale (función)"
  - "free_locale (función)"
  - "configuraciones regionales, liberar"
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _free_locale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Libera un objeto de la configuración regional.  
  
## Sintaxis  
  
```  
void _free_locale(  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `locale`  
 Objeto de la configuración regional a liberar.  
  
## Comentarios  
 La función de `_free_locale` se utiliza para liberar el objeto de configuración regional obtenido de una llamada a `_get_current_locale` o a `_create_locale`.  
  
 El nombre anterior de esta función, `__free_locale` \(con dos subrayado principales\) está desusado.  
  
## Requisitos  
  
|`Routine`|Encabezado necesario|  
|---------------|--------------------------|  
|`_free_locale`|\<locale.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No hay equivalente.  
  
## Vea también  
 [\_get\_current\_locale](../../c-runtime-library/reference/get-current-locale.md)   
 [\_create\_locale, \_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)