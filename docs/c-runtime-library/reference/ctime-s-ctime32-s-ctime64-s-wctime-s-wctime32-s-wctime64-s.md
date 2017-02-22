---
title: "ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ctime64_s"
  - "_wctime32_s"
  - "ctime_s"
  - "_wctime64_s"
  - "_ctime32_s"
  - "_wctime_s"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "ctime64_s"
  - "_ctime32_s"
  - "_tctime32_s"
  - "_ctime64_s"
  - "_wctime_s"
  - "_tctime_s"
  - "_tctime64_s"
  - "ctime_s"
  - "ctime32_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_wctime32_s (función)"
  - "ctime64_s (función)"
  - "_tctime64_s (función)"
  - "_wctime_s (función)"
  - "tctime_s (función)"
  - "_wctime64_s (función)"
  - "ctime_s (función)"
  - "ctime32_s (función)"
  - "_ctime64_s (función)"
  - "tctime64_s (función)"
  - "wctime64_s (función)"
  - "wctime_s (función)"
  - "_tctime_s (función)"
  - "tctime32_s (función)"
  - "wctime32_s (función)"
  - "hora, convertir"
  - "_ctime32_s (función)"
  - "_tctime32_s (función)"
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convertir un valor de hora en una cadena y ajustar la configuración de la zona horaria local. Estas son versiones de [ctime, \_ctime64, \_wctime, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t ctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _ctime32_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _ctime64_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time64_t *time )  
;  
errno_t _wctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _wctime32_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _wctime64_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time64_t *time   
);  
template <size_t size>  
errno_t _ctime32_s(   
   char (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _ctime64_s(   
   char (&buffer)[size],  
   const __time64_t *time  
); // C++ only  
template <size_t size>  
errno_t _wctime32_s(   
   wchar_t (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _wctime64_s(   
   wchar_t (&buffer)[size],  
   const __time64_t *time   
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `buffer`  
 Debe ser lo suficientemente grande como para contener 26 caracteres. Un puntero al resultado de la cadena de caracteres, o `NULL`si:  
  
-   `time` Representa una fecha anterior a la medianoche del 1 de enero de 1970 UTC.  
  
-   Si utiliza `_ctime32_s` o `_wctime32_s` y `time` representa una fecha posterior a las 23:59:59 del 18 de enero de 2038, hora UTC.  
  
-   Si utiliza `_ctime64_s` o `_wctime64_s` y `time` representa una fecha posterior a las 23:59:59 del 31 de diciembre de 3000, UTC.  
  
-   Si utiliza `_ctime_s` o `_wctime_s`, estas funciones son contenedores para las funciones anteriores. Vea la sección Comentarios.  
  
 \[in\] `numberOfElements`  
 Tamaño del búfer.  
  
 \[in\] t`ime`  
 Puntero a la hora almacenada.  
  
## Valor devuelto  
 Cero si es correcta. Si se produce un error debido a un parámetro no válido, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, se devuelve un código de error. Códigos de error se definen en ERRNO. H; Para obtener una lista de estos errores, vea [errno](../../c-runtime-library/errno-constants.md). Los códigos de error real se produce para cada condición de error se muestran en la tabla siguiente.  
  
## Condiciones de error  
  
|`buffer`|`numberOfElements`|`time`|Volver|Valor de `buffer`|  
|--------------|------------------------|------------|------------|-----------------------|  
|`NULL`|any|any|`EINVAL`|No modificado|  
|No `NULL` \(puntos de memoria válida\)|0|any|`EINVAL`|No modificado|  
|No `NULL`|0 \< tamaño \< 26|any|`EINVAL`|Cadena vacía|  
|No `NULL`|\>\= 26|NULL|`EINVAL`|Cadena vacía|  
|No `NULL`|\>\= 26|\< 0|`EINVAL`|Cadena vacía|  
  
## Comentarios  
 El `ctime_s` función convierte un valor de hora almacenado como un [time\_t](../../c-runtime-library/standard-types.md) estructura en una cadena de caracteres. El `time` valor suele obtenerse a partir de una llamada a [tiempo](../../c-runtime-library/reference/time-time32-time64.md), que devuelve el número de segundos transcurrido desde la medianoche \(00: 00:00\) del 1 de enero de 1970, hora universal coordinada \(UTC\). La cadena del valor devuelto contiene exactamente 26 caracteres y tiene el formato:  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 Se utiliza un reloj de 24 horas. Todos los campos tienen un ancho constante. El carácter de nueva línea \('\\n'\) y el carácter nulo \('\\0'\) ocupan las dos últimas posiciones de la cadena.  
  
 La cadena de caracteres convertidos también se ajusta según la configuración de zona horaria local. Consulte la `time`, [\_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), y [localtime32\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) funciones para obtener información acerca de cómo configurar la hora local y la [\_tzset](../../c-runtime-library/reference/tzset.md) \(función\) para obtener información acerca de cómo definir el entorno de zona horaria y variables globales.  
  
 `_wctime32_s` y `_wctime64_s` son la versión de caracteres anchos de `_ctime32_s` y `_ctime64_s`; devuelve un puntero a la cadena de caracteres anchos. De lo contrario, `_ctime64_s`, `_wctime32_s`, y `_wctime64_s` se comportan exactamente igual a `_ctime32_s`.  
  
 `ctime_s` es una función insertada que se evalúa como `_ctime64_s` y `time_t` es equivalente a `__time64_t`. Si necesita forzar el compilador para interpretar `time_t` como el antiguo `time_t` de 32 bits, puede definir `_USE_32BIT_TIME_T`. Hacer esto hará que `ctime_s` se evalúe como `_ctime32_s`. Esto no se recomienda porque puede producir un error de la aplicación después del 18 de enero de 2038, y no se permite en plataformas de 64 bits.  
  
 En C\+\+, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulta [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tctime_s`|`ctime_s`|`ctime_s`|`_wctime_s`|  
|`_tctime32_s`|`_ctime32_s`|`_ctime32_s`|`_wctime32_s`|  
|`_tctime64_s`|`_ctime64_s`|`_ctime64_s`|`_wctime64_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`ctime_s,`<br /><br /> `_ctime32_s,`<br /><br /> `_ctime64_s`|\<time.h\>|  
|`_wctime_s,`<br /><br /> `_wctime32_s,`<br /><br /> `_wctime64_s`|\< time.h \> o \< wchar.h \>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_wctime_s.c  
/* This program gets the current  
 * time in time_t form and then uses _wctime_s to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
#define SIZE 26  
  
int main( void )  
{  
   time_t ltime;  
   wchar_t buf[SIZE];  
   errno_t err;  
  
   time( &ltime );  
  
   err = _wctime_s( buf, SIZE, &ltime );  
   if (err != 0)  
   {  
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);  
   }  
   wprintf_s( L"The time is %s\n", buf );  
}  
```  
  
## Resultados del ejemplo  
  
```  
The time is Fri Apr 25 13:03:39 2003  
```  
  
## Equivalente en .NET Framework  
  
-   [System::DateTime::GetDateTimeFormats](https://msdn.microsoft.com/en-us/library/system.datetime.getdatetimeformats.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime\_s, \_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s, \_gmtime32\_s, \_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)