---
title: isprint, iswprint, _isprint_l, _iswprint_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswprint
- _istprint
- isprint
dev_langs:
- C++
helpviewer_keywords:
- _istprint function
- iswprint function
- _iswprint_l function
- isprint_l function
- istprint function
- isprint function
- iswprint_l function
- _isprint_l function
ms.assetid: a8bbcdb0-e8d0-4d8c-ae4e-56d3bdee6ca3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36d4c6fcc699392f32a45dfff6131a3b7b7e66ad
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="isprint-iswprint-isprintl-iswprintl"></a>isprint, iswprint, _isprint_l, _iswprint_l
Determina si un entero representa un carácter imprimible.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int isprint(  
   int c   
);  
int iswprint(  
   wint_t c   
);  
int _isprint_l(  
   int c,  
   _locale_t locale  
);  
int _iswprint_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Entero que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de un carácter imprimible. `isprint` Devuelve un valor distinto de cero si `c` es un carácter imprimible: Esto incluye el carácter de espacio (0 x 20 - 0x7E). `iswprint` devuelve un valor distinto de cero si `c` es un carácter ancho imprimible, incluido el carácter ancho de espacio. Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
 El resultado de la condición de prueba para estas funciones depende del valor de la categoría `LC_CTYPE` de la configuración regional; para obtener más información, vea [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual del comportamiento dependiente de la configuración regional; las versiones que tienen el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).  
  
 El comportamiento de `isprint` e `_isprint_l` es indefinido si `c` no se encuentra al final del archivo ni en el intervalo de 0 a 0xFF, incluidos. Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_unicode definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|**_** `istprint`|`isprint`|[_ismbcprint](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswprint`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`isprint`|\<ctype.h>|  
|`iswprint`|\<ctype.h> o \<wchar.h>|  
|`_isprint_l`|\<ctype.h>|  
|`_iswprint_l`|\<ctype.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)