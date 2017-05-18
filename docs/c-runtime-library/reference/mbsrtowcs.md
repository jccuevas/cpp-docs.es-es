---
title: mbsrtowcs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- mbsrtowcs
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
- mbsrtowcs
dev_langs:
- C++
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
caps.latest.revision: 20
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
ms.openlocfilehash: bec54ca0efe0f8aefabbe0c616e283b64fd22166
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="mbsrtowcs"></a>mbsrtowcs
Convierte una cadena de caracteres multibyte en la configuración regional actual en una cadena de caracteres anchos correspondiente, con la capacidad de reinicio en medio de un carácter multibyte. Hay disponible una versión más segura de esta función; vea [mbsrtowcs_s](../../c-runtime-library/reference/mbsrtowcs-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t mbsrtowcs(  
   wchar_t *wcstr,  
   const char **mbstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t mbsrtowcs(  
   wchar_t (&wcstr)[size],  
   const char **mbstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `wcstr`  
 Dirección para almacenar la cadena de caracteres anchos convertida.  
  
 [in, out] `mbstr`  
 Puntero indirecto a la ubicación de la cadena de caracteres multibyte a convertir.  
  
 [in] `count`  
 Número máximo de caracteres (no bytes) a convertir y almacenar en `wcstr`.  
  
 [in, out] `mbstate`  
 Un puntero a un objeto `mbstate_t` de estado de la conversión. Si este valor es un puntero nulo, se utiliza un objeto de estado de la conversión interno estático. Dado que el objeto `mbstate_t` interno no es seguro para subprocesos, se recomienda pasar siempre su propio parámetro `mbstate`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el número de caracteres convertidos correctamente, sin incluir el carácter nulo de terminación, de haberlo. Devuelve (size_t)(-1) si se produce un error y establece `errno` a EILSEQ.  
  
## <a name="remarks"></a>Comentarios  
 La función `mbsrtowcs` convierte una cadena de caracteres multibyte indirectamente señalada por `mbstr` en caracteres anchos almacenados en el búfer señalado por `wcstr`, utilizando el estado de conversión contenido en `mbstate`. La conversión continúa para cada carácter hasta que se encuentra un carácter multibyte nulo de terminación, se encuentra una secuencia multibyte que no se corresponde con un carácter válido en la configuración regional actual, o se convierten `count` caracteres. Si `mbsrtowcs` encuentra el carácter multibyte nulo ('\0') antes o al producirse `count`, lo convierte en un carácter nulo de terminación de 16 bits y se detiene.  
  
 Por tanto, la cadena de caracteres anchos en `wcstr` tiene terminación nula solo si `mbsrtowcs` encuentra un carácter multibyte nulo durante la conversión. Si las secuencias señaladas por `mbstr` y `wcstr` se superponen, el comportamiento de `mbsrtowcs` no está definido. `mbsrtowcs` se ve afectado por la categoría LC_TYPE de la configuración regional actual.  
  
 La función `mbsrtowcs` difiere de [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) en que se puede reiniciar. El estado de la conversión se almacena en `mbstate` para llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación debe utilizar `mbsrlen` en lugar de `mbslen` si se utiliza una llamada subsiguiente a `mbsrtowcs` en lugar de a `mbstowcs.`  
  
 Si `wcstr` no es un puntero nulo, al objeto de puntero señalado por `mbstr` se le asigna un puntero nulo si la conversión se detuvo por encontrarse un carácter nulo de terminación. De lo contrario, se le asigna la dirección inmediatamente posterior al último carácter multibyte convertido, de haberlo. Esto permite que una llamada de función subsiguiente reinicie la conversión en el punto en que se detuvo esta llamada.  
  
 Si el argumento `wcstr` es un puntero nulo, el argumento `count` se omite y `mbsrtowcs` devuelve el tamaño requerido en caracteres anchos para la cadena de destino. Si `mbstate` es un puntero nulo, la función usa un objeto de estado de la conversión `mbstate_t` interno estático, no seguro para subprocesos. Si la secuencia de caracteres `mbstr` no tiene una representación de caracteres multibyte correspondiente, se devuelve el valor -1 y `errno` se establece a `EILSEQ`.  
  
 Si `mbstr` es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece `errno` en `EINVAL` y devuelve -1.  
  
 En C++, esta función tiene una sobrecarga de plantilla que invoca una contrapartida más nueva y segura de la función. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Excepciones  
 La función `mbsrtowcs` es segura para subprocesos siempre y cuando ninguna función en el proceso actual llame a `setlocale`, mientras se ejecute esta función y el argumento `mbstate` no sea un puntero nulo.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`mbsrtowcs`|\<wchar.h>|  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtowc](../../c-runtime-library/reference/mbrtowc.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
