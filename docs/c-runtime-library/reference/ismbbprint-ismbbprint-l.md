---
title: "_ismbbprint, _ismbbprint_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbbprint_l"
  - "_ismbbprint"
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
  - "_ismbbprint_l"
  - "_ismbbprint"
  - "ismbbprint"
  - "ismbbprint_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ismbbprint_l (función)"
  - "ismbbprint (función)"
  - "_ismbbprint (función)"
  - "_ismbbprint_l (función)"
ms.assetid: d08a061c-18a8-48f2-a75d-bff4870aec9d
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _ismbbprint, _ismbbprint_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si el carácter multibyte especificado es un carácter imprimible.  
  
## Sintaxis  
  
```  
int _ismbbprint(  
   unsigned int c   
);  
int _ismbbprint_l(  
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
 `_ismbbprint` devuelve un valor distinto de cero si la expresión:  
  
```  
isprint || _ismbbkprint  
```  
  
 es distinto de cero para `c` o 0 si no lo es.`_ismbbprint` usa la configuración regional actual para cualquier comportamiento que dependa de la configuración regional.`_ismbbprint_l` es exactamente igual, salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ismbbprint`|\<mbctype.h\>|  
|`_ismbbprint_l`|\<mbctype.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [\_ismbb \(Rutinas\)](../../c-runtime-library/ismbb-routines.md)