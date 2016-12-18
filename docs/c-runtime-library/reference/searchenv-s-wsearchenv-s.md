---
title: "_searchenv_s, _wsearchenv_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wsearchenv_s"
  - "_searchenv_s"
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
  - "_searchenv_s"
  - "_wsearchenv_s"
  - "wsearchenv_s"
  - "searchenv_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_searchenv_s (función)"
  - "_tsearchenv_s (función)"
  - "_wsearchenv_s (función)"
  - "desbordamientos del búfer"
  - "búferes [C++], evitar desbordamientos"
  - "búferes [C++], desbordamientos del búfer"
  - "environment (función)"
  - "environment (función), buscar archivos"
  - "archivos [C++], buscar"
  - "searchenv_s (función)"
  - "tsearchenv_s (función)"
  - "wsearchenv_s (función)"
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
caps.latest.revision: 32
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _searchenv_s, _wsearchenv_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Busca un archivo mediante rutas de acceso del entorno.  Estas versiones de [\_searchenv, \_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
errno_t _searchenv_s(  
   const char *filename,  
   const char *varname,  
   char *pathname,  
   size_t numberOfElements  
);  
errno_t _wsearchenv_s(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t *pathname,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _searchenv_s(  
   const char *filename,  
   const char *varname,  
   char (&pathname)[size]  
); // C++ only  
template <size_t size>  
errno_t _wsearchenv_s(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t (&pathname)[size]  
); // C++ only  
```  
  
#### Parámetros  
 \[in\] `filename`  
 Nombre del archivo que se va a buscar.  
  
 \[in\] `varname`  
 Entorno en el que se va a buscar.  
  
 \[out\] `pathname`  
 Búfer en el que se va a almacenar la ruta de acceso completa.  
  
 \[in\] `numberOfElements`  
 Tamaño del búfer `pathname`.  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
 Si `filename` es una cadena vacía, el valor devuelto es `ENOENT`.  
  
### Condiciones de error  
  
|`filename`|`varname`|`pathname`|`numberOfElements`|Valor devuelto|Contenido de `pathname`|  
|----------------|---------------|----------------|------------------------|--------------------|-----------------------------|  
|any|any|`NULL`|any|`EINVAL`|no disponible|  
|`NULL`|any|any|any|`EINVAL`|no cambia|  
|any|any|any|\<\= 0|`EINVAL`|no cambia|  
  
 Si se produce una de estas condiciones de error, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
## Comentarios  
 Las rutina `_searchenv_s` busca el archivo de destino en el dominio especificado.  La variable `varname` puede ser cualquier variable de entorno o definida por el usuario que especifique una lista de rutas de acceso de directorio, por ejemplo `PATH`, `LIB` y `INCLUDE`.  Dado que `_searchenv_s` distingue entre mayúsculas y minúsculas, `varname` debe coincidir con las mayúsculas y minúsculas de la variable de entorno.  Si `varname` no coincide con el nombre de una variable de entorno definida en el entorno del proceso, la función devuelve cero y la variable `pathname` no cambia.  
  
 La rutina busca el archivo primero en el directorio de trabajo actual.  Si no encuentra el archivo, busca en los directorios especificados por la variable de entorno.  Si el archivo de destino está en uno de esos directorios, la ruta de acceso creada recientemente se copia en `pathname`.  Si el archivo `filename` no se encuentra, `pathname` contiene una cadena vacía terminada en un valor nulo.  
  
 El búfer de `pathname` debe tener `_MAX_PATH` caracteres como mínimo, para dar cabida a todo el nombre de ruta de acceso creada.  Si no es así, `_searchenv_s` puede saturar el búfer de `pathname` y generar un comportamiento inesperado.  
  
 `_wsearchenv_s` es una versión con caracteres anchos de `_searchenv_s`; los argumentos a `_wsearchenv_s` son cadenas de caracteres anchos.  Por lo demás, `_wsearchenv_s` y `_searchenv_s` se comportan de forma idéntica.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tsearchenv_s`|`_searchenv_s`|`_searchenv_s`|`_wsearchenv_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_searchenv_s`|\<stdlib.h\>|  
|`_wsearchenv_s`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_searchenv_s.c  
/* This program searches for a file in  
 * a directory specified by an environment variable.  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char pathbuffer[_MAX_PATH];  
   char searchfile[] = "CL.EXE";  
   char envvar[] = "PATH";  
   errno_t err;  
  
   /* Search for file in PATH environment variable: */  
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );  
   if (err != 0)  
   {  
      printf("Error searching the path. Error code: %d\n", err);  
   }  
   if( *pathbuffer != '\0' )  
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );  
   else  
      printf( "%s not found\n", searchfile );  
}  
```  
  
  **Ruta de acceso de CL.EXE:**  
**C:\\Archivos de programa\\Microsoft Visual Studio 2010\\VC\\BIN\\CL.EXE**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [\_searchenv, \_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)   
 [getenv, \_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [\_putenv, \_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)