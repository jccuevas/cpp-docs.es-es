---
title: _searchenv_s, _wsearchenv_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wsearchenv_s
- _searchenv_s
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
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
dev_langs:
- C++
helpviewer_keywords:
- tsearchenv_s function
- files [C++], finding
- buffers [C++], buffer overruns
- environment paths, searching for files
- wsearchenv_s function
- searchenv_s function
- _tsearchenv_s function
- buffer overruns
- buffers [C++], avoiding overruns
- _wsearchenv_s function
- _searchenv_s function
- environment paths
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
caps.latest.revision: 32
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
ms.openlocfilehash: c70908d3c884eed962560e0a5284c66c3c234a7e
ms.lasthandoff: 02/24/2017

---
# <a name="searchenvs-wsearchenvs"></a>_searchenv_s, _wsearchenv_s
Busca un archivo mediante rutas de acceso del entorno. Estas versiones de [_searchenv, _wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md) incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 [in] `filename`  
 Nombre del archivo que se va a buscar.  
  
 [in] `varname`  
 Entorno en el que se va a buscar.  
  
 [out] `pathname`  
 Búfer en el que se va a almacenar la ruta de acceso completa.  
  
 [in] `numberOfElements`  
 Tamaño del búfer `pathname`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
 Si `filename` es una cadena vacía, el valor devuelto es `ENOENT`.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`filename`|`varname`|`pathname`|`numberOfElements`|Valor devuelto|Contenido de `pathname`|  
|----------------|---------------|----------------|------------------------|------------------|----------------------------|  
|any|cualquiera|`NULL`|any|`EINVAL`|no disponible|  
|`NULL`|cualquiera|cualquiera|cualquiera|`EINVAL`|no cambia|  
|any|cualquiera|any|<= 0|`EINVAL`|no cambia|  
  
 Si se da alguna de estas condiciones de error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
## <a name="remarks"></a>Comentarios  
 Las rutina `_searchenv_s` busca el archivo de destino en el dominio especificado. La variable `varname` puede ser cualquier variable de entorno o definida por el usuario que especifique una lista de rutas de acceso de directorio, por ejemplo `PATH`, `LIB` y `INCLUDE`. Dado que `_searchenv_s` distingue entre mayúsculas y minúsculas, `varname` debe coincidir con las mayúsculas y minúsculas de la variable de entorno. Si `varname` no coincide con el nombre de una variable de entorno definida en el entorno del proceso, la función devuelve cero y la variable `pathname` no cambia.  
  
 La rutina busca el archivo primero en el directorio de trabajo actual. Si no encuentra el archivo, busca en los directorios especificados por la variable de entorno. Si el archivo de destino está en uno de esos directorios, la ruta de acceso creada recientemente se copia en `pathname`. Si el archivo `filename` no se encuentra, `pathname` contiene una cadena vacía terminada en un valor nulo.  
  
 El búfer de `pathname` debe tener `_MAX_PATH` caracteres como mínimo, para dar cabida a todo el nombre de ruta de acceso creada. Si no es así, `_searchenv_s` puede saturar el búfer de `pathname` y generar un comportamiento inesperado.  
  
 `_wsearchenv_s` es una versión con caracteres anchos de `_searchenv_s`; los argumentos a `_wsearchenv_s` son cadenas de caracteres anchos. Por lo demás, `_wsearchenv_s` y `_searchenv_s` se comportan de forma idéntica.  
  
 En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsearchenv_s`|`_searchenv_s`|`_searchenv_s`|`_wsearchenv_s`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_searchenv_s`|\<stdlib.h>|  
|`_wsearchenv_s`|\<stdlib.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
Path for CL.EXE:  
C:\Program Files\Microsoft Visual Studio 2010\VC\BIN\CL.EXE  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [_searchenv, _wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)   
 [getenv, _wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_putenv, _wputenv](../../c-runtime-library/reference/putenv-wputenv.md)
