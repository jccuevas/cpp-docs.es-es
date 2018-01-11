---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
dev_langs: C++
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7fe06748a6e349f612fdf564c9aed917e43f164b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tolower-tolower-towlower-tolowerl-towlowerl"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l
Convierte un carácter a minúsculas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int tolower(  
   int c   
);  
int _tolower(  
   int c   
);  
int towlower(  
   wint_t c   
);  
int _tolower_l(  
   int c,  
   _locale_t locale   
);  
int _towlower_l(  
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `c`  
 Carácter que se va a convertir.  
  
 [in] `locale`  
 Configuración regional que se va a usar para la traducción específica de configuración regional.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas rutinas convierte una copia de `c` a minúsculas, si la conversión es posible, y devuelve el resultado. No se reserva ningún valor devuelto para indicar un error.  
  
## <a name="remarks"></a>Comentarios  
 Cada una de estas rutinas convierte una determinada letra mayúscula en una letra minúscula si es posible y pertinente. La conversión de mayúsculas y minúsculas de `towlower` es específica de la configuración regional. Solo se convierten los caracteres pertinentes para la configuración regional actual. Las funciones sin el sufijo `_l` usan la configuración regional establecida en ese momento. Las versiones de estas funciones que tienen el sufijo `_l` toman la configuración regional como un parámetro y lo usan en lugar de la configuración regional establecida en ese momento. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).  
  
 Para que `_tolower` produzca los resultados esperados, [__isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) e [isupper](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) deben devolver un valor distinto de cero.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_totlower`|`tolower`|`_mbctolower`|`towlower`|  
|`_totlower_l`|`_tolower_l`|`_mbctolower_l`|`_towlower_l`|  
  
> [!NOTE]
>  `_tolower_l` y `_towlower_l` no dependen de la configuración regional y no están diseñadas para llamarlas directamente. Se proporcionan solo para el uso interno por parte de `_totlower_l`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`tolower`|\<ctype.h>|  
|`_tolower`|\<ctype.h>|  
|`towlower`|\<ctype.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [to (Funciones)](../../c-runtime-library/to-functions.md).  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)   
 [to (Funciones)](../../c-runtime-library/to-functions.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)