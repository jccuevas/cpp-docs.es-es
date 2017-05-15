---
title: mbstowcs_s, _mbstowcs_s_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- _mbstowcs_s_l
- mbstowcs_s
dev_langs:
- C++
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
caps.latest.revision: 31
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 8858827e65ad342f2c48dba26b3be7f7f9dd2ca3
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s, _mbstowcs_s_l
Convertir una secuencia de caracteres multibyte en una secuencia correspondiente de caracteres anchos. Versiones de [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count   
);  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `pReturnValue`  
 El número de caracteres convertidos.  
  
 [out] `wcstr`  
 Dirección del búfer para la cadena de caracteres anchos convertida.  
  
 [in] `sizeInWords`  
 Tamaño del búfer `wcstr` en palabras.  
  
 [in]`mbstr`  
 Dirección de una secuencia de caracteres multibyte terminados en nulo.  
  
 [in] `count`  
 Número máximo de caracteres anchos que se va a almacenar en el búfer `wcstr`, sin incluir el terminador nulo, o [_TRUNCATE](../../c-runtime-library/truncate.md).  
  
 [in] `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
|Condición de error|Valor devuelto y `errno`|  
|---------------------|------------------------------|  
|`wcstr` es `NULL` y `sizeInWords` > 0|`EINVAL`|  
|`mbstr` es `NULL`|`EINVAL`|  
|El búfer de destino es demasiado pequeño para contener la cadena convertida (a menos que `count` sea `_TRUNCATE`; vea la sección Comentarios a continuación)|`ERANGE`|  
|`wcstr` no es `NULL` y `sizeInWords` == 0|`EINVAL`|  
  
 Si se produce alguna de estas condiciones, se invoca la excepción de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si se permite que la ejecución continúe, la función devuelve un código de error y establece `errno` como se indica en la tabla.  
  
## <a name="remarks"></a>Comentarios  
 La función `mbstowcs_s` convierte una cadena de caracteres multibyte a la que apunta `mbstr` en caracteres anchos almacenados en el búfer al que apunta `wcstr`. La conversión continuará para cada carácter hasta que se cumpla alguna de estas condiciones:  
  
-   Se encuentra un carácter multibyte nulo  
  
-   Se encuentra un carácter multibyte no válido  
  
-   El número de caracteres anchos almacenados en el búfer `wcstr` es igual a `count`.  
  
 La cadena de destino siempre termina en nulo (aun en caso de error).  
  
 Si `count` es el valor especial [_TRUNCATE](../../c-runtime-library/truncate.md), `mbstowcs_s` convierte la parte de la cadena que quepa en el búfer de destino, dejando espacio para un terminador nulo.  
  
 Si `mbstowcs_s` convierte correctamente la cadena de origen, pone el tamaño en caracteres anchos de la cadena convertida, incluido el terminador nulo, en `*``pReturnValue` (siempre que `pReturnValue` no sea `NULL`). Esto ocurre aunque el argumento `wcstr` sea `NULL` y permite determinar el tamaño de búfer necesario. Observe que, si `wcstr` es `NULL`, se omite `count` y `sizeInWords` debe ser 0.  
  
 Si `mbstowcs_s` encuentra un carácter multibyte no válido, pone 0 en `*``pReturnValue`, establece el búfer de destino en una cadena vacía, establece `errno` en `EILSEQ` y devuelve `EILSEQ`.  
  
 Si las secuencias señaladas por `mbstr` y `wcstr` se superponen, el comportamiento de `mbstowcs_s` no está definido.  
  
> [!IMPORTANT]
>  Asegúrese de que `wcstr` y `mbstr` no se superponen, y de que `count` refleja correctamente el número de caracteres multibyte a convertir.  
  
 `mbstowcs_s` usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional; `_mbstowcs_s_l` es igual, salvo que en su lugar usa la configuración regional pasada. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`mbstowcs_s`|\<stdlib.h>|  
|`_mbstowcs_s_l`|\<stdlib.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs, _wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)
