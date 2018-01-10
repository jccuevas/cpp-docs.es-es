---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
dev_langs: C++
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 97c6f5f4c827ca315eb1de36ee8d4f19d94214bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ctime-ctime32-ctime64-wctime-wctime32-wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
Convierte un valor de hora en cadena y lo ajusta según la configuración de zona horaria local. Hay disponibles versiones más seguras de estas funciones; consulte [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
char *ctime(   
   const time_t *timer   
);  
char *_ctime32(   
   const __time32_t *timer )  
;  
char *_ctime64(   
   const __time64_t *timer )  
;  
wchar_t *_wctime(   
   const time_t *timer   
);  
wchar_t *_wctime32(   
   const __time32_t *timer  
);  
wchar_t *_wctime64(   
   const __time64_t *timer   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `timer`  
 Puntero a la hora almacenada.  
  
## <a name="return-value"></a>Valor devuelto  
 Puntero al resultado de la cadena de caracteres. Se devuelve `NULL` si:  
  
-   `time` representa una fecha anterior a la medianoche del 1 de enero de 1970, UTC.  
  
-   Se usa `_ctime32` o `_wctime32`, y `time` representa una fecha posterior a las 23:59:59 horas del 18 de enero de 2038, UTC.  
  
-   Se usa `_ctime64` o `_wctime64`, y `time` representa una fecha posterior a las 23:59:59 horas del 31 de diciembre de 3000, UTC.  
  
 `ctime` es una función insertada que se evalúa como `_ctime64`, y `time_t` es equivalente a `__time64_t`. Si necesita forzar el compilador para interpretar `time_t` como el antiguo `time_t` de 32 bits, puede definir `_USE_32BIT_TIME_T`. Al hacerlo, `ctime` se evaluará como `_ctime32`. Esto no es recomendable porque puede producir un error en la aplicación después del 18 de enero de 2038 y no se permite en plataformas de 64 bits.  
  
## <a name="remarks"></a>Comentarios  
 La función `ctime` convierte un valor de tiempo almacenado como valor [time_t](../../c-runtime-library/standard-types.md) en una cadena de caracteres. El valor `timer` suele obtenerse de una llamada a [time](../../c-runtime-library/reference/time-time32-time64.md), que devuelve el número de segundos transcurridos desde la medianoche (00:00:00) del 1 de enero de 1970, hora universal coordinada (UTC). La cadena del valor devuelto contiene exactamente 26 caracteres y tiene el formato:  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 Se usa un reloj de 24 horas. Todos los campos tienen un ancho constante. El carácter de nueva línea ("\n") y el carácter nulo ("\0") ocupan las dos últimas posiciones de la cadena.  
  
 La cadena de caracteres convertidos también se ajusta en función de la configuración de zona horaria local. Consulte las funciones `time`, [_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) y [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) para obtener información sobre cómo configurar la hora local; consulte la función [_tzset](../../c-runtime-library/reference/tzset.md) para obtener información sobre cómo definir el entorno de zona horaria y las variables globales.  
  
 Una llamada a `ctime` modifica el búfer único asignado estáticamente que usan las funciones `gmtime` y `localtime`. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior. `ctime` comparte un búfer estático con la función `asctime`. Por lo tanto, una llamada a `ctime` destruye los resultados de las llamadas anteriores a `asctime`, `localtime` o `gmtime`.  
  
 `_wctime` y `_wctime64` son las versiones de caracteres anchos de `ctime` y `_ctime64`; devuelven un puntero a una cadena de caracteres anchos. De lo contrario, `_ctime64`, `_wctime` y `_wctime64` se comportan exactamente igual que `ctime`.  
  
 Estas funciones validan sus parámetros. Si `timer` es un puntero nulo, o si el valor del temporizador es negativo, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven `NULL` y establecen `errno` en `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tctime`|`ctime`|`ctime`|`_wctime`|  
|`_tctime32`|`_ctime32`|`_ctime32`|`_wctime32`|  
|`_tctime64`|`_ctime64`|`_ctime64`|`_wctime64`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`ctime`|\<time.h>|  
|`_ctime32`|\<time.h>|  
|`_ctime64`|\<time.h>|  
|`_wctime`|\<time.h> o \<wchar.h>|  
|`_wctime32`|\<time.h> o \<wchar.h>|  
|`_wctime64`|\<time.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_ctime64.c  
// compile with: /W3  
/* This program gets the current  
 * time in _time64_t form, then uses ctime to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   __time64_t ltime;  
  
   _time64( &ltime );  
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996  
   // Note: _ctime64 is deprecated; consider using _ctime64_s  
}  
```  
  
```Output  
The time is Wed Feb 13 16:04:43 2002  
```  
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)