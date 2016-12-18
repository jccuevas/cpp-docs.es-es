---
title: "_get_current_locale | Microsoft Docs"
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
  - "_get_current_locale"
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
  - "get_current_locale"
  - "__get_current_locale"
  - "_get_current_locale"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__get_current_locale (función)"
  - "_get_current_locale (función)"
  - "get_current_locale (función)"
  - "configuraciones regionales, obtener información sobre"
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_current_locale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene un objeto de configuración regional que representa la configuración regional actual.  
  
## Sintaxis  
  
```  
_locale_t _get_current_locale(void);  
```  
  
## Valor devuelto  
 Un objeto de configuración regional que representa la configuración regional actual.  
  
## Comentarios  
 La funciónde `_get_current_locale`obtiene la configuración regional actualmente establecida en el subproceso y devuelve un objeto de configuración regional que representa esa configuración regional.  
  
 El nombre anterior de esta función, `__get_current_locale` \(con dos subrayado principales\) está desusado.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_get_current_locale`|\<locale.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No hay equivalente.  
  
## Vea también  
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale, \_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)