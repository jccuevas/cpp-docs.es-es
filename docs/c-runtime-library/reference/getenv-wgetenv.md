---
title: "getenv, _wgetenv | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "getenv"
  - "_wgetenv"
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
  - "api-ms-win-crt-environment-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_wgetenv"
  - "getenv"
  - "_tgetenv"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tgetenv (función)"
  - "_wgetenv (función)"
  - "valores de entorno"
  - "variables de entorno"
  - "getenv (función)"
  - "tgetenv (función)"
  - "wgetenv (función)"
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
caps.latest.revision: 31
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# getenv, _wgetenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene un valor del entorno actual.  Hay disponibles versiones más seguras de estas funciones; vea [getenv\_s, \_wgetenv\_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *getenv(   
   const char *varname   
);  
wchar_t *_wgetenv(   
   const wchar_t *varname   
);  
```  
  
#### Parámetros  
 `varname`  
 Nombre de la variable de entorno.  
  
## Valor devuelto  
 Devuelve un puntero a la entrada de la tabla de entornos que contiene `varname`.  No es seguro modificar el valor de la variable de entorno con el puntero devuelto.  Use la función `_putenv` para modificar el valor de una variable de entorno.  El valor devuelto es `NULL` si `varname` no se encuentra en la tabla de entornos.  
  
## Comentarios  
 La función `getenv` busca `varname` en la lista de variables de entorno.  `getenv` no distingue entre mayúsculas y minúsculas en el sistema operativo Windows.  `getenv` y `_putenv` usan la copia del entorno indicado por la variable global `_environ` para tener acceso al entorno.  `getenv` solo funciona en las estructuras de datos a las que puede tener acceso la biblioteca en tiempo de ejecución y no en el “segmento” del entorno que el sistema operativo crea para el proceso.  En consecuencia, los programas que usan el argumento de `envp` para [main](../../cpp/main-program-startup.md) o [wmain](../../cpp/main-program-startup.md) podrían recuperar información no válida.  
  
 Si `varname` es `NULL`, esta función invoca un controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `NULL`.  
  
 `_wgetenv` es una versión con caracteres anchos de `getenv`; el argumento y el valor devuelto de `_wgetenv` son cadenas de caracteres anchos.  La variable global `_wenviron` es una versión con caracteres anchos de `_environ`.  
  
 En un programa de MBCS \(por ejemplo, en un programa ASCII de SBCS\), `_wenviron` es inicialmente `NULL` porque el entorno está formado por cadenas de caracteres multibyte.  Después, en la primera llamada a `_wputenv`, o en la primera llamada a `_wgetenv` si ya existe un entorno \(MBCS\), se crea un entorno de cadenas de caracteres anchos correspondiente, al que señala `_wenviron`.  
  
 De la misma forma, en un programa de Unicode \(`_wmain`\), `_environ` es inicialmente `NULL` porque el entorno está formado por cadenas de caracteres anchos.  Después, en la primera llamada a `_putenv`, o en la primera llamada a `getenv` si ya existe un entorno \(Unicode\), se crea un entorno de MBCS correspondiente, al que señala `_environ`.  
  
 Si dos copias del entorno \(MBCS y Unicode\) existen simultáneamente en un programa, el sistema en tiempo de ejecución debe mantener las dos copias, lo que ralentiza el tiempo de ejecución.  Por ejemplo, cada vez que se llame a `_putenv`, se ejecuta automáticamente una llamada a `_wputenv`, de forma que se correspondan las dos cadenas de entorno.  
  
> [!CAUTION]
>  En raras ocasiones, cuando el sistema en tiempo de ejecución mantiene una versión Unicode y una versión multibyte del entorno, las dos versiones del entorno podrían no corresponderse exactamente.  La razón es que, aunque cualquier cadena de caracteres multibyte se asigna a una cadena de Unicode única, la asignación de una cadena de Unicode única a una cadena de caracteres multibyte no es necesariamente única.  Para obtener más información, vea [\_environ, \_wenviron](../../c-runtime-library/environ-wenviron.md).  
  
> [!NOTE]
>  Los grupos de funciones de `_putenv` y `_getenv` no son seguros para subprocesos.  `_getenv` podría devolver un puntero de cadena mientras `_putenv` modifica la cadena, y se generarían errores aleatorios.  Asegúrese de que las llamadas a estas funciones están sincronizadas.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tgetenv`|`getenv`|`getenv`|`_wgetenv`|  
  
 Para comprobar o cambiar el valor de la variable de entorno `TZ`, use `getenv`, `_putenv` y `_tzset` según sea necesario.  Para obtener más información sobre `TZ`, vea [\_tzset](../../c-runtime-library/reference/tzset.md) y [\_daylight, timezone y \_tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`getenv`|\<stdlib.h\>|  
|`_wgetenv`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_getenv.c  
// compile with: /W3  
// This program uses getenv to retrieve  
// the LIB environment variable and then uses  
// _putenv to change it to a new value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *libvar;  
  
   // Get the value of the LIB environment variable.  
   libvar = getenv( "LIB" ); // C4996  
   // Note: getenv is deprecated; consider using getenv_s instead  
  
   if( libvar != NULL )  
      printf( "Original LIB variable is: %s\n", libvar );  
  
   // Attempt to change path. Note that this only affects the environment  
   // variable of the current process. The command processor's  
   // environment is not changed.  
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996  
   // Note: _putenv is deprecated; consider using putenv_s instead  
  
   // Get new value.  
   libvar = getenv( "LIB" ); // C4996  
  
   if( libvar != NULL )  
      printf( "New LIB variable is: %s\n", libvar );  
}  
```  
  
  **La variable LIB original es: C:\\progra~1\\devstu~1\\vc\\lib**  
**La nueva variable LIB es: c:\\mylib;c:\\yourlib**   
## Equivalente en .NET Framework  
 [System::Environment::GetEnvironmentVariable](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [\_putenv, \_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)   
 [Constantes de entorno](../../c-runtime-library/environmental-constants.md)