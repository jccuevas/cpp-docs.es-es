---
title: "_ismbbalpha, _ismbbalpha_l | Microsoft Docs"
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
  - "_ismbbalpha"
  - "_ismbbalpha_l"
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
  - "ismbbalpha"
  - "ismbbalpha_l"
  - "_ismbbalpha"
  - "_ismbbalpha_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ismbbalpha (función)"
  - "ismbbalpha_l (función)"
  - "_ismbbalpha (función)"
  - "_ismbbalpha_l (función)"
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbbalpha, _ismbbalpha_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un carácter multibyte especificado es alfa.  
  
## Sintaxis  
  
```  
int _ismbbalpha(  
   unsigned int c   
);  
int _ismbbalpha_l(  
   unsigned int c   
);  
```  
  
#### Parámetros  
 `c`  
 Entero que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_ismbbalpha` devuelve un valor distinto de cero si la expresión:  
  
```  
isalpha || _ismbbkalnum  
```  
  
 es distinto de cero para `c` o 0 si no lo es.`_ismbbalpha` usa la configuración regional actual para cualquier valor de los caracteres dependientes de la configuración regional.`_ismbbalpha_l` es exactamente igual, salvo que usa el parámetro de configuración regional que se pasa.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ismbbalpha`|\<mbctype.h\>|  
|`_ismbbalpha_l`|\<mbctype.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [\_ismbb \(Rutinas\)](../../c-runtime-library/ismbb-routines.md)