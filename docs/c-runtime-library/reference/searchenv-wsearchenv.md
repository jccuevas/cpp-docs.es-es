---
title: _searchenv, _wsearchenv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _searchenv
- _wsearchenv
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
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
dev_langs:
- C++
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
caps.latest.revision: 33
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
ms.openlocfilehash: 2c71b97e925ab23c893eefd6092efffe57bea3a7
ms.contentlocale: es-es
ms.lasthandoff: 02/28/2017

---
# <a name="searchenv-wsearchenv"></a>_searchenv, _wsearchenv
Usa las rutas de acceso de entorno para buscar un archivo. Hay disponibles versiones más seguras de estas funciones; vea [_searchenv_s, _wsearchenv_s](../../c-runtime-library/reference/searchenv-s-wsearchenv-s.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _searchenv(  
   const char *filename,  
   const char *varname,  
   char *pathname   
);  
void _wsearchenv(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t *pathname   
);  
template <size_t size>  
void _searchenv(  
   const char *filename,  
   const char *varname,  
   char (&pathname)[size]  
); // C++ only  
template <size_t size>  
void _wsearchenv(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t (&pathname)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 Nombre del archivo que se va a buscar.  
  
 `varname`  
 Entorno en el que se va a buscar.  
  
 `pathname`  
 Búfer en el que se va a almacenar la ruta de acceso completa.  
  
## <a name="remarks"></a>Comentarios  
 Las rutina `_searchenv` busca el archivo de destino en el dominio especificado. La variable `varname` puede ser cualquier variable de entorno o definida por el usuario (por ejemplo, `PATH`, `LIB` o `INCLUDE`) que especifique una lista de rutas de acceso de directorio. Dado que `_searchenv` distingue entre mayúsculas y minúsculas, `varname` debe coincidir con las mayúsculas y minúsculas de la variable de entorno.  
  
 En primer lugar, la rutina busca el archivo en el directorio de trabajo actual. Si no lo encuentra aquí, lo busca en los directorios que especifica la variable de entorno. Si el archivo de destino está en uno de esos directorios, la ruta de acceso creada recientemente se copia en `pathname`. Si el archivo `filename` no se encuentra, `pathname` contiene una cadena vacía terminada en un valor nulo.  
  
 El búfer de `pathname` debe tener `_MAX_PATH` caracteres como mínimo, para dar cabida a todo el nombre de ruta de acceso creada. En caso contrario, `_searchenv` puede saturar el búfer de `pathname` y generar un comportamiento inesperado.  
  
 `_wsearchenv` es una versión de caracteres anchos de `_searchenv`, y los argumentos para `_wsearchenv` también son cadenas de caracteres anchos. Por lo demás, `_wsearchenv` y `_searchenv` se comportan de forma idéntica.  
  
 Si `filename` es una cadena vacía, estas funciones devuelven `ENOENT`.  
  
 Si `filename` o `pathname` es un puntero `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen `errno` en `EINVAL`.  
  
 Para obtener más información sobre `errno` y los códigos de error, vea [errno (Constantes)](../../c-runtime-library/errno-constants.md).  
  
 En C++, estas funciones tienen sobrecargas de plantilla que invocan a los homólogos más recientes y seguros de dichas funciones. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsearchenv`|`_searchenv`|`_searchenv`|`_wsearchenv`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_searchenv`|\<stdlib.h>|  
|`_wsearchenv`|\<stdlib.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```C  
// crt_searchenv.c  
// compile with: /W3  
// This program searches for a file in  
// a directory that's specified by an environment variable.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char pathbuffer[_MAX_PATH];  
   char searchfile[] = "CL.EXE";  
   char envvar[] = "PATH";  
  
   // Search for file in PATH environment variable:  
   _searchenv( searchfile, envvar, pathbuffer ); // C4996  
   // Note: _searchenv is deprecated; consider using _searchenv_s  
   if( *pathbuffer != '\0' )  
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );  
   else  
      printf( "%s not found\n", searchfile );  
}  
```  
  
```Output  
Path for CL.EXE:  
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [getenv, _wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_putenv, _wputenv](../../c-runtime-library/reference/putenv-wputenv.md)   
 [_searchenv_s, _wsearchenv_s](../../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)
