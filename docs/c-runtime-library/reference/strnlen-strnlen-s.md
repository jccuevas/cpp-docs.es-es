---
title: strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
dev_langs:
- C++
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
caps.latest.revision: 35
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: f7cba068af7ec6f14970d174d2b3e9b4121d7c40
ms.lasthandoff: 02/24/2017

---
# <a name="strnlen-strnlens-wcsnlen-wcsnlens-mbsnlen-mbsnlenl-mbstrnlen-mbstrnlenl"></a>strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l
Obtiene la longitud de una cadena usando la configuración regional actual o una que se haya pasado. Se trata de versiones más seguras de [strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).  
  
> [!IMPORTANT]
>  `_mbsnlen`, `_mbsnlen_l`, `_mbstrnlen` y `_mbstrnlen_l` no se pueden usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t strnlen(  
   const char *str,  
   size_t numberOfElements   
);  
size_t strnlen_s(  
   const char *str,  
   size_t numberOfElements   
);  
size_t wcsnlen(  
   const wchar_t *str,  
   size_t numberOfElements  
);  
size_t wcsnlen_s(  
   const wchar_t *str,  
   size_t numberOfElements  
);  
size_t _mbsnlen(  
   const unsigned char *str,  
   size_t numberOfElements  
);  
size_t _mbsnlen_l(  
   const unsigned char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
size_t _mbstrnlen(  
   const char *str,  
   size_t numberOfElements  
);  
size_t _mbstrnlen_l(  
   const char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `str`  
 Cadena terminada en un valor nulo.  
  
 `numberOfElements`  
 Tamaño del búfer de cadena.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Estas funciones devuelven el número de caracteres de la cadena, sin incluir el carácter null de terminación. Si no hay un carácter de terminación null en los primeros `numberOfElements` bytes de la cadena (o caracteres anchos, en el caso de `wcsnlen`), se devuelve `numberOfElements` para indicar que existe una situación de error. Las cadenas acabadas en null tienen longitudes estrictamente inferiores a `numberOfElements`.  
  
 `_mbstrnlen` y `_mbstrnlen_l` devuelven -1 si la cadena contiene un carácter multibyte no válido.  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  `strnlen` no reemplaza a `strlen`; `strnlen` está pensado para usarse únicamente para calcular el tamaño de los datos entrantes que no son de confianza en un búfer con un tamaño conocido (por ejemplo, un paquete de red). `strnlen` calcula la longitud, pero no traspasa el final del búfer si la cadena está sin terminar. Para otras situaciones, vea `strlen`. (Esto mismo es válido para `wcsnlen`, `_mbsnlen` y `_mbstrnlen`).  
  
 Cada una de estas funciones devuelve el número de caracteres en `str`, sin incluir el carácter null de terminación. Con todo, `strnlen` y `strnlen_s` interpretan la cadena como una cadena de caracteres de un solo byte, de modo que el valor devuelto siempre es igual al número de bytes, incluso si la cadena contiene caracteres multibyte. `wcsnlen` y `wcsnlen_s` son las versiones con caracteres anchos de `strnlen` y `strnlen_s` respectivamente; los argumentos de `wcsnlen` y `wcsnlen_s` son cadenas de caracteres anchos y, como tal, el recuento de caracteres se muestra en unidades de caracteres anchos. De lo contrario, `wcsnlen` y `strnlen` se comportan de forma idéntica, al igual que `strnlen_s` y `wcsnlen_s`.  
  
 `strnlen`, `wcsnlen,` y `_mbsnlen` no validan sus parámetros. Si `str` es `NULL`, se produce una infracción de acceso.  
  
 `strnlen_s` y `wcsnlen_s` validan sus parámetros. Si `str` es `NULL`, las funciones devuelven 0.  
  
 `_mbstrnlen` también valida sus parámetros. Si `str` es `NULL`, o si `numberOfElements` es mayor que `INT_MAX`, `_mbstrnlen` genera una excepción de parámetro no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `_mbstrnlen` establece `errno` en `EINVAL` y devuelve -1.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsnlen`|`strnlen`|`strnlen`|`wcsnlen`|  
|`_tcscnlen`|`strnlen`|`_mbsnlen`|`wcsnlen`|  
|`_tcscnlen_l`|`strnlen`|`_mbsnlen_l`|`wcsnlen`|  
  
 `_mbsnlen` y `_mbstrnlen` devuelven el número de caracteres multibyte en una cadena de caracteres multibyte. `_mbsnlen` reconoce secuencias de caracteres multibyte en función de la página de códigos multibyte que se usa actualmente o según la configuración regional que se haya pasado. No comprueba la validez de los caracteres multibyte. `_mbstrnlen` comprueba la validez de los caracteres multibyte y reconoce secuencias de caracteres multibyte. Si la cadena que se pasa a `_mbstrnlen` contiene un carácter multibyte no válido, `errno` se establece en `EILSEQ`.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones son idénticas, salvo por el hecho de que las que no tienen el sufijo `_l` usan la configuración regional actual cuando el comportamiento depende de la configuración regional, y las que tienen el sufijo `_l` usan en su lugar el parámetro de configuración regional que se ha pasado. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`strnlen`, `strnlen_s`|\<string.h>|  
|`wcsnlen`, `wcsnlen_s`|\<string.h> o \<wchar.h>|  
|`_mbsnlen`, `_mbsnlen_l`|\<mbstring.h>|  
|`_mbstrnlen`, `_mbstrnlen_l`|\<stdlib.h>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
  
      // crt_strnlen.c  
  
#include <string.h>  
  
int main()  
{  
   // str1 is 82 characters long. str2 is 159 characters long   
  
   char* str1 = "The length of a string is the number of characters\n"  
               "excluding the terminating null.";  
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"  
                "than the maximum size specified, the maximum size is\n"  
                "returned rather than the actual size of the string.";  
   size_t len;  
   size_t maxsize = 100;  
  
   len = strnlen(str1, maxsize);  
   printf("%s\n Length: %d \n\n", str1, len);  
  
   len = strnlen(str2, maxsize);  
   printf("%s\n Length: %d \n", str2, len);  
}  
```  
  
```Output  
The length of a string is the number of characters  
excluding the terminating null.  
 Length: 82   
  
strnlen takes a maximum size. If the string is longer  
than the maximum size specified, the maximum size is  
returned rather than the actual size of the string.  
 Length: 100   
```  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 [System::String::Length](https://msdn.microsoft.com/en-us/library/system.string.length.aspx)  
  
## <a name="see-also"></a>Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strcoll (Funciones)](../../c-runtime-library/strcoll-functions.md)   
 [strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)
