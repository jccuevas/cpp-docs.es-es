---
title: "_ismbbkprint, _ismbbkprint_l | Microsoft Docs"
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
  - "_ismbbkprint"
  - "_ismbbkprint_l"
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
  - "_ismbbkprint_l"
  - "ismbbkprint"
  - "_ismbbkprint"
  - "ismbbkprint_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbbkprint (función)"
  - "ismbbkprint_l (función)"
  - "ismbbkprint (función)"
  - "_ismbbkprint_l (función)"
ms.assetid: 8d1d3258-1e34-4365-81ed-97c95de25475
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbbkprint, _ismbbkprint_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un carácter multibyte determinado es un signo de puntuación.  
  
## Sintaxis  
  
```  
int _ismbbkprint(  
   unsigned int c   
);  
int _ismbbkprint_l(  
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
 `_ismbbkprint` devuelve un valor distinto de cero si el entero `c` es un texto no ASCII o un signo de puntuación no ASCII; de lo contrario devuelve 0. Por ejemplo, solo en la página de códigos 932, `_ismbbkprint` comprueba si hay caracteres o signos de puntuación katakana \(intervalo: 0xA1 – 0xDF\).`_ismbbkprint` usa la configuración regional actual para los valores de caracteres dependientes de la configuración regional.`_ismbbkprint_l`  es exactamente igual, salvo que usa el parámetro de configuración regional que se pasa. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ismbbkprint`|\<mbctype.h\>|  
|`_ismbbkprint_l`|\<mbctype.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [\_ismbb \(Rutinas\)](../../c-runtime-library/ismbb-routines.md)