---
title: "_ismbbtrail, _ismbbtrail_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbbtrail"
  - "_ismbbtrail_l"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ismbbtrail"
  - "ismbbtrail"
  - "_ismbbtrail_l"
  - "ismbbtrail_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ismbbtrail_l (función)"
  - "_ismbbtrail (función)"
  - "_ismbbtrail_l (función)"
  - "ismbbtrail (función)"
ms.assetid: dfdd0292-960b-4c1d-bf11-146e0fc80247
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbbtrail, _ismbbtrail_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un byte es el byte final de un carácter multibyte.  
  
## Sintaxis  
  
```  
int _ismbbtrail(  
   unsigned int c   
);  
int _ismbbtrail_l(  
   unsigned int c,  
   _locale_t locale   
);  
```  
  
#### Parámetros  
 `c`  
 Entero que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_ismbbtrail` devuelve un valor distinto de cero si el entero `c` es el segundo byte de un carácter multibyte. Por ejemplo, en la página de códigos 932 únicamente, los intervalos válidos son de 0x40 a 0x7E y de 0x80 a 0xFC.  
  
## Comentarios  
 `_ismbbtrail` usa la configuración regional actual para el comportamiento que dependa de la configuración regional.`_ismbbtrail_l` es exactamente igual, salvo que usa el parámetro de configuración regional que se pasa. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_ismbbtrail`|\<mbctype.h\> o \<mbstring.h\>|\<ctype.h\>,\* \<limits.h\>, \<stdlib.h\>|  
|`_ismbbtrail_l`|\<mbctype.h\> o \<mbstring.h\>|\<ctype.h\>,\* \<limits.h\>, \<stdlib.h\>|  
  
 \* Para las constantes de manifiesto de las condiciones de prueba.  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [\_ismbb \(Rutinas\)](../../c-runtime-library/ismbb-routines.md)