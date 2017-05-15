---
title: getenv_s, _wgetenv_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- getenv_s
- _wgetenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- getenv_s
- _tgetenv_s
- _wgetenv_s
dev_langs:
- C++
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
caps.latest.revision: 42
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
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: de79cb66e33564f321dd3277528d67a8d7e0ddc0
ms.contentlocale: es-es
ms.lasthandoff: 02/28/2017

---
# <a name="getenvs-wgetenvs"></a>getenv_s, _wgetenv_s
Obtiene un valor del entorno actual. Estas versiones de [getenv, _wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md) incluyen mejoras de seguridad, tal como se describe en [Características de seguridad en CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t getenv_s(   
   size_t *pReturnValue,  
   char* buffer,  
   size_t numberOfElements,  
   const char *varname   
);  
errno_t _wgetenv_s(   
   size_t *pReturnValue,  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *varname   
);  
template <size_t size>  
errno_t getenv_s(   
   size_t *pReturnValue,  
   char (&buffer)[size],  
   const char *varname   
); // C++ only  
template <size_t size>  
errno_t _wgetenv_s(   
   size_t *pReturnValue,  
   wchar_t (&buffer)[size],  
   const wchar_t *varname   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pReturnValue`  
 El tamaño del búfer necesario o 0 si no se encuentra la variable.  
  
 `buffer`  
 El búfer para almacenar el valor de la variable de entorno.  
  
 `numberOfElements`  
 Tamaño de `buffer`.  
  
 `varname`  
 Nombre de la variable de entorno.  
  
## <a name="return-value"></a>Valor devuelto  
 Cero si es correcto; en caso contrario, un código de error si se produce un error.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`pReturnValue`|`buffer`|`numberOfElements`|`varname`|Valor devuelto|  
|--------------------|--------------|------------------------|---------------|------------------|  
|`NULL`|cualquiera|cualquiera|cualquiera|`EINVAL`|  
|cualquiera|`NULL`|>0|cualquiera|`EINVAL`|  
|cualquiera|cualquiera|cualquiera|`NULL`|`EINVAL`|  
  
 Cualquiera de estas condiciones de error invoca un controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
 Además, si el búfer es demasiado pequeño, estas funciones devuelven `ERANGE`. No invocan un controlador de parámetros no válido. Escriben el tamaño de búfer necesario en `pReturnValue` y, de esta forma, permite a los programas llamar a la función con un búfer mayor.  
  
## <a name="remarks"></a>Comentarios  
 La función `getenv_s` busca `varname` en la lista de variables de entorno. `getenv_s` no distingue entre mayúsculas y minúsculas en el sistema operativo Windows. `getenv_s` y `_putenv_s` usan la copia del entorno indicada por la variable global `_environ` para tener acceso al entorno. `getenv_s` solo funciona en las estructuras de datos a las que puede tener acceso la biblioteca en tiempo de ejecución y no en el “segmento” del entorno que el sistema operativo crea para el proceso. En consecuencia, los programas que usan el argumento `envp` en [main](../../cpp/main-program-startup.md) o [wmain](../../cpp/main-program-startup.md) podrían recuperar información no válida.  
  
 `_wgetenv_s` es una versión con caracteres anchos de `getenv_s`; el argumento y el valor devuelto de `_wgetenv_s` son cadenas de caracteres anchos. La variable global `_wenviron` es una versión con caracteres anchos de `_environ`.  
  
 En un programa de MBCS (por ejemplo, en un programa ASCII de SBCS), `_wenviron` es inicialmente `NULL` porque el entorno está formado por cadenas de caracteres multibyte. Después, en la primera llamada a `_wputenv`, o en la primera llamada a `_wgetenv_s`, si ya existe un entorno (MBCS), se crea un entorno de cadenas de caracteres anchos correspondiente, al que señala `_wenviron`.  
  
 De la misma forma, en un programa de Unicode (`(_wmain`), `_environ` es inicialmente `NULL` porque el entorno está formado por cadenas de caracteres anchos. Después, en la primera llamada a `_putenv`, o en la primera llamada a `getenv_s` si ya existe un entorno (Unicode), se crea un entorno de MBCS correspondiente, al que señala `_environ`.  
  
 Si dos copias del entorno (MBCS y Unicode) existen simultáneamente en un programa, el sistema en tiempo de ejecución debe mantener las dos copias, lo que ralentiza el tiempo de ejecución. Por ejemplo, cuando se llame a `_putenv`, se ejecuta automáticamente una llamada a `_wputenv`, de forma que se correspondan las dos cadenas de entorno.  
  
> [!CAUTION]
>  En raras ocasiones, cuando el sistema en tiempo de ejecución mantiene una versión Unicode y una versión multibyte del entorno, las dos versiones del entorno podrían no corresponderse exactamente. La razón es que, aunque cualquier cadena de caracteres multibyte se asigna a una cadena de Unicode única, la asignación de una cadena de Unicode única a una cadena de caracteres multibyte no es necesariamente única. Para obtener más información, vea [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).  
  
> [!NOTE]
>  Los grupos de funciones de `_putenv_s` y `_getenv_s` no son seguros para subprocesos. `_getenv_s` podría devolver un puntero de cadena mientras `_putenv_s` modifica la cadena y, por lo tanto, generarían errores aleatorios. Asegúrese de que las llamadas a estas funciones están sincronizadas.  
  
 En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir automáticamente la longitud del búfer, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tgetenv_s`|`getenv_s`|`getenv_s`|`_wgetenv_s`|  
  
 Para comprobar o cambiar el valor de la variable de entorno `TZ`, use `getenv_s`, `_putenv` y `_tzset` según sea necesario. Para obtener más información sobre `TZ`, vea [_tzset](../../c-runtime-library/reference/tzset.md) y [_daylight, _dstbias, _timezone y _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`getenv_s`|\<stdlib.h>|  
|`_wgetenv_s`|\<stdlib.h> o \<wchar.h>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```C  
// crt_getenv_s.c  
// This program uses getenv_s to retrieve  
// the LIB environment variable and then uses  
// _putenv to change it to a new value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* libvar;  
   size_t requiredSize;  
  
   getenv_s( &requiredSize, NULL, 0, "LIB");  
   if (requiredSize == 0)  
   {  
      printf("LIB doesn't exist!\n");  
      exit(1);  
   }  
  
   libvar = (char*) malloc(requiredSize * sizeof(char));  
   if (!libvar)  
   {  
      printf("Failed to allocate memory!\n");  
      exit(1);  
   }  
  
   // Get the value of the LIB environment variable.  
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );  
  
   printf( "Original LIB variable is: %s\n", libvar );  
  
   // Attempt to change path. Note that this only affects  
   // the environment variable of the current process. The command  
   // processor's environment is not changed.  
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );  
  
   getenv_s( &requiredSize, NULL, 0, "LIB");  
  
   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));  
   if (!libvar)  
   {  
      printf("Failed to allocate memory!\n");  
      exit(1);  
   }  
  
   // Get the new value of the LIB environment variable.   
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );  
  
   printf( "New LIB variable is: %s\n", libvar );  
  
   free(libvar);  
}  
```  
  
```Output  
Original LIB variable is: c:\vctools\lib;c:\vctools\atlmfc\lib;c:\vctools\PlatformSDK\lib;c:\vctools\Visual Studio SDKs\DIA Sdk\lib;c:\vctools\Visual Studio SDKs\BSC Sdk\lib  
New LIB variable is: c:\mylib;c:\yourlib  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [Constantes de entorno](../../c-runtime-library/environmental-constants.md)   
 [_putenv, _wputenv](../../c-runtime-library/reference/putenv-wputenv.md)   
 [_dupenv_s, _wdupenv_s](../../c-runtime-library/reference/dupenv-s-wdupenv-s.md)
