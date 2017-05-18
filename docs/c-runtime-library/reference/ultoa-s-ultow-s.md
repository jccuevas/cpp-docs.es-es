---
title: _ultoa_s, _ultow_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ultow_s
- _ultoa_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ultow_s
- ultoa_s
- ultow_s
- _ultoa_s
dev_langs:
- C++
helpviewer_keywords:
- _ultoa_s function
- converting integers
- integers, converting
- _ultow_s function
- ultoa_s function
- converting numbers, to strings
- ultow_s function
ms.assetid: 606ce905-6752-46ac-a15a-bdc22920e1d4
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: f35701cf1ef644b140cae01ef2d8707cfb387a68
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="ultoas-ultows"></a>_ultoa_s, _ultow_s
Convierte un entero largo sin signo en una cadena. Estas son versiones de [_ultoa, _ultow](../../c-runtime-library/reference/ultoa-ultow.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t _ultoa_s(  
    unsigned long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ultow_s(  
    unsigned long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ultoa_s(  
    unsigned long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ultow_s(  
    unsigned long value,  
    wchar_t (&str)[size],  
    int radix   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value`  
 Número que se va a convertir.  
  
 `str`  
 Cadena de resultado.  
  
 `sizeOfstr`  
 Tamaño de `str` en bytes para `_ultoa_s` o en palabras para `_ultow_s`.  
  
 `radix`  
 Base de `value`.  
  
## <a name="return-value"></a>Valor devuelto  
 Cero si la función se realizó correctamente o si fue un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La función `_ultoa_s` convierte los dígitos de `value` en una cadena de caracteres terminada en un valor nulo y almacena el resultado (hasta 33 bytes) en `str`. El `radix` especifica el argumento de la base de `value`, que debe estar comprendido entre 2 y 36. `_ultow_s` es una versión con caracteres anchos de `_ultoa_s`; el segundo argumento de `_ultow_s` es una cadena de caracteres anchos.  
  
 Si `str` es un puntero `NULL` o `sizeOfstr` es menor o igual que cero, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen `errno` en `EINVAL`; si `value` o `str` están fuera del intervalo de un entero largo, estas funciones devuelven -1 y establecen `errno` en `ERANGE`.  
  
 En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ultot_s`|`_ultoa_s`|`_ultoa_s`|`_ultow_s`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_ultoa_s`|\<stdlib.h>|  
|`_ultow_s`|\<stdlib.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [_ultoa, _ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [_ltoa, _ltow](../../c-runtime-library/reference/ltoa-ltow.md)   
 [_ltoa_s, _ltow_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)   
 [_ltoa_s, _ltow_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)
