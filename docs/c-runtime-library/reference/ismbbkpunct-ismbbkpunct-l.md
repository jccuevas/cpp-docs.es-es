---
title: "_ismbbkpunct, _ismbbkpunct_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbbkpunct_l"
  - "_ismbbkpunct"
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
  - "ismbbkpunct_l"
  - "_ismbbkpunct_l"
  - "ismbbkpunct"
  - "_ismbbkpunct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ismbbkpunct_l (función)"
  - "ismbbkpunct_l (función)"
  - "ismbbkpunct (función)"
  - "_ismbbkpunct (función)"
ms.assetid: a04c59cd-5ca7-4296-bec0-2b0d7f04edd0
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _ismbbkpunct, _ismbbkpunct_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Comprueba si un carácter multibyte es un carácter de puntuación.  
  
## Sintaxis  
  
```  
int _ismbbkpunct(  
   unsigned int c   
);  
int _ismbbkpunct_l(  
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
 `_ismbbkpunct` devuelve un valor distinto de cero si el entero `c` es un signo de puntuación no ASCII; de lo contrario, devuelve 0. Por ejemplo, en la página de códigos 932 únicamente, `_ismbbkpunct` prueba si hay signos de puntuación katakana.`_ismbbkpunct` usa la configuración regional actual para cualquier valor de los caracteres dependientes de la configuración regional.`_ismbbkpunct_l` es exactamente igual, salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ismbbkpunct`|\<mbctype.h\>|  
|`_ismbbkpunct_l`|\<mbctype.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [\_ismbb \(Rutinas\)](../../c-runtime-library/ismbb-routines.md)