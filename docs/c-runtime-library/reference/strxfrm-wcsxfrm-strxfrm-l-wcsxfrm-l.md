---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- strxfrm
- _tcsxfrm
- wcsxfrm
dev_langs:
- C++
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
caps.latest.revision: 18
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: b05ec00ae2144670844cd54de0900aa1412128ff
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
Transforma una cadena en función de la información específica de la configuración regional.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t strxfrm(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
size_t wcsxfrm(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
size_t _strxfrm_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
size_t wcsxfrm_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `strDest`  
 Cadena de destino.  
  
 `strSource`  
 Cadena de origen.  
  
 `count`  
 Número máximo de caracteres que se va a colocar en `strDest`.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve la longitud de la cadena transformada, sin contar el carácter nulo de terminación. Si el valor devuelto es mayor o igual a `count`, el contenido de `strDest` es imprevisible. Si se produce un error, cada función establece `errno` y devuelve `INT_MAX`. Para un carácter no válido, `errno` se establece en `EILSEQ`.  
  
## <a name="remarks"></a>Comentarios  
 La función `strxfrm` transforma la cadena señalada por `strSource` en un nuevo formulario intercalado que se almacena en `strDest`. En la cadena resultante no se transforman ni colocan más de `count` caracteres (incluido el carácter nulo). La transformación se efectúa con el valor de la categoría `LC_COLLATE` de la configuración regional. Para obtener más información sobre `LC_COLLATE`, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). `strxfrm` usa la configuración regional actual para el comportamiento dependiente de la configuración regional; `_strxfrm_l` es idéntico, salvo que usa la configuración regional que se pasa en lugar de usar la configuración regional actual. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Después de la transformación, si se efectúa una llamada a `strcmp` con las dos cadenas transformadas, se generarán unos resultados idénticos a los que se generarían en una llamada a `strcoll` aplicada a las dos cadenas originales. Al igual que con `strcoll` y `stricoll`, `strxfrm` controla automáticamente las cadenas de caracteres multibyte según corresponda.  
  
 `wcsxfrm` es una versión con caracteres anchos de `strxfrm`; los argumentos de cadena de `wcsxfrm` son punteros con caracteres anchos. Para `wcsxfrm`, después de la transformación de la cadena, si se efectúa una llamada a `wcscmp` con las dos cadenas transformadas, se generarán unos resultados idénticos a los que se generarían en una llamada a `wcscoll` aplicada a las dos cadenas originales. Por lo demás, `wcsxfrm` y `strxfrm` se comportan de forma idéntica. `wcsxfrm` usa la configuración regional actual para el comportamiento dependiente de la configuración regional; `_wcsxfrm_l` usa la configuración regional que se pasa en lugar de usar la configuración regional actual.  
  
 Estas funciones validan sus parámetros. Si `strSource` es un puntero nulo, si `strDest` es un puntero NULL (a menos que el recuento sea cero) o si `count` es mayor que `INT_MAX`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `INT_MAX`.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsxfrm`|`strxfrm`|`strxfrm`|`wcsxfrm`|  
|`_tcsxfrm_l`|`_strxfrm_l`|`_strxfrm_l`|`_wcsxfrm_l`|  
  
 En la configuración regional "C", el orden de los caracteres del juego de caracteres (juego de caracteres ASCII) es el mismo que el orden lexicográfico de los caracteres. Sin embargo, en otras configuraciones regionales, el orden de los caracteres del juego de caracteres puede diferir del orden lexicográfico de los caracteres. Por ejemplo, en algunas configuraciones regionales europeas, el carácter “a” (valor 0x61) precede al carácter “&\#x00E4;” (valor 0xE4) en el juego de caracteres, pero el carácter “ä” precede al carácter “a” lexicográficamente.  
  
 En las configuraciones regionales en las que el juego de caracteres y el orden de los caracteres lexicográficos son distintos, use `strxfrm` en las cadenas originales y `strcmp` en las cadenas resultantes para generar una comparación de cadenas lexicográfica de acuerdo con el valor de la categoría `LC_COLLATE` de la configuración regional actual. Por lo tanto, para comparar dos cadenas de manera lexicográfica en la configuración regional anterior, use `strxfrm` en las cadenas originales y, luego, `strcmp` en las cadenas resultantes. Como alternativa, puede usar `strcoll` en lugar de `strcmp` en las cadenas originales.  
  
 Básicamente, `strxfrm` es un contenedor situado alrededor de [LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700) con `LCMAP_SORTKEY`.  
  
 El valor de la siguiente expresión es el tamaño de la matriz necesario para albergar la transformación `strxfrm` de la cadena de origen:  
  
```  
1 + strxfrm( NULL, string, 0 )  
```  
  
 Únicamente para la configuración regional de "C", `strxfrm` equivale a lo siguiente:  
  
```  
strncpy( _string1, _string2, _count );  
return( strlen( _string1 ) );  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`strxfrm`|\<string.h>|  
|`wcsxfrm`|\<string.h> o \<wchar.h>|  
|`_strxfrm_l`|\<string.h>|  
|`_wcsxfrm_l`|\<string.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll (Funciones)](../../c-runtime-library/strcoll-functions.md)   
 [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)
