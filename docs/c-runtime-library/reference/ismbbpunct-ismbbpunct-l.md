---
title: "_ismbbpunct, _ismbbpunct_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbbpunct"
  - "_ismbbpunct_l"
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
  - "ismbbpunct"
  - "ismbbpunct_l"
  - "_ismbbpunct_l"
  - "_ismbbpunct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ismbbpunct (función)"
  - "_ismbbpunct (función)"
  - "ismbbpunct_l (función)"
  - "_ismbbpunct_l (función)"
ms.assetid: 1976c9d3-7d1a-415f-ac52-2715c7bb56eb
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _ismbbpunct, _ismbbpunct_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un carácter determinado es un carácter de puntuación.  
  
## Sintaxis  
  
```  
int _ismbbpunct(  
   unsigned int c   
);  
int _ismbbpunct_l(  
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
 `_ismbbpunct` devuelve un valor distinto de cero si el entero `c` es un símbolo de puntuación no ASCII.`_ismbbpunct` usa la configuración regional actual para cualquier valor de los caracteres dependientes de la configuración regional.`_ismbbpunct_l` es exactamente igual, salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ismbbpunct`|\<mbctype.h\>|  
|`_ismbbpunct_l`|\<mbctype.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [\_ismbb \(Rutinas\)](../../c-runtime-library/ismbb-routines.md)