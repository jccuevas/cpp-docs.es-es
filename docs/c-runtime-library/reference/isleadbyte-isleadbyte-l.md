---
title: "isleadbyte, _isleadbyte_l | Microsoft Docs"
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
  - "_isleadbyte_l"
  - "isleadbyte"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_istleadbyte"
  - "_isleadbyte_l"
  - "isleadbyte"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "bytes iniciales"
  - "_isleadbyte_l (función)"
  - "_istleadbyte (función)"
  - "istleadbyte (función)"
  - "isleadbyte (función)"
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isleadbyte, _isleadbyte_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un carácter es el byte inicial de un carácter multibyte.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int isleadbyte(  
   int c   
);  
int _isleadbyte_l(  
   int c   
);  
```  
  
#### Parámetros  
 `c`  
 Entero que se va a probar.  
  
## Valor devuelto  
 `isleadbyte` devuelve un valor distinto de cero si el argumento cumple la condición de prueba o 0 si no la cumple. En la configuración regional de "C" y en configuraciones regionales de juegos de caracteres de byte único \(SBCS\), `isleadbyte` devuelve siempre 0.  
  
## Comentarios  
 La macro `isleadbyte` devuelve un valor distinto de cero si el argumento es el primer byte de un carácter multibyte.`isleadbyte` genera un resultado significativo para cualquier argumento entero de –1 \(`EOF`\) a `UCHAR_MAX` \(0xFF\), incluidos.  
  
 El tipo de argumento esperado de `isleadbyte` es `int`; si se pasa un carácter con signo, el compilador podría convertirlo en un entero por la extensión de signo y producir resultados imprevisibles.  
  
 La versión de esta función con el sufijo `_l` es idéntica, salvo que usa la configuración regional pasada en lugar de la configuración regional de su comportamiento dependiente de la configuración regional.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_istleadbyte`|Siempre devuelve false|**\_** `isleadbyte`|Siempre devuelve false|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`isleadbyte`|\<ctype.h\>|  
|`_isleadbyte_l`|\<ctype.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No está disponible, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx).  
  
## Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [\_ismbb \(Rutinas\)](../../c-runtime-library/ismbb-routines.md)