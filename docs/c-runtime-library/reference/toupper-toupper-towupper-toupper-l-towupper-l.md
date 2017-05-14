---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
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
- towupper
- _toupper
- _totupper
- toupper
dev_langs:
- C++
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: e782f6168d48ecc1d24b90f2030909de32c9ee26
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="toupper-toupper-towupper-toupperl-towupperl"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l
Convierte caracteres a mayúsculas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int toupper(  
   int c   
);  
int _toupper(  
   int c   
);  
int towupper(  
   wint_t c   
);  
int _toupper_l(  
   int c ,  
   _locale_t locale  
);  
int _towupper_l(  
   wint_t c ,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Carácter que se va a convertir.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas rutinas convierte una copia de `c`, si es posible, y devuelve el resultado.  
  
 Si `c` es un carácter ancho para el que `iswlower` es distinto de cero y hay un carácter ancho correspondiente para el que `iswupper` es distinto de cero, `towupper` devuelve el carácter ancho correspondiente; en caso contrario, `towupper` devuelve `c` sin cambios.  
  
 No se reserva ningún valor devuelto para indicar un error.  
  
 Para que `toupper` produzca los resultados esperados, [__isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) e [islower](../../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md) deben devolver un valor distinto de cero.  
  
## <a name="remarks"></a>Comentarios  
 Cada una de estas rutinas convierte una determinada letra minúscula en una letra mayúscula si es posible y pertinente. La conversión de mayúsculas y minúsculas de `towupper` es específica de la configuración regional. Solo se convierten los caracteres pertinentes para la configuración regional actual. Las funciones sin el sufijo `_l` usan la configuración regional establecida en ese momento. Las versiones de estas funciones con el sufijo `_l` toman la configuración regional como un parámetro y lo usan en lugar de la configuración regional establecida en ese momento. Para más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Para que `toupper` produzca los resultados esperados, [__isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) e [isupper](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) deben devolver un valor distinto de cero.  
  
 [Rutinas de conversión de datos](../../c-runtime-library/data-conversion.md)  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_totupper`|`toupper`|`_mbctoupper`|`towupper`|  
|`_totupper_l`|`_toupper_l`|`_mbctoupper_l`|`_towupper_l`|  
  
> [!NOTE]
>  `_toupper_l` y `_towupper_l` no dependen de la configuración regional y no están diseñadas para llamarlas directamente. Se proporcionan solo para el uso interno por parte de `_totupper_l`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`toupper`|\<ctype.h>|  
|`_toupper`|\<ctype.h>|  
|`towupper`|\<ctype.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [to (Funciones)](../../c-runtime-library/to-functions.md).  
  
## <a name="see-also"></a>Vea también  
 [is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)   
 [to (Funciones)](../../c-runtime-library/to-functions.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)
