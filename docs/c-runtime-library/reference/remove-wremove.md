---
title: remove, _wremove | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wremove
- remove
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- remove
- _wremove
- _tremove
dev_langs:
- C++
helpviewer_keywords:
- tremove function
- _wremove function
- files [C++], deleting
- _tremove function
- files [C++], removing
- wremove function
- remove function
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
caps.latest.revision: 10
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
ms.openlocfilehash: 621a1c2ed9b44afb0f47fbac37b6c8de3cccecdf
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="remove-wremove"></a>remove, _wremove
Elimina un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int remove(  
   const char *path   
);  
int _wremove(  
   const wchar_t *path   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *path*  
 Ruta de acceso del archivo que se va a quitar.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve 0 si el archivo se elimina correctamente. De lo contrario, devuelve -1 y establece `errno` en `EACCES` para indicar que la ruta de acceso especifica un archivo de solo lectura o que el archivo está abierto, o bien en **ENOENT** para indicar que no se encontró el nombre de archivo o la ruta de acceso o que la ruta de acceso especifica un directorio.  
  
 Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## <a name="remarks"></a>Comentarios  
 La función **remove** elimina el archivo especificado por *path*. `_wremove` es una versión con caracteres anchos de **_remove**; el argumento *path* para `_wremove` es una cadena de caracteres anchos. `_wremove` y **_remove** se comportan de forma idéntica. Para poder eliminar un archivo, primero se deben cerrar todos los controladores correspondientes.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tremove`|**remove**|**remove**|`_wremove`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|**remove**|\<stdio.h> o \<io.h>|  
|`_wremove`|\<stdio.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_remove.c  
/* This program uses remove to delete crt_remove.txt */  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( remove( "crt_remove.txt" ) == -1 )  
      perror( "Could not delete 'CRT_REMOVE.TXT'" );  
   else  
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );  
}  
```  
  
## <a name="input-crtremovetxt"></a>Entrada: crt_remove.txt  
  
```  
This file will be deleted.  
```  
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
```  
Deleted 'CRT_REMOVE.TXT'  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_unlink, _wunlink](../../c-runtime-library/reference/unlink-wunlink.md)
